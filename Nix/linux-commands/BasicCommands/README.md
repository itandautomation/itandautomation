## Linuxt Tutorial - Part 7 : Quick Start Guide to Basic Linux Commands

First things first, to start using Linux commands, we need to open the terminal. If you are using Mac then the terminal comes installed by default and if you are using Windows then you can use Windows terminal or windows PowerShell which also comes installed by default. Also on most of the Linux distributions terminal comes installed by default. There are also many 3rd parties terminals available such as putty, mobaxterm, iterm, warp etc. You can try to google it and see which are available.  Once you have your terminal open, you'll see a command prompt where you can start typing commands."

**1. pwd - Print Working Directory**
+ This stands for 'Print Working Directory', and it shows you the current directory you're in. Just type `pwd` and hit 'Enter'. It displays the full path of the current directory.

**2. ls - List Directory Contents**
+ It lists the contents of a directory. Simply type `ls` and press 'Enter'. This command shows all the files and folders in the current directory. You can also use options like `ls -l` for a detailed list, including file permissions, owner, size, and modification date. 

**3. cd - Change Directory**
+ To navigate through directories, we use the `cd` command, which stands for 'Change Directory'. For example, to move into a directory, you'd type `cd <dir-name>`. You can always go back to the previous directory by typing `cd ..`

**4. mkdir - Make Directory**
+ `mkdir` which stands for ‘Make Directory’. Creating new directories is easy with the `mkdir` command. Let's create a new directory named 'test'. Just type `mkdir test`.
Now, if we use `ls` again, we can see the new 'test' directory.

**5. rm and rmdir - Remove Files and Directories**
+ To remove files, we use the `rm` command, and for directories, we use `rmdir`. Be careful with these commands, as they permanently delete files and directories. For example, `rm <filename>` deletes a file, and `rmdir <directory-name>` deletes an empty directory.

**6. touch - Create an Empty File**
+ If you need to create an empty file, you can use the `touch` command. For eg, `touch touch1.txt` will create a new, empty file named 'touch1.txt'." You can also create multiple file using this command for eg: `touch test1 test2 test3`. Now, let's check with `ls` to see our new file."

**7. cp - Copy Files and Directories**
+ To copy files, we use the `cp` command. For example, `cp example.txt example_copy.txt` will create a copy of 'example.txt' named 'example_copy.txt'. You can also use `-r` to copy directories recursively.

**8. mv - Move or Rename Files and Directories**
+ The `mv` command is used for moving or renaming files and directories. For example, `mv example.txt new_example.txt` renames 'example.txt' to 'new_example.txt' Now let's try to move a file into a directory using this `mv` command. `mv <file-name> <dir>`. This will move the file inside the diretory. 

**9.  cat - Concatenate and Display Files**
+ The cat command is used to display the contents of a file. For example, `cat <file-name>` will show the contents of the file(file-name) which you have used for." 

**10.  man - Manual Pages**
+ Finally, if you ever need help with a command, you can use the `man` command, which stands for 'manual'. Just type `man` followed by the command name, like `man ls`, to get detailed information about this command. As you can see many options that can be used with ls command. So if you wanted to know anything about the commands or in more detail to use commands use `man`  followed by any command. 

### Other Resources
---
+ [ssh](https://github.com/itandautomation/itandautomation/tree/main/linux-tutorial/ssh) - Mastering SSH on Linux

