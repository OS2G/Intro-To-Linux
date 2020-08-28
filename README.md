
# Welcome to the 90s
An introduction to Linux and making it work on ~~the world's worst operating system,~~ Windows.

## What is Linux?
### An operating system
Linux is an operating system, similar to Windows and related to macOS. It runs on a set of hardware to orchestrate the connections of said hardware together into something known as a personal computer, allowing you to run software on top such as word processors, or access everyone's favorite thing: ~~Internet Explorer~~ the Internet. It can run on bare bones hardware, or be virtualized.

### How does it work?
#### A history
Linux at its heart is only a kernel. That is to say, it is the core. It's based on an older kernel named UNIX. There's history to that, but it doesn't really matter. It simply manages hardware and provides an interface for higher level software to interact with that hardware in an abstracted way. The shell, where you run commands, is a program that allows you to interact with the kernel and devices it manages. More software allows you to continue to provide more functionality, providing a competent user "friendly" experience where you can achieve your dreams. This is how we got to Graphical User Interfaces, or GUIs for short.

#### Files
In Windows, every drive has a letter (`C:`). Every folder under it contains your files and the files the system needs. You have `Windows` as the place where the the Windows operating system lives, and folders such as `Program Files` and `Users` also used to allow programs to have a place and users to have files.

In UNIX based operating system, everything is a file. Whether it's a device, a folder, and actual file; it's all referenced as a file in the system. Therefore, the boot drive is rightfully named the root, and is `/`. Everything stems from there. `home` is where you put your files. `etc` has system configurations. `usr` has libraries and program files. `bin` has references to binaries, or programs. There are more, but it's not very important.

This sounds... interesting? Can you show me how to use it?

## How can I use it?

There are many ways to use it, but we will be focusing on Windows and WSL.

#### Install it
Similar to Windows (and macOS), it can be installed on hardware. You grab the OS and set up a flash drive with its installer and you're good to go.

#### Virtualization
You can run Linux virtually. This can be done by downloading something like VirtualBox and then also downloading the OS itself.

#### macOS
macOS is based on NeXTSTEP which was stemmed from UNIX, the operating system Linux took its inspiration from. As such, many of the commands that exist in Linux are also standard in macOS Terminal thanks to Berkley's Software Distribution (BSD).

#### Linux
Why are you even asking?

#### Windows
- Bash emulators such as MinGW and Cygwin allow you to run natively compiled Linux programs under Windows, but doesn't allow you to have a real Linux experience, nor run programs compiled for Linux.
- Windows Subsystem for Linux is an integration Microsoft made allowing for Linux calls to translate to Windows calls so you have fast performance while running native Linux programs.
- As mentioned earlier, you can virtualize it using something like VirtualBox.

## WSL
We recommend you use Windows Subsystem for Linux
Windows has a tutorial: https://docs.microsoft.com/en-us/windows/wsl/install-win10

### Getting the back-end
*Note:* You will need to restart your system after doing this, be prepared!

1. Or, search for "Turn windows features on or off"
2. Find "Windows Subsystem for Linux" and check it, clicking "Ok" to apply changes
3. Allow windows to install it if need be. You may need to restart or computer.

If you want to indulge in Windows CLI and do it in one go:
- Open up powershell as Administrator and run:
```
dism.exe /online /enable-feature /featurename:Microsoft-Windows-Subsystem-Linux /all
```

### Getting a distribution of Linux

1. Open the Microsoft Store
2. Search for "Ubuntu"
3. Install it (no need to login to Microsoft Store)

### Setting up Linux in WSL
1. Search for "wsl" in windows search and open it
2. It will start setting itself up, it will take awhile
3. Set your preferred username and password.

*A quirk of Linux/UNIX CLI is that passwords don't show up as asterisks, the keyboard cursor just doesn't move. Hit enter after you have typed in your password.*

Knock knock Neo. Follow the white rabbit.

### Where's my GUI?!
Linux, like every operating system, has a command line based shell it operates on. It's the basis of how everything works.

Both macOS and Windows abstract that command line shell and instead have startup scripts that simply run the services and programs necessary to give you mouse support and graphical windows you can touch with your fingers and move around.

Many distributions of Linux do the same. For instance, modern version of Ubuntu run a modified version of Gnome Desktop. Even with all of the graphical tools at hand, sometimes you need to get nitty gritty and use some commands to reach your goal. This is especially true if you're doing programming.

## Alright, so how does this work?

### Command Line Tutorial
1. Determine where in the file system the shell opens to
	- `pwd`
	- `echo $HOME` (shows the bash alias for the home directory)
	- `echo ~` (shows this is another usable symbol)
2. View what all is in the current folder
	- `ls` (shows everything currently there)
	- `ls -a` (show hidden files)
3. What are `.` and `..`? (current directory and parent directory)
	- `ls -a .` (does the same thing as ls -a but shows syntax order: command [flags] inputs)
	- `ls -a ..` (shows the parent directory’s content, which will include the current folder)
4. How do we move around inside the file system?
	- `cd` (change directory) (automatically moves you to the user’s home directory)
	- `cd ..` (goes up to the parent directory)
	- `cd .` (then does nothing - you’re telling the computer to change directories to the current directory)
	- `cd ~` (will go back to the home directory)
	- `pwd` to confirm they’re back in the home directory
5. Creating stuff!
	- `mkdir testfolder` (creates a new directory called testfolder)
	- `touch example` (creates an empty file called example)
	- Use `ls` to show the new folder and file
6. Manipulating files
	- `mv ./example ./example.txt` (turns the original file into a text file)
	- `cp ./example.txt ./testfolder/newtest.txt`
	- `ls` (shows the change in the example file)
	- `ls testfolder/` (shows the change in the internal file name)
7. Clean it up
	- `rm example.txt` (gets rid of the original file)
	- `rm -r ./testfolder/` (gets rid of the file and the folder)
		- BE VERY CAREFUL! This is recursive, so if you input the wrong sequence, you will not be able to recover what you delete.
8. Use `vi` to create a text file
	- `vi` (opens the editor)
		- `:q` (quits the editor)
	- `ls` (no new file!)
	- `vi test` (will show file name at the top of the editor)
		- Type up gibberish (for the sake of example)
		- `:!q` (will not save the file and then quits)
	- `vi test` 
		- `“i”/”esc”` (changes modes in the editor - worth touching on/explaining)
		- `“The quick brown fox jumped over the lazy dog”` (This can be other stuff)
		- `:w` (saves the text)
		- `:q` (quits the editor)
	- Move around with `k,j,h,l`
9. View the contents of a file
	- `cat test` (prints the contents of the file)
	- `more test` (reads the contents of the file)
10. Modify file permissions
	- `chmod 444 test` (sets the file to be read only)
	- `vi test` (Try to edit the text file)
		- `:wq` (Make some changes and try to save them)
		- Will tell you it’s denied!
	- `chmod 644 test` (sets the file to be writable by user)
	- `vi test` (Try to edit the text file)
		- `:wq` (Make some changes and try to save them)
		- This time it will work!
11. Modify file ownership
	- `chown root:root test` (try to change ownership, will fail)
	- `sudo chown root:root test` (have to be root to change the ownership to a user that's not you)
	- `ls -l` to see owners and permissions
	- `sudo chown $USER:$USER test` (take ownership again
12. Install a different text editor
	- `sudo apt update` (updates the package database)
	- `sudo apt install nano` (installs the package "nano")
	- `nano` (opens the nano editor)
13. Install other applications
	- `sudo apt install hollywood`
	- `hollywood`
	- spam `^c` to quit all windows (ctrl + c)
 
### Cheat Sheet
1. `pwd`: Will return the current directory
2. `ls`: List everything in current directory
	- -a shows hidden files
	- -l list format
3. `cd`: Change directory
	- `cd .`  = Change into current directory
	- `cd ..` = Change into the previous directory
	- `cd ../..`= Move 2 directories up
4. `mkdir dirName`: Make directory/ Create folder
5. `touch fileName`: Create/Update a file called “fileName”
	- No type automatically assigned
6. `touch fileName.txt`: Create a text file called “fileName”
	- Editors
		- `vi`
		- `vim`
		- `nano`
		- `emacs`
7. `cp file location`: Copy file into location
8. `rm file`: remove file
	- PERMANENT
9. `rmdir`: Remove Folder
	- Permanent (folder must have no files in it otherwise)
10. `man command`: Manual for command


### Further Resources
* [Learn the way of the Linux-Fu (linuxjourney)](https://linuxjourney.com/)
