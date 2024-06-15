## Linuxt Tutorial - Part 5 : Rocky Linux 9.4 Installation : Step-By-Step

I am using Vmware Fusion which is a software hypervisor developed by VMWARE for macOS systems but you can choose to use any hypervisor such as Oracle Virtual Box.

**Downloading Rocky Linux 9 ISO**
+ Head over to the official Rocky Linux website: https://rockylinux.org/.
+ Click on "Downloads".
+ Under "Choose a release", select "Rocky Linux 9.0".
+ Choose the architecture (either x86_64 or aarch64) that matches your needs. Most likely, you'll want the x86_64 version.
+ Download the ISO file.

**Creating a New Virtual Machine in VMware Fusion**
+ Open VMware Fusion on your Mac.
+ Click "New Virtual Machine".
+ Drag the downloaded Rocky Linux 9 ISO file you downloaded earlier. Click "Continue".
+ And Click “Continue” again
+ Here, you can allocate resources to your virtual machine. VMware Fusion recommends a minimum of 2 CPU cores, 2GB of RAM, and 20GB of disk space which you can see in this screen. You can also adjust these based on your system's capabilities and your desired usage for Rocky Linux.
+ Click "Customize Settings" if you want to change the default virtual machine settings. Otherwise, click "Finish".
+ Give your virtual machine a recognizable name and choose a location to store it. Click "Save”
+ Once you save it VMware Fusion will automatically open the installation windows if not then click "Play" to power it on.
+ Select Install Rocky Linux 9.4 and hit enter
+ The Rocky Linux installer will boot. 
+ Choose your preferred language and keyboard layout, then click "Continue".
+ In the "Installation Summary" screen, you can review the configuration options. We'll focus on the key ones:
+ **Software Selection:** I have used Minimal ISO here so it only have few options available here but if you have used DVD ISO or BOOT ISO then you might see other options here too for example "Server with GUI" which provides a graphical desktop environment while "Minimal Install" is a text-based installation for experienced users. Choose your installation type. "Server with GUI" provides a graphical desktop environment, while "Minimal Install" is a text-based installation for experienced users. I will just choose “Minimal Install” for this demo and click on “Done”
+ **Installation Destination**: Select the disk where Rocky Linux will be installed. It should be pre-selected by default.
+ Under "User Settings", set a strong root password. This is the administrator account for the system or you can create any other user as an administrator.
+ To create a user account click on “User Creation”. Give the user details here. Make sure you set a strong password. Click “Done”
+ As you can see “Begin Installation” is still disabled as we haven’t set up an administrator account. So one thing to note here is either you have to set up a root account or you can make a new user as an administrator. I don’t want to set up root account here so I will make the user created previously as an administrator. 
+ To do that click on “User Creation” again make sure you check on “Make this user administrator” and hit  “Done” again. Now you can see that “Begin Installation” is enabled.
+ Review the installation summary and click "Begin Installation". The installation process will take some time.
+ **TIP:** Press the “control + command “on your keyboard to release it mouse cursor from the vmware fusion
  
**Post-Installation**
+ Once the installation is complete, the virtual machine will prompt you to reboot. Click "Reboot".
+ Upon reaching the login screen, log in with the user account and password you created during installation.
+ Type the command **cat /etc/os-release** to check about the operating system.
