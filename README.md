# DELL_XPS_9575_9570_Linux_Ubuntu_Install

Install Ubuntu along with Windows on Dell XPS 9575 or 9570. I have tested with Pop! OS, Elemontry OS and Ubuntu 20.04.

There are following steps:

## Shrinking Your Windows Partition

To install Ubuntu 20.04, you need to first create a partition for it. You can do this by taking the following steps:
* Type “Create and Format Hard Disk Partitions” in the Windows Search Bar.
* Right click on the largest partition and click “Shrink Volume”.
* Choose the desired size for Ubuntu 20.04 (eg. 40–200 GB, depending on your storage size).
* See the newly created “Unallocated space” in the partition diagram.

## BIOS: Switch from RAID to AHCI Mode

**If you want to use Linux along with Windows, you have to do this for your DELL XPS.**
* Type “cmd” into the Windows Search Bar, then click “Run as administrator”.
* This next step makes your computer boot into safeboot. This is needed for the RAID to AHCI transition. Type this command and press ENTER:

`bcdedit /set {current} safeboot minimal`

* Restart the computer and enter the BIOS Setup. For the Dell XPS 15 9575, this means restarting the laptop and then repeatedly pressing F12 during the restart.
* Under System Configuation, change the SATA Operation mode from RAID to AHCI.
* Save changes and try to boot into Windows. It will automatically boot to Safe Mode.
* Type “cmd” into the Windows Search Bar, then click “Run as administrator”.
* This next step makes your computer not boot into safeboot. Type this command and press ENTER:

`bcdedit /deletevalue {current} safeboot`

* Reboot once more and Windows will automatically start with AHCI drivers enabled.

## Install Ubuntu

* Plug in the USB stick containing Ubuntu, Restart the computer and Pressing F12
* Choose the USB stick as the boot option, then you can follow the normall installation of Ubuntu as usual, I haven't made much change in the steps, most of them are just default.

## After Installation

You should not make any change after installation. However, you can do some optimisation:

* Make Grub List font bigger (all the words are tiny in 4K screen), please use

`sudo apt-get install grub-customizer`

and change the font to 30

* It your Linux system use GNOME, you can install some addons in https://extensions.gnome.org/, there are many useful and popular addon to make your system much easier to use, espcailly the ones in the first page (the most popular)!

* Highly suggeset you to install Chrome (https://www.google.co.uk/chrome/) (Not Chromium) in your OS, it will allow you to install Youtubue Music and work with Cast!

* Time zone auto adjust for both system:

`timedatectl set-local-rtc 1 --adjust-system-clock`

* Dispaly problem when switching to Windows

`sudo gedit /etc/default/grub

#Uncomment to disable graphical terminal (grub-pc only)

GRUB_TERMINAL=console

sudo update-grub`

## Reference

https://medium.com/@tylergwlum/my-journey-installing-ubuntu-18-04-on-the-dell-xps-15-7590-2019-756f738a6447

https://support.system76.com/articles/customize-gnome/
