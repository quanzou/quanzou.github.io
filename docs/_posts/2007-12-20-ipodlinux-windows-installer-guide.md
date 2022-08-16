---
layout: post
title: "iPodlinux Windows Installer Guide --- 1st Generation iPod Nano"
toc: true
categories:
  - Tech
tags:
  - Game
date:   2007-12-20
---

I've owned a 1st Generation iPod nano since 2006 Spring, which was a gift from 
my French classmates when I graduated from Paris 6 and CNRS-Gif. It's my first 
Apple product I'd ever had. I am pretty satisfied with it until one day when I 
want to transfer my songs from iPod to an computer. I was not able to drag songs 
through iTunes. Then I did a online search about available rom for iPod, there 
it is --- **iPodLinux**. However, several models are not supported, and mine is 
unfortunately in the list. I tried the official installer several times, it 
didn't work out, until I found the following guide specially tuned for 1st 
Generation iPod Nano.

Netless Installer v2.3w Build 20070107, the method was used on a 1st generation 
4Gb iPod Nano with Windows XP SP2. it will not work on a 2nd generation nano. 
This guide will cover the following topics: **Loader v2.4** and **Podzilla2** 
Install Package, Enabling start Files, Loading Modules, Setting up **loader.cfg**, 
Installing **iBoy**, Installing **iDoom**, Installing **RockBox**, Installing 
**mvpd** and Converting **avi** files for playing on iPod.

## Download the Package

Download [ipodlinux-installer-2.3w-netless-20070107.zip](https://onedrive.live.com/embed?cid=E53D6D82FAE9F70E&resid=E53D6D82FAE9F70E%21148&authkey=ACE5xyA9TdharAY){:target="_blank"}, and extract the file. 

## Install Linux onto iPod

 + Browse to the **.\Required Software\ipodlinux-installer-2.3w-netless-20070107\\** 
   folder and double-click **installer.exe**. 
   
 + If the installer complains about an incompatible Sysinfo file, then **Installer2** 
   is unable to operate on these models/firmware versions at the moment (as of 
   version 2.3). Because of the updates (Firmware version 1.2 or newer) that 
   came on September 12, 2006 with iTunes 7, **Installer2** is no longer able to 
   detect the iPod's version. The error message looks like: 
   
   ~~~console
   Invalid SysInfo file. There was something wrong with the syntax of your sysinfo file; try restarting your iPod.
   Error code 0(The operation completed successfully)
   ~~~
   
   To correct this problem, you will need to manually create a new SysInfo file 
   to replace the old one. For the model I had **nano 1G 4GB:**, The Sysinfo file 
   is given as below: 
    
   ~~~console
   BoardHwName: iPod M26
   pszSerialNumber: XXXXXXXXXXX
   ModelNumStr: MA005
   FirewireGuid: 0x000A2700128567DA
   HddFirmwareRev: ADBA41KB
   RegionCode: S(0x0006)
   PolicyFlags: 0x00000001
   buildID: 0x05108000 (5.1)
   visibleBuildID: 0x01108000 (1.1)
   boardHwRev: 0x00000000 (0.0 0)
   boardHwSwInterfaceRev: 0x000C0005 (0.0.12 5)
   bootLoaderImageRev: 0x00000000 (0.0 0)
   diskModeImageRev: 0x00000000 (0.0 0)
   diagImageRev: 0x00000000 (0.0 0)
   osImageRev: 0x00000000 (0.0 0)
   iPodFamily: 0x00000000
   updaterFamily: 0x00000000
   ~~~

   then, replace **XXXXXXXXXXXX** with the serial number found on the back of 
   your iPod. If you have other model number, go to [http://ipodlinux.org/Sysinfo](http://ipodlinux.org/Sysinfo){:target="_blank"} 
   and follow the instructions there to create the **Sysinfo** file for your 
   specific model.
   
 + After the **Sysinfo** file has been accepted by the installer, check the 
   **Advanced Partitioning and package selection** checkbox on the bottom left, 
   and click Next. 
   
 + Make sure that **Shrinking the data partition** is selected, and the default 
   value of 128 MB is enough space, unless you are planning to put a lot of files 
   into the linux filesystem. Click Next. 

 + Select the **iPodLoader2 (nice menu interface, but still experimental)** radio 
   button and leave the **save backup** checkbox selected if you would like to 
   make a backup in case there is an error. Click **Next**.
   
   > **CAUTION**: the backup system is very buggy and will probably exit prematurely 
   with an error. 
   
   If you selected a backup and the installer exits with an error, use the 
   provided HP tool to perform a FAT 32 format on your iPod. Then run iTunes 
   and restore your iPod to its factory settings. Wait for iTunes to ask you to 
   rename your iPod, eject it, reselect your language and hold down play until 
   it goes into sleep mode and then wake it up, reconnect it, and then restart 
   this guide. 


 + When you click **Next**, there will be a series of errors which are normal. 
   They will not affect this method of install. Just click ok to each of them 
   and they will go away. I had about 7 errors when installing for **nano 1G 4GB**.
   
 + Click the **Load Package(s) information** button in the lower left of the 
   screen. Browse to **selection.ipl** and click **OK**.
   
 + Click **Next**, and the installer will install **iPodlinux** onto your iPod.
 
 + When it is done, click **Finish**. Eject your iPod, and once it reboots 
   select **Apple OS**.
   
## Enabling start files

 + Browse to the **\Required Software\LTools\\** folder and double-click **LTOOLSnet.exe**.
 
 + In the top half of the **LTOOLSnet-C#** window, browse to **\Required Software\Enable StartFile\\** folder.
 
 + In the bottom half of the **LTOOLSnet-C#** window, browse to the **ext** folder.
 
 + In the the **LTOOLSnet-C#** window, click **File** and Uncheck **Linux read only**. 
 
 + In the bottom half of the **LTOOLSnet-C#** window, scroll down until you find 
   the **rc** file. Rightclick this file and select **Modify**. Change the name 
   to **rc.old**. This backs up the rc file in case of an error.
   
 + Drag the **rc** file from the top half down into the bottom half. Close LTools.
 
 + Eject your iPod. Reboot your iPod into **iPodLinux**, then click 
   **Power >Reboot iPod > absolutely** and reboot into **Apple OS**.
   
## Loading modules

 + Browse into the folder **\Reqiured Software\modules\\**.
 
 + For descriptions of what each module does, [http://www.ipodlinux.org/Special_Module.html](http://www.ipodlinux.org/Special_Module.html){:target="_blank"} 
   makes a list of which modules you would like to install. I chose the following 
   modules: browser, browseradmin, calc, clocks, extlaunch, headerclock, 
   mikmodule, mouse, mpdc, PodDraw, PodPaint, PodWrite, Pong, textinput, tidial, 
   tikeypad, tiosk, tiwidgets, tixtensions, and tunnel. You will need to 
   routinely check this website to make sure that your modules are up to date. 
   The installer claims to do this for you, but is very buggy when trying to 
   update the iPod.
   
 + Browse to My Computer and click on your iPod drive. Create a folder in the 
   root and name it **modules**. Copy the corresponding modules that you 
   selected from the **.\Required Software\modules\\** folder and paste them in 
   the newly created **modules** folder on your iPod. 
   
   > **NOTE**: iPodlinux will only install about **30** modules each time, so if you have more than 30, repeat this process after each iPod reboot.
   
 + Open Notepad. Paste this code into it: 
   
   ~~~console
   mv /hp/modules/* /usr/lib/
   ~~~
   
   Save this file in the root of your iPod as **start** with no extension.
 
 + Eject your iPod. Reboot your iPod into **iPodLinux**, then click 
   **Power >Reboot iPod > absolutely** and reboot into **Apple OS**.
   
## Setting up LOADER.CFG

 + Open Notepad and type in the following snippet of code:
 
   ~~~console
   # iPodLoader 2.3 config file
   # this turns the backlight on
   backlight = 1
   timeout = 10
   default = 7
   #This is the Selection List
   Apple OS @ ramimg
   iPodLinux @ (hd0,2)/linux.bin
   Sleep @ sleep
   Disk Mode @ diskmode
   ~~~
 
 + Save as **loader.cfg** on your iPod’s root folder.
 
   ![Boot_Loader](https://bn1303files.storage.live.com/y4mGPOoGeI6bGac2utRVp7eodfY_YJTZmiHdjVEUr92QyEOqG_ENjDPqWemarOl6rIl9zMP0KXVigOmnhLFOeKMNlvEX69-OickWRZf0ciyL_3fzTDkbsLuJbgsd_SVOjDqQZPi_HtyJiVjqGjWVU7NhQycRUvQ6cyv9R6HjUsj6DMgsjQih7tcN3uS6zWbQKKs?width=399&height=300&cropmode=none){: width="399" height="300"}

   
## Installing Rockbox

 + Browse to [https://www.rockbox.org/download/byhand.cgi](https://www.rockbox.org/download/byhand.cgi) 
   and find your iPod, and download the latest build of RockBox for your iPod. 
   Extract the file called **rockbox.ipod** and a folder named **.rockbox**, 
   and copy them to your iPod drive which already contains the folders Calendar, 
   Contacts, and Notes.
   
 + Open **loader.cfg** and add the following code:
 
   ~~~console
   RockBox @ (hd0,1)/rockbo~1.ipod
   ~~~
   
   RockBox is now installed on your iPod! 
   
 + **Plugins** are programs that Rockbox can load and run. Two plugins were 
   installed as demo: **Bubble** and **Battery Benchmark**. For a full list of 
   plugins, please refert to **The Rockbox Manual**. 
 
   ![Bubbles](https://bn1303files.storage.live.com/y4m0G8pahzm7tLxuFJggQ1OWsEjRRNipNjC1QHKrGlI4wC8cXVMoBYBxWvWJ8erWz1LLbv6dYQeucTj9MExuExDoxZxtJn1-0SDONsGOWeftORryc55OXTrh6SqxS3YKjbtEjdHRFeo2zp217kp-gRgTSXmBdwq5DJJWt0ksiBY6H072TCdHwN5BpeAJaxKT1x_?width=397&height=300&cropmode=none){: width="397" height="300"}
   
   ![battery_benchmark](https://bn1303files.storage.live.com/y4m9YxymEwsmogPL1eWPwwQehYM9Cn6_FlzhNOHunrk0Spjn9xF0vS06w9dHomG0G-zjgGJz6gdJuyz6GbW94yTws0mSnNZLt53DEfmjtz7mQXaIhDLej5gA1M9VyiHb-nehEZ6piFBZ4S-TBc8sXH6LOd9LJfAkQsD5_IQ0uX_jYJuLBlP71E2OCc04-z1Z4x1?width=469&height=636&cropmode=none){: width="469" height="636"}
   


