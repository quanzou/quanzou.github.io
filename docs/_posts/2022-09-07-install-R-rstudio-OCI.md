---
layout: post
title: "Install R and RStudio at an Ubuntu Instance on Oracle Cloud Infrastructure (OCI)"
toc: true
categories:
  - Tech
tags:
  - software
  - linux
date:   2022-09-07 5:30:02 PM
---

After VNC has been working for Oracle Cloud Infrastructure (OCI) as explained in 
previous post --- [**Connect OCI Through VNC**](https://quanzou.github.io/tech/connect-OCI-through-VNC/), 
I am going to install Both **`R`** and **`RStudio`** at OCI with **4** Arm-based 
Ampere A1 cores and **24** GB of memory. The Arm-based Virtual Machine is much 
stronger than AMD based one, although not all software builds are supported on 
Arm64(aarch64). 

## Introduction

**`R`** is a programming language for statistical computing and graphics supported 
by the R Core Team and the R Foundation for Statistical Computing. In 1991, 
statisticians Ross Ihaka and Robert Gentleman at the University of Auckland, 
New Zealand, embarked on an **`S`** implementation. It was named partly after the 
first names of the first two **`R`** authors and partly as a play on the name of **`S`**. 
Multiple third-party graphical user interfaces are also available, such as 
**`RStudio`**, an integrated development environment, and Jupyter, a notebook 
interface. 

**`RStudio`** is an integrated development environment for R, a programming language 
for statistical computing and graphics. It is available in two formats: 
**`RStudio` Desktop**  is a regular desktop application while **`RStudio Server`**  runs 
on a remote server and allows accessing **`RStudio`** using a web browser.

## Install **`R`**

The current **`R 4.2`** are fully supported only for the latest Ubuntu Long Term 
Support (LTS) release, but available for most Ubuntu release until their official 
end of life date. 

The LSB (Linux Standard Base) command shows that Ubuntu distribution comes with 
OCI Boot Volumn Image is 22.04.1 LTS `Jammy Jellyfish`, which was released on 
April 21, 2022. This release of Ubuntu Linux distribution will have long-term 
support until 2027. Later, people from StackExchange pointed out that Ubuntu 
22.04 of arm64 (aarch64) build is not supported by **`R 4.2.1`** by the time of this 
article. This results the failure of upgrading from **`R 4.1.2`** to **`R 4.2.1`**. 

```bash
$ lsb_release -a
Distributor ID: Ubuntu
Description:    Ubuntu 22.04.1 LTS
Release:        22.04
Codename:       jammy
```

### Install from Binary

The default R build comes with the source list `jammy` is version **4.1.2**, 
together with other 1082 CRAN Packages.  

```bash
# resynchronize package indices from the source quietly level 2
$ sudo apt update -qq

# install two helper packages without considering dependency packages
$ sudo apt install --no-install-recommends software-properties-common dirmngr

# to install R 
$ sudo apt install --no-install-recommends r-base

# query with pattern matching package names
$ apt list r-base
r-base/jammy 4.1.2-1ubuntu2 all
```

The **r-base** package --- GNU R statistical computation and graphics system ---
mainly includes two packages: **r-base-core** and a metapackage **r-recommended**. 
One can find more details about the packages with the following commands: 

~~~bash
# query the dpkg database with exact package name: 
$ dpkg-query --list 'r-base'
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version        Architecture Description
+++-==============-==============-============-=================================================
ii  r-base         4.1.2-1ubuntu2 all          GNU R statistical computation and graphics system

# list all installed packages in /var/lib/dpkg/status, and filter with package name: 
$ dpkg-query --list | grep r-base
ii  r-base         4.1.2-1ubuntu2    all      GNU R statistical computation and graphics system
ii  r-base-core    4.1.2-1ubuntu2    arm64    GNU R core of statistical computation and graphics system

# list all installed packagesand filter with package name: 
$ apt list --installed | grep r-base
r-base-core/jammy,now 4.1.2-1ubuntu2 arm64 [installed]
r-base/jammy,now 4.1.2-1ubuntu2 all [installed]

# show a listing of each reverse dependency (currently installed):
$ apt-cache rdepends --installed r-base

# show package details of versions, reverse and forward dependencies:
$ apt-cache showpkg r-base

# query the APT cache in /var/lib/apt/lists/ of all 1082 r-cran packages: 
$ apt-cache search r-cran-
~~~

Now, we can verify the installation of **`R`**: 

~~~bash
$ /usr/bin/R --version
R version 4.1.2 (2021-11-01) -- "Bird Hippie"
Copyright (C) 2021 The R Foundation for Statistical Computing
Platform: aarch64-unknown-linux-gnu (64-bit)

R is free software and comes with ABSOLUTELY NO WARRANTY.
You are welcome to redistribute it under the terms of the
GNU General Public License versions 2 or 3.
For more information about these matters see
~~~

### Upgrade **`R`** from Official Repository 

The latest **`R`** (Funny-Looking Kid) R-4.2.1, was releaseed on 2022-06-23. User 
can download the precompiled binaries and upgrade the package. 

~~~bash
# update indices
$ sudo apt update -qq

# install two helper packages if haven't installed
$ sudo apt install --no-install-recommends software-properties-common dirmngr

# upgrade two helper packages if have installed
$ sudo apt install --only-upgrade software-properties-common dirmngr
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
dirmngr is already the newest version (2.2.27-3ubuntu2.1).
software-properties-common is already the newest version (0.99.22.3).

# add the signing key (by Michael Rutter) for these repos
# To verify key, run gpg --show-keys /etc/apt/trusted.gpg.d/cran_ubuntu_key.asc 
# Fingerprint: E298A3A825C0D65DFD57CBB651716619E084DAB9
$ wget -qO- https://cloud.r-project.org/bin/linux/ubuntu/marutter_pubkey.asc | sudo tee -a /etc/apt/trusted.gpg.d/cran_ubuntu_key.asc
$ gpg --show-keys /etc/apt/trusted.gpg.d/cran_ubuntu_key.asc
pub   rsa2048 2010-10-19 [SCA] [expires: 2027-09-30]
      E298A3A825C0D65DFD57CBB651716619E084DAB9
uid                      Michael Rutter <marutter@gmail.com>
sub   rsa2048 2010-10-19 [E] [expires: 2027-09-30]

# add the R 4.0 repo from CRAN -- adjust 'focal' to 'groovy' or 'bionic' as needed
$ sudo add-apt-repository "deb https://cloud.r-project.org/bin/linux/ubuntu $(lsb_release -cs)-cran40/"
Repository: 'deb https://cloud.r-project.org/bin/linux/ubuntu jammy-cran40/'
Description:
Archive for codename: jammy-cran40/ components:
More info: https://cloud.r-project.org/bin/linux/ubuntu
Adding repository.
Press [ENTER] to continue or Ctrl-c to cancel.
Adding deb entry to /etc/apt/sources.list.d/archive_uri-https_cloud_r-project_org_bin_linux_ubuntu-jammy.list
Adding disabled deb-src entry to /etc/apt/sources.list.d/archive_uri-https_cloud_r-project_org_bin_linux_ubuntu-jammy.list
Get:1 https://cloud.r-project.org/bin/linux/ubuntu jammy-cran40/ InRelease [3626 B]
Hit:2 http://ports.ubuntu.com/ubuntu-ports jammy-security InRelease
Hit:3 http://iad-ad-3.clouds.ports.ubuntu.com/ubuntu-ports jammy InRelease
Get:4 https://cloud.r-project.org/bin/linux/ubuntu jammy-cran40/ Packages [16.9 kB]
Hit:5 http://iad-ad-3.clouds.ports.ubuntu.com/ubuntu-ports jammy-updates InRelease
Hit:6 http://iad-ad-3.clouds.ports.ubuntu.com/ubuntu-ports jammy-backports InRelease
Fetched 20.5 kB in 1s (39.1 kB/s)
Reading package lists... Done
~~~

We can first verify that newer version of R is available, then install or 
upgrade by the following commonds: 

~~~bash
# list all package name
$ apt list r-base -a
Listing... Done
r-base/jammy-cran40 4.2.1-2.2204.0 all [upgradable from: 4.1.2-1ubuntu2]
r-base/jammy-cran40 4.2.1-1.2204.0 all
r-base/jammy-cran40 4.2.0-1.2204.0 all
r-base/jammy,now 4.1.2-1ubuntu2 all [installed,upgradable to: 4.2.1-2.2204.0]

$ sudo apt-get --dry-run install --no-install-recommends r-base
The following packages have unmet dependencies:
 r-base : Depends: r-base-core (>= 4.2.1-2.2204.0) but 4.1.2-1ubuntu2 is to be installed
          Depends: r-recommended (= 4.2.1-2.2204.0) but 4.1.2-1ubuntu2 is to be installed
E: Unable to correct problems, you have held broken packages.

$ sudo apt-get --dry-run install --only-upgrade r-base
The following packages have unmet dependencies:
 r-base : Depends: r-base-core (>= 4.2.1-2.2204.0) but 4.1.2-1ubuntu2 is to be installed
          Depends: r-recommended (= 4.2.1-2.2204.0) but 4.1.2-1ubuntu2 is to be installed
          Recommends: r-base-html but it is not going to be installed
          Recommends: r-doc-html but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

$ sudo apt upgrade
The following packages have been kept back:
  dmidecode r-base r-cran-boot r-cran-codetools r-recommended
0 upgraded, 0 newly installed, 0 to remove and 5 not upgraded.
~~~

If you encountered error messages above during upgrading, then there are packages 
on which **`r-base`** **4.1.2** depends were kept back. We need to completely 
remove all Ubuntu packages for R and clean the installation. The **`autoremove`** 
option will remove all dependent libraries after previous package modification. 
It's always a good habbit of runnig `autoremove` after an update. 

~~~bash
# completely remove R installation
$ sudo apt-get purge r-base* r-recommended r-cran-*
$ sudo apt update
$ sudo apt autoremove

# installation only works for AMD Ubuntu
$ sudo apt-get --dry-run install --no-install-recommends r-base
r-base is already the newest version (4.2.1-2.2204.0).
0 upgraded, 0 newly installed, 0 to remove and 26 not upgraded.

# add the current R 4.0 or later c2d4u repository:
$ sudo add-apt-repository ppa:c2d4u.team/c2d4u4.0+
Repository: 'deb https://ppa.launchpadcontent.net/c2d4u.team/c2d4u4.0+/ubuntu/ jammy main'
Description:
A PPA for R packages from CRAN's Task Views built against R 4.0 (and subsequent releases).  Only building packages for LTS releases.
More info: https://launchpad.net/~c2d4u.team/+archive/ubuntu/c2d4u4.0+
Adding repository.
Press [ENTER] to continue or Ctrl-c to cancel.
Adding deb entry to /etc/apt/sources.list.d/c2d4u_team-ubuntu-c2d4u4_0_-jammy.list
Adding disabled deb-src entry to /etc/apt/sources.list.d/c2d4u_team-ubuntu-c2d4u4_0_-jammy.list
~~~

After adding the current R 4.0 or later ‘c2d4u’ to the repository at 
**/etc/apt/resource.list.d/c2d4u_team-ubuntu-c2d4u4_0_-jammy.list**,  we have 
access to 5000+ CRAN packages available for Ubuntu LTS releases. Packages installed 
under Ubuntu will be available server wide for every user at 
**ls /usr/lib/R/site-library/**; however, packages installed within R, will 
only be available for local user at **~/R/aarch64-unknown-linux-gnu-library/4.1/**. 

>Note: The upgrade method works for AMD64 Ubuntu only, but not on **`arm64`** build. 
Ubuntu 22.04 of **arm64** (**aarch64**) is not supported by R 4.2.1 by the time 
of this article. 

### Install from Source

To upgrade to **`R`** to version **`4.2`**, I am going to build R from the source 
codes. 

#### Download the source package 
 
~~~bash
# Install required dependencies
$ sudo apt-get update
$ sudo apt-get install gdebi-core

#Specify R version#
$ export R_VERSION=4.2.1

# Download and extract the version of R that you want to install:
# -O option writes output to a local file named like the remote file
$ curl -O https://cran.rstudio.com/src/base/R-4/R-${R_VERSION}.tar.gz
$ tar -xzvf R-${R_VERSION}.tar.gz
$ cd R-${R_VERSION}
~~~

#### Prerequisites

The Intel components install into **`/usr/local/lib`**, the **`arm64`** ones 
into **`/opt/R/`**:

~~~bash
# Essential programs and libraries: C and Fortran 90
$ sudo apt install build-essential
$ sudo apt-get install gfortran
$ sudo apt install zlib1g zlib1g-dev
$ sudo apt-get install libbz2-dev
$ sudo apt-get install liblzma-dev
$ sudo apt-get install libcurl4-openssl-dev

# binary components pcre2 support
$ sudo apt install libpcre2-dev

# Component readline support the command-line editing
$ sudo apt-get install libreadline-dev

# graphic support for an X sub-system
$ sudo apt-get install libx11-dev xorg-dev 

#  Capabilities skipped:        PNG, JPEG, TIFF, cairo, ICU
# Components jpeg, libpng, tiff and png for bitmapped graphics devices. 
$ sudo apt-get install libtiff-dev
$ sudo apt-get install libcairo2-dev
$ sudo apt-get install libicu-dev 

# configure: WARNING: you cannot build info or HTML versions of the R manuals
$ sudo apt-get install texinfo texlive texlive-fonts-extra 

# Java support
$ sudo apt-get install default-jdk default-jre

$ $ java -version
openjdk version "11.0.14" 2022-01-18
OpenJDK Runtime Environment (build 11.0.14+9-Ubuntu-0ubuntu2)
OpenJDK 64-Bit Server VM (build 11.0.14+9-Ubuntu-0ubuntu2, mixed mode, sharing)

$ javac -version
javac 11.0.14
~~~

#### Configure, Compile and Install

Configure has many options: **`./configure --help`**. If you need to re-configure 
**`R`** with different options run **`make clean`** or **`make distclean`** 
before doing so.

~~~bash
# configure 
$ ./configure \
    --with-readline=yes --with-x=yes \
    --prefix=/opt/R/${R_VERSION} \
    --enable-memory-profiling \
    --enable-R-shlib \
    --with-blas \
    --with-lapack

$ make
$ make check 
$ sudo make install	
~~~

**`make check`** checks the built system works correctly. Failures are not 
necessarily problems as they might be caused by missing functionality, but you 
should look carefully at any reported discrepancies. 

To install info and PDF versions of the manuals, use **`sudo make install-info`** 
and/or **`sudo make install-pdf`**. 

Now, we can verify the installation of **`R`**: 

~~~bash 
$ /opt/R/4.2.1/bin/R --version
R version 4.2.1 (2022-06-23) -- "Funny-Looking Kid"
Copyright (C) 2022 The R Foundation for Statistical Computing
Platform: aarch64-unknown-linux-gnu (64-bit)
~~~

To ensure that R is available on the default system PATH variable, 
create symbolic links to the version of R that you installed:

~~~bash 
sudo ln -s /opt/R/${R_VERSION}/bin/R /usr/local/bin/R
sudo ln -s /opt/R/${R_VERSION}/bin/Rscript /usr/local/bin/Rscript
~~~

## Install RStudio from Source

RStudio Team has already started experimenting arm64 builds, also known as aarch64.
However, builds under arm64 CPU architecture are intended for testing purposes, 
and are not recommended for general use. They do not include a bundled copy of 
Quarto or Pandoc (see quarto-cli#190), so these tools must be installed 
separately to work with Quarto or R Markdown content. 

#### Download the source package 

Download and extract the latest version of **`RStudio`**:

~~~bash
$ wget https://github.com/rstudio/rstudio/archive/refs/tags/v2022.07.1+554.tar.gz
$ tar -xzvf v2022.07.1+554.tar.gz
$ cd rstudio-2022.07.1-554/
~~~

### Prerequisites

Building RStudio requires a number of dependencies (including R itself).
There are platform-specific instructions for satisfying these dependencies
within the following directories

+ dependencies
  + linux
  + osx
  + windows

README file contained within the root of each platform's directory contains 
specific instructions.

RStudio requires relatively recent versions of a number of components. It is
therefore likely to only correctly configure and build on more recent Linux
systems. Specific version requirements for various components include:

+ R 3.3.0
+ CMake 3.4.3 or newer
+ Boost 1.78
+ Qt 5.12.8 (Required only for Desktop)
+ patchelf 0.9 (Required only for Desktop)

Run the install-dependencies script appropriate to your platform'spackage 
management system: 

~~~bash
$ ./dependencies/linux/install-dependencies-jammy
~~~

### Cmake and Install

From the root of the RStudio tree create a build directory and then change to it:

~~~bash
$ mkdir build
$ cd build
$ sudo apt install cmake
$ cmake .. -DRSTUDIO_TARGET=Server \
           -DCMAKE_BUILD_TYPE=Release \
           -DCMAKE_INSTALL_PREFIX=/usr/local/lib/rstudio-server
$ sudo make install
~~~

**Desktop** builds not currently supported on aarch64, therefore, only **Server** 
version is build. 

### RStudio Server Configuration

After successful installation of RStudio Server, we can create an rstudio-server 
system user account (RStudio will automatically run under this account if it is 
present). You can do this with:

~~~bash
$ sudo useradd -r rstudio-server
~~~

Register RStudio as a daemon using an init.d (for most systems) or systemd (for 
Ubuntu from 15.04, RHEL from 7) or upstart (for Ubuntu before 15.04) or 
launchd plist (for Mac OSX) script appropriate to your system.

~~~bash
# display rstudio-server system service file 
$ cat /usr/local/lib/rstudio-server/extras/systemd/rstudio-server.service
[Unit]
Description=RStudio Server
After=network-online.target
Wants=network-online.target

[Service]
Type=forking
PIDFile=/run/rstudio-server.pid
ExecStart=/usr/local/lib/rstudio-server/bin/rserver
ExecStop=/usr/bin/killall -TERM rserver
KillMode=none
Restart=on-failure

[Install]
WantedBy=multi-user.target

# create systemd configuration: 
$ sudo cp /usr/local/lib/rstudio-server/extras/systemd/rstudio-server.service  /etc/systemd/system/.

# Create a soft link in /usr/sbin to the server administrative script
$ sudo ln -f -s /usr/local/lib/rstudio-server/bin/rstudio-server /usr/sbin/rstudio-server

# make the system aware of the new unit file: 
$ sudo systemctl daemon-reload

# enable the unit file:
$ sudo systemctl enable rstudio-server.service

# start the rstudio-server service: 
$ sudo systemctl start rstudio-server.service
$ sudo systemctl status rstudio-server.service
● rstudio-server.service - RStudio Server
     Loaded: loaded (/etc/systemd/system/rstudio-server.service; enabled; vendor preset: enabled)
     Active: active (running) since Fri 2022-09-09 17:40:55 UTC; 9s ago
    Process: 9081 ExecStart=/usr/local/lib/rstudio-server/bin/rserver (code=exited, status=0/SUCCESS)
   Main PID: 9082 (rserver)
      Tasks: 4 (limit: 28701)
     Memory: 10.8M
        CPU: 849ms
     CGroup: /system.slice/rstudio-server.service
             └─9082 /usr/local/lib/rstudio-server/bin/rserver

Sep 09 17:40:55 instance-20220824-1108 systemd[1]: Starting RStudio Server...
Sep 09 17:40:55 instance-20220824-1108 systemd[1]: Started RStudio Server.
~~~

RStudio server is now ready to use whenever host server boots up, and I can 
manage it with systemctl commands like any other systemd service.

### Using RStudio Server

Install a compatitable browser to access RStudio Server: 

~~~bash
$ sudo apt install epiphany-browser
~~~

Then access RStudio Server from epiphany-browser at **http://localhost:8787**. 

![rstudio_signin]({{ site.url }}{{ site.baseurl }}/assets/images/install-R-RStudio-OCI/rstudio_signin.png){: width="660" height="299"} 

To access Rstudio Server from external client **http://public-server-ip:8787**, 
we need to open port 8787 of the host server firewall: 

~~~bash
sudo iptables -I INPUT 7 -m state --state NEW -p tcp --dport 8787 -j ACCEPT
sudo netfilter-persistent save
~~~

If RStudio Server is running on a public network then configuring it to use 
SSL (Secure Sockets Layer) encryption is strongly recommended. You can do this 
via the ssl-enabled setting along with related settings that specify the 
location of your SSL certificate and key. Unfortunately, this feature is only 
available for **`RStudio Server Pro`** version. 

![rstudio_server]({{ site.url }}{{ site.baseurl }}/assets/images/install-R-RStudio-OCI/rstudio_server.png){: width="660" height="400"} 

## Reference 

1. [Ubuntu Packages For R --- Brief Instructions](https://cran.r-project.org/bin/linux/ubuntu/){:target="_blank"} (accessed September 07, 2022). 
2. [R Installation and Administration](https://cran.r-project.org/doc/manuals/R-admin.html){:target="_blank"} (accessed September 07, 2022). 
3. [RStudio Documentation --- Install R](https://docs.rstudio.com/resources/install-r/){:target="_blank"} (accessed September 07, 2022).
4. [RStudio Server for Ubuntu 22 (arm64)](https://dailies.rstudio.com/rstudio/elsbeth-geranium/server/jammy-arm64/){:target="_blank"} (accessed September 07, 2022). 
5. Upgrading R from 4.1.2 to 4.2.1 under Ubuntu aarch64/arm64 22.04 LTS have unmet dependencies, ask Ubuntu Stack Exchange, 2022.  [https://askubuntu.com/questions/1428565](https://askubuntu.com/questions/1428565){:target="_blank"} (accessed September 07, 2022). 