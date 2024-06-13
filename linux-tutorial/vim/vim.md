## Linuxt Tutorial - Part 8 : VIM basics - A Comprehensive Guide for New Users

Vim stands for "Vi IMproved." Most of the linux distribution comes with default text editors like ‘vi’ and ‘nano’. ‘vim’ is an upgraded version of the older Vi editor created for Unix systems. It's a highly configurable text editor built to enable efficient text editing. Vim is available on almost all Unix-based systems, including Linux. What makes Vim special is its modal nature, which means it has different modes for inserting text, navigating, and executing commands.

Before we use vim text editor we have to make sure it’s installed. You can check it by running `which vim` command. If it’s installed then it will show the path where it is installed. 

+ Installation (Debian or Ubuntu)
`sudo apt-get install vim`
+ Installation (Redhat,CentOS, Rocky)
`sudo yum install vim` or `sudo dnf install vim`

Create any file using `touch <file-name>` or you can direclty use vim to create and write on the file. Let's open a test file by typing: `vim <file-name>`

Now you are in 'vim'

Vim has several modes, but the three main ones are:

**Normal Mode:** This is the default mode when you start Vim. Here, you can navigate and use commands.

**Insert Mode:** This mode allows you to insert text. You can enter this mode by pressing 'i', 'a' and 'o'.

**Command Mode:** You can execute commands to save, exit, and perform various operations. You can enter this mode by pressing ':' (colon) in Normal mode.

Let's go through some essential commands to get you started.

**Insert Mode:** 

+ To start typing, you need to enter 'Insert mode' Press 'i' in 'Normal mode'. Now you can type as you would in any text editor. To return to 'Normal mode', press 'Esc'. You can see 'Insert' disappear from the terminal and it has now enter into 'Normal mode'.

**Saving and Exiting:**

+ To save your file and exit 'vim', type `:wq` (which means write and quiet) and press 'Enter'. Now let’s check this file using 'cat' command. 
+ Now let’s open the file again usig 'vim' and try to use save only 
To save the file without exiting, type `:w` and press 'Enter'. Now the file has been saved. If you want to exit type `:q` or colon `q!` to force exit and press 'Enter'.
+ Now again let’s check using 'cat' command `cat <file-name>`. You can see  the file has been updated.

**Navigating:**
+ Now let’s look into how we Navigate in vim. Make sure you are in 'Normal mode'and move the cursor 'up', 'down', 'left', and 'right' using the arrow keys(left right up and down) or you can also use 'h'(for moving left), 'l' (for moving right ), 'k'(for moving up), and 'j'(for moving down) respectively.

+ To Jump to the beginning of a line pres `0`(zero) and to jump to the end of the line press `$`(dollar).
To move by words, use w to move to the start of the next word… and b to move back to the start of the previous word.

+ Deleting text: 
To delete a character, position the cursor over it and press `x` or you can switch to 'Insert mode' and use back arrow key to delete any text from backwards but be very careful when you switch to 'Insert mode'.
+ To delete a word, position the cursor at the start of the word and press `dw`. It deletes a single word.
+ To delete a line, press `dd`. You can see it deletes the entire line.

+ Set line numbers: Now let’s look into how to set line numbers. Line numbering is useful for navigating and referencing specific lines in your code or text files.
Press `esc` key to switch to 'command mode' Press `:` and the curson will move at the bottom left corner of the screen. Then type `set number` or `set nu` and hit 'Enter'. You can see the line number displayed at the left side of the screen.
+ To disable this line number you can again type `:set nonumber` or `set nu!` or also type `set number!` Which will disappear the line number.

**Search text in VIM**
+ Type `/` (forward slash)and enter the word you want to search. Press `?` for backward 

**TIPS**
+ Here are some quick tips to enhance your Vim experience:
+ Learn the Shortcuts: Vim has a steep learning curve, but learning the shortcuts can make you much more efficient.
+ Use Vimtutor: 'Vim' comes with a built-in tutorial. Just type `vimtutor` in your terminal to start learning.
+ So Vim is an incredibly powerful tool, and with practice, you can become very efficient at editing text. Whether you're writing code, editing configuration files, or taking notes, Vim has the capabilities to make your workflow smoother.

### Other Resources
---
+ [Quick Start Guide to Basic Linux Commands](https://github.com/itandautomation/itandautomation/tree/main/linux-tutorial/linux-commands)
