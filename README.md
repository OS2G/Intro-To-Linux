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

### Install it
Similar to Windows (and macOS), it can be installed on hardware. You grab the OS and set up a flash drive with its installer and you're good to go.

### Virtualization
You can run Linux virtually. This can be done by downloading something like VirtualBox and then also downloading the OS itself.

### macOS
macOS is based on NeXTSTEP which was stemmed from UNIX, the operating system Linux took its inspiration from. As such, many of the commands that exist in Linux are also standard in macOS Terminal thanks to Berkley's Software Distribution (BSD).

### Linux
Why are you even asking?

### Windows
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

## Where's my GUI?!
Linux, like every operating system, has a command line based shell it operates on. It's the basis of how everything works.

Both macOS and Windows abstract that command line shell and instead have startup scripts that simply run the services and programs necessary to give you mouse support and graphical windows you can touch with your fingers and move around.

Many distributions of Linux do the same. For instance, modern version of Ubuntu run a modified version of Gnome Desktop. Even with all of the graphical tools at hand, sometimes you need to get nitty gritty and use some commands to reach your goal. This is especially true if you're doing programming.

## Alright, so how does this work?
