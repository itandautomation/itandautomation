## Linuxt Tutorial - Part 4 : Debian12 Installattion : Step-By-Step

I am using Vmware Fusion which is a software hypervisor developed by VMWARE for macOS systems but you can choose to use any hypervisor such as Oracle Virtual Box.

+ Download Debian 12 for [arm64](https://cdimage.debian.org/debian-cd/current/arm64/iso-cd/) or [amd64](https://www.debian.org/download).
+ Once you have completed downloading the image of Debian 12. Open Vmvware Fusion and click on + icon and New.
+ Drag your image which you have downloaded before to start the installation and click on continue and click continue again and click on finish button.
+ Save the virtual machine, you can give any name here.
+ Once it is saved you can see your virtual machine in the virtual machine list.
+ Double click on it to start the installation process
+ Select install, select language and select your location.
+ Select the language of your keyboard and click next which will start to install files, libraries and components for debian 12.(This might take few mins depending on your hardware.)
+ Enter a hostname for your debain12 host.
+ You can enter domain name if you want or you can leave it blank here and click on continue
+ Enter you root password, please make sure you give the strong root password and hit the continue button
+ Verify the root password again.
+ Enter your username, you can give your name here and continue
+ Again give the strong password here
+ Verify password one more time and continue 
+ Select Guided - use the entire disk. (Please note here that the entire disk here is the only part of the disk that has been assign to this virtual machine in the start of the installation process and this can be increased or decreased later as per the needs.)
+ Select disk partition 
+ Select all files in one partition
+ Select finish partitioning and write changes to disk
+ Select to write the changes to disks.
+ Select No to scan extra media
+ Select No to use a Network mirror or you can also choose yes if you want to use a network mirror.
+ Choose No if you don’t want to participate in the package survey
+ Select the software for installation and by default ssh server and Standard System Utililites will be selected.
+ Click continue.
+ Installation will be completed and click on continue to reboot this virtual machine.
+ Once it reboots, you will be able to see a login screen
+ Enter your username what you have set up before during installation process and type your password. Please note that in Linux you won’t be able to even see anything while typing your password this is because Linux has a security features that hides the password from the screen. 
+ You can use **cat /etc/os-release** command to check about the OS release
