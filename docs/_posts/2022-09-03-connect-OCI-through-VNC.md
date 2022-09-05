---
layout: post
title: "Connect an Ubuntu Instance on Oracle Cloud Infrastructure (OCI) Through VNC"
toc: true
categories:
  - Tech
tags:
  - software
  - linux
date:   2022-09-03 5:30:02 PM
---

In September 2019, Oracle began offering Always Free services: 
[**`OCI Cloud Free Tier`**](https://www.oracle.com/cloud/free/){:target="_blank"}. 
As of September 2022, the Always Free cloud services include: 

+ 2 AMD based Compute VMs with 1/8 OCPU** and 1 GB memory each
+ Arm-based Ampere A1 cores and 24 GB of memory usable as 1 VM or up to 4 VMs with 3,000 OCPU hours and 18,000 GB hours per month
+ 2 Block Volumes Storage, 200 GB total
+ 10 GB Object Storage – Standard
+ 10 GB Object Storage – Infrequent Access
+ 10 GB Archive Storage
+ Resource Manager: managed Terraform
+ 5 OCI Bastions

Although people can get most of the task done through terminal by command line, 
it is always nice to interact with OCI through a graphical desktop environment. 
Oracle has offered a guide on how to connect an [Oracle Linux 7 Instance](https://docs.oracle.com/en-us/iaas/linchat/how_to_connect_through_vnc_to_public_ip_of_oracle_linux_7_instance.htm){:target="_blank"}, 
but no documentation about connecting an **Ubuntu 22.04 LTS** instance. In this 
guide, I will set up a VNC server with TightVNC on an Ubuntu 22.04 server and 
connect to it securely through an SSH tunnel. 

## Introduction

**`Virtual Network Computing`** (VNC) is a graphical desktop-sharing system that 
uses the Remote Frame Buffer protocol (RFB) to remotely control another computer. 
It transmits the keyboard and mouse input from one computer to another, 
relaying the graphical-screen updates, over a network.

## Install the Desktop Environment and VNC Server

By default, an Ubuntu 22.04 server does not come with a graphical desktop 
environment or a VNC server installed. I will install packages for the **`Xfce`** 
desktop environment and the **`TightVNC`** from the official Ubuntu repository. 
Both Xfce and TightVNC are known for being lightweight, fast and stable. 

TigerVNC has a different feature set than TightVNC, despite its origins. 
For example, TigerVNC adds encryption for all supported operating systems and 
not just Linux. Conversely, TightVNC has features that TigerVNC doesn't have, 
such as file transfers. In this guide, I chose **`TightVNC`** as an demonstration. 

Issue the following commadn line to install Xfce along with the xfce4-goodies 
package and the TightVNC server:

~~~bash
$ sudo apt update
$ sudo apt install xfce4 xfce4-goodies
$ sudo apt install tightvncserver
~~~

Next, run the vncserver command to set a VNC access password, create the initial 
configuration files, and start a VNC server instance:

~~~bash
$ vncserver
Password: 
Verify: 
Would you like to enter a view-only password (y/n)? n

New 'X' desktop is hostname:1

Creating default startup script /home/username/.vnc/xstartup
Starting applications specified in /home/username/.vnc/xstartup
Log file is /home/username/.vnc/hostname:1.log
~~~

User with the view-only password will not be able to control the VNC instance 
with their mouse or keyboard. This is a helpful option if you want to demonstrate 
something to other people using your VNC server, but this isn’t required. Note 
that if you ever want to change your password or add a view-only password, you 
can do so with the vncpasswd command:

~~~bash
$ vncpasswd
~~~

The process then creates the necessary default configuration files and 
connection information for the server. Additionally, it launches a default server 
instance on port **5901**. This port is called a **display port**, and is 
referred to by VNC as :1. VNC can launch multiple instances on other display 
ports, with :2 referring to port 5902, :3 referring to 5903, and so on. 

## Configure the VNC Server

At this point, the VNC server is installed and running. Now let’s configure it 
to launch Xfce and give us access to the server through a graphical interface.

The VNC server needs to know which commands to execute when it starts up. 
Specifically, VNC needs to know which graphical desktop environment it should 
connect to.

The commands that the VNC server runs at startup are located in a configuration 
file called **~/.vnc/xstartup**. The startup script was created when you ran the 
vncserver command in the previous step, but you’ll create your own to launch 
the Xfce desktop.

Because you are going to be changing how the VNC server is configured, first 
stop the VNC server instance that is running on port 5901 with the following 
command:

~~~bash
$ vncserver -kill :1
Killing Xtightvnc process ID 132308
~~~

Before you modify the xstartup file, back up the original:

~~~bash
$ cp ~/.vnc/xstartup ~/.vnc/xstartup.bak
~~~

Now create a new xstartup file, then add the following lines to the file:

~~~bash
$ vi ~/.vnc/xstartup
#!/bin/bash
xrdb $HOME/.Xresources # <1>
startxfce4 & # <2>
$ chmod +x ~/.vnc/xstartup
$ vncserver -localhost # <3>
New 'X' desktop is hostname:1

Starting applications specified in /home/username/.vnc/xstartup
Log file is /home/username/.vnc/hostname:1.log
~~~

1. Xserver reads user’s .Xresources file
2. launch Xfce
3. restart the VNC server

.Xresources is where a user can make changes to certain settings of the 
graphical desktop, like terminal colors, cursor themes, and font rendering. 
Whenever VNC server starts or restarts, these scripts will execute automatically.

**-localhost** option in <3>, binds the VNC server to server’s loopback 
interface, allowing only connections that originate from the server where VNC 
is installed.

## Connect to the VNC Desktop Securely

In this section, I'll establish an SSH tunnel between the client machine and the
host server, essentially tricking VNC into thinking that the connection from 
the client machine originated on the host server. This strategy will add an 
extra layer of security around VNC, as the only users who will be able to 
access it are those that already have SSH access to the host server.

VNC itself doesn’t use secure protocols when connecting. To securely connect 
to the host server, an SSH tunnel has to be estabished and then direct the VNC 
client to connect using that tunnel rather than making a direct connection.

### Connect VNC from the Bash Shell

Create an SSH connection on the client computer that securely forwards to the 
localhost connection for VNC:

~~~bash
$ ssh -L 59000:localhost:5901 -C -N -l username hostname
~~~

-L 59000:localhost:5901
: Specifies that the given port on the client computer (59000) is to be forwarded 
to the given host and port on the destination server (localhost:5901, meaning 
port 5901 on the destination server, defined as hostname). 
Note that the client port is somewhat arbitrary; as long as the port isn’t 
already bound to another service, it can be used as the forwarding port for ssh 
tunnel.

-C
: Enables compression which can help minimize resource consumption and speed 
things up.

-N
: Do not execute a remote command.  This is useful for just forwarding ports.

-l username hostname
: Specifies the user to log in as on the remote machine.

> Note: This command establishes an SSH tunnel that forwards information from 
port 5901 of the VNC server to port 59000 of the client machine via port 22 
on each machine, the default port for SSH. This is more secure than simply 
opening up the host server’s firewall to allow connections to port 5901, as that 
would allow anyone to access the host server over VNC. By connecting over an 
SSH tunnel, VNC access is limited to client machines that already have SSH 
access to the host server.

Press `CTRL+C` in the client terminal to stop the SSH tunnel. This will 
disconnect your VNC session as well.

### Connect VNC from Putty

In the **Connection** category on the left panel of the PuTTY configuration 
window, expand the **SSH** and click on **Tunnels**. 
On the **Options controlling SSH port forwarding** screen, enter 59000 at the 
Source Port and localhost:5901 as the Destination, then save the configuration. 

![putty_tunnel](https://bn1303files.storage.live.com/y4maXO18RwAQiftRyYDBmTiyEwOLLeCnQXvFL3BRY8IQ8IORVI0De4ZtLUCvIVB74DtrI3Uimdb-xa7ShNNokLMI3S-if4E_pkv6cBArfgXYhrrd6PiTaXkIoJAO03q16LCAzDdRxlobnVOXWYhMeOCfzty1JnZPsAEaPxUanzQqBIsDVxgCVEC8MidT2H1Le4s?width=466&height=447&cropmode=none){: width="466" height="447"} 

Once the tunnel is running, use a VNC client to connect to localhost:59000. Then, 
fill in the vnc password created earlier to authenticate. 

![vnc_viewer](https://bn1303files.storage.live.com/y4mDwbOiwa1BkudEN3-nvnAVZq8VlN-NA7rmj2AzjnfkqUR4dXFejiVbpd8L_lA5w50tkYn377lotLjXBZKPoBN1Y8wcIdnGTMHwsxxTla75ObY53WeCJoZlXk6bAVNtDROIlEWrIOdpdeAhaCTn8Rx56a6PYWWZ1hWZBUSXVE7LDYp1krQDdX121vkl4nu996T?width=469&height=200&cropmode=none){: width="469" height="200"} 

Once you are connected, you’ll see the default Xfce desktop:

![vnc_xfce](https://bn1303files.storage.live.com/y4mi_ZDdvK4EPTCQVCoZ7OcxMTDBcJJMRKfR3VQU-9b77AfOOXNyHsJZmWZT8Z-s6WBCtTcSEgGkNWJHBBLnNl77FRFBufFg1CX_D1-khyAJjiGMFlma2oBenLmRsvfMOld9Y5ZfYebD5yX7CRjqQY8RSbU1CF6sAivRm9tRdtjg0snoQ-eC_J4jQrz-iQV5Oqz?width=660&height=428&cropmode=none){: width="660" height="428"} 

## Run VNC as a System Service

VNC server can be configured to run as a systemd service when host server boots 
up. User can start, stop, and restart it as needed, like any other service.


### Configure the VNC system service 

First, create a new configuration file called **`/etc/systemd/system/vncserver@.service`**: 

~~~bash
$ sudo vi /etc/systemd/system/vncserver@.service

[Unit]
Description=Start TightVNC server at startup
After=syslog.target network.target

[Service]
Type=forking
User=username
Group=username
WorkingDirectory=/home/username

PIDFile=/home/username/.vnc/%H:%i.pid
ExecStartPre=-/usr/bin/vncserver -kill :%i > /dev/null 2>&1
ExecStart=/usr/bin/vncserver -depth 24 -geometry 1280x800 -localhost :%i
ExecStop=/usr/bin/vncserver -kill :%i

[Install]
WantedBy=multi-user.target
~~~

The **`@`** symbol in the file name of configuration file passes the argument of 
VNC display port to the service. Also, change the value of **User**, **Group**, 
**WorkingDirectory** and **username** in the value of **PIDFILE**. 

ExecStartPre
: stops VNC if it’s already running. 

ExecStart
: starts VNC and sets the color depth to 24-bit color with a resolution of 1280x800. 
Note that the **-localhost** option is included again.

### Launch the VNC system service 

Make systemd reload its configuration files, and then enable and start 
the vncserver services:

~~~bash
$ sudo systemctl daemon-reload # <1>
$ sudo systemctl enable vncserver@1.service # <2>
$ vncserver -kill :1 # <3>
$ sudo systemctl start vncserver@1 # <4>
$ sudo systemctl status vncserver@1
● vncserver@1.service - Start TightVNC server at startup
     Loaded: loaded (/etc/systemd/system/vncserver@.service; enabled; vendor preset: enabled)
     Active: active (running) since Sun 2022-09-04 21:06:47 UTC; 18h ago
    Process: 147262 ExecStartPre=/usr/bin/vncserver -kill :1 > /dev/null 2>&1 (code=exited, status=2)
    Process: 147266 ExecStart=/usr/bin/vncserver -depth 24 -geometry 1280x800 -localhost :1 (code=exited, status=0/SUCCESS)
   Main PID: 147277 (Xtightvnc)
      Tasks: 70 (limit: 28701)
     Memory: 148.7M
        CPU: 1min 211ms
     CGroup: /system.slice/system-vncserver.slice/vncserver@1.service
...
~~~

1. Rerun all generators, reload all unit files, and recreate the entire dependency tree.
2. Enable one or more units or unit instances. This will create a set of symlinks, 
after the symlinks have been created, the system manager configuration is reloaded 
in order to ensure the changes are taken into account immediately. The **`1`** 
following the **`@`** sign signifies display port number for the VNC service. 
3. Stop the current instance of the VNC server if it’s still running. 
4. Start (activate) one or more units specified on the command line.

Now, the VNC server is now ready to use whenever host server boots up, and 
it can be managed and controlled by systemd and service manager --- **systemctl**.
