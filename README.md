# DELL_XPS_9575_9570_Linux_Ubuntu_Install
Install Ubuntu along with Windows on Dell XPS 9575 or 9570

There are following steps:

# Shrinking Your Windows Partition
To install Ubuntu 20.04, you need to first create a partition for it. You can do this by taking the following steps:
• Type “Create and Format Hard Disk Partitions” in the Windows Search Bar.
• Right click on the largest partition and click “Shrink Volume”.
• Choose the desired size for Ubuntu 20.04 (eg. 40–200 GB, depending on your storage size).
• See the newly created “Unallocated space” in the partition diagram.

# BIOS: Switch from RAID to AHCI Mode
*If you want to use Linux along with Windows, you have to do this for your DELL XPS.*
• Type “cmd” into the Windows Search Bar, then click “Run as administrator”.
• This next step makes your computer boot into safeboot. This is needed for the RAID to AHCI transition. Type this command and press ENTER:
bcdedit /set {current} safeboot minimal

• Restart the computer and enter the BIOS Setup. For the Dell XPS 15 9575, this means restarting the laptop and then repeatedly pressing F2 during the restart. This has to be done early and often to work.
• Under System Configuation, change the SATA Operation mode from RAID to AHCI.
• Save changes and try to boot into Windows. It will automatically boot to Safe Mode.
• Type “cmd” into the Windows Search Bar, then click “Run as administrator”.
• This next step makes your computer not boot into safeboot. Type this command and press ENTER:
bcdedit /deletevalue {current} safeboot
• Reboot once more and Windows will automatically start with AHCI drivers enabled.

# Install 
Then you can follow the normall installation of Ubuntu as usual

# After Installation

Reference:
https://medium.com/@tylergwlum/my-journey-installing-ubuntu-18-04-on-the-dell-xps-15-7590-2019-756f738a6447
