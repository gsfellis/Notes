# 1 Using Linux

## 1.1 The Shell

### 1.1.1 Shell Overview

* The shell is a Command Line Interface (CLI)
* User has to type commands at the command prompt
* Many tasks to administer and support a Linux system must be done from the command line.
* Using a CLI opposed to a GUI saves system resources
* There are many shells to try:
  * sh (Bourne Shell) - oldest Linux shell designed for UNIX
  * bash (Bourne Again Shell) - Typical default CLI for most Linux systems
    * Command completion when pressing the Tab key
    * Command history
  * C Shell - Originally designed for BSD Unix and uses syntax is a variation of C programming
  * tsch Shell - Improved C Shell distributed with freeBSD
  * Z Shell - Improved bash shell
* Default shell can be found with:

```bash
echo $SHELL
```

* You can switch shells by using the shell command.
* List of installed shells can be found in /etc/shells
* Multiple shell sessions can be run at once
  * Typically can switch between shell sessions with Alt+F# keys
  * Sometimes Ctrl+Alt+F# may be used in other distributions
* Terminal sessions can be run from the GUI
* Shells use configuration files to establish their operating environments

### 1.1.3 Shell Commands

* Most tasks in Linux can be handled from the CLI
* PATH Environment Variable is different than a Windows System
* Linux does not look in the current directory
* Only searches for the file you're trying to run in the directories in the PATH environment variable.
* Can check the PATH:

```bash
echo $PATH
```

## 1.3 Text Editors

* **vi** or **vim**
* different modes
  * command mode - Can't edit the file but can move around in the file
    * dw - delete word after cursor with space (cuts for pasting)
    * de - delete word after cursor without space (cuts for pasting)
    * d$ - delete to end of line (cuts for pasting)
    * dd - deletes entire line (cuts for pasting)
    * p - paste at cursor
    * u - undo last action
    * D - delete to end of line without cut
    * yy - copy line for pasting
    * a - append after cursor
    * A - append after current line
    * C - move to end of line
    * cc - Change text of the entire line
    * Ctrl+g - displays status line
    * /*term* - search forwards for *term*
    * ?*term* - search backwards for *term*
  * Insert Mode - Can actually edit the file
    * I, INS, S, O, A will all start insert mode but each have different functions
    * Look for --INSERT-- at the bottom of the screen
  * Replace mode - Press INS again from Insert Mode
    * Look for --REPLACE-- at the bottom
  * Press ESC to return to Command Mode
  * Command line mode - Press : to enter commands
    * w - write, w filename - write to filename
    * q - quit
    * wq or exit - Saves file and quits
    * q! - quit without saving changes
    * w! - overwrite current file
    * e! - revert changes since last write

## 1.4 Aliases

* Shortcut to a command
* ll - alias for 'ls -l'
* .. - alias for 'cd ..'
* **alias** will display all aliases available
  * **alias details='ls -l'** creates an alias called details that runs 'ls -l'. Can also overwrite existing details alias
* **unalias [name]** removes an alias

## 1.5 Environment Variables

* A setting that defines the user's computing environment.
* Convention is to use uppercase characters, (e.g. SHELL and EUID)
* initially assigned default values from the shell configuration files.
* Can modify the default values assigned to an environment variable
* Modifying values assigned to environment variables only apply to the current session. You must **export** the modified variables to change other shell sessions.
* TO make changes persistent across system reboots, add the change to the appropriate shell configuration file(s)
* You can define non-environmnet variables at the shell prompt.
* Common environmnet variables:
  * BASH - location of the bash executable file
  * SHELL - the user's login shell
  * CPU - the type of CPU
  * DISPLAY - Location where X Windows output goes.
  * ENV - Location of the config file for current shell
  * EUID - ID number of the current user
  * HISTFILE - File name where past commands are stored
  * HISTSIZE - Number of past commands in HISTFILE for current session
  * HISTFILESIZE - Number of past commands in HISTFILE for multiple sessions
  * HOME - Absolute path of the user's home directory
  * HOST - name of the computer
  * HOSTNAME - same as HOST used by different distributions
  * INFODIR - The path to the computer's informatiopn pages
  * LOGNAME - The username of the current user
  * MAIL - The path to the current user's mailbox
  * MANPATH - The path to the computer's man pages
  * OLDPWD - The directory the user was in prior to switching to the current directory
  * OSTYPE - The type os OS. Usually, this is Linux.
  * PATH - The directory paths used to search for programs and files.
  * PS1 - The characters the shell uses to define what the shell prompt looks like
  * PWD - The path of the current working directory
  * LANG - The language that the OS uses
* Common environment variable commands
  * echo $[variable]
  * env - displays environment variables for all child sessions
  * set - set shell environment varaible. Without options, display the set environment variables for the system
  * unset [variable] - Remove an environment variable
  * [VARIABLE]=[value] - change the value assigned to a variable
  * export [variable] - Export a variable to make it available to all other shell sessions

## 1.6 Shell Configuration Files

* Shell configuration files execute when a shell starts. The shell type determines which shell configuration files are executed.
  * *Login shells* run when the system starts and is using only the CLI as the UI
  * *Non-login shells* run when a shell session is opened from within the GUI.
* Common shell files used:

| Configuration File | Description | Used by Shell Type |
|---|---|---|
| ~/.bashrc | Stores shell preferences for individual users. | Non-login and and login shells by most distributions. |
| /etc/profile | stores system-wide configuration commands and is used primarily to set environment variables. | Login |
| ~/.bash_profile | Stores shell preferences for individual users | Login |
| ~/.bash_login | Stores commands that execute when a user logs in | Login |
| ~/.profile | stores configuration preferences similar to /etc/profile, but for individual users | Login
| ~/.bash_logout | stores commands that execute when a user logs out. | Login

* Login shells execute the configuration scripts they use in the following order:
  1. /etc/profile
  1. ~/.bash_profile (If this file is found, the shell does not look for other files )
  1. ~/.bash_login (If this file is found, the shell does not look for other files.)
  1. ~/.profile (only in the absense of the two preceding files)

* The **su -l** command switches to a user and creates a new login shell; however, without the **-l** option, a non-login shell is started.

## 1.7 Redirection and Piping

* Administrators often use the following methods to manipulate information created by shell commands:

  * Redirection
    * *Redirection* directs standard input, output, and error streams to locations other than the default. Be aware of the following redirection details:

    * By default the Linux system classifies information with the following file descriptors:
      * Standard input (stdin) comes from the keyboard. Using redirection, 0 represents stdin.
      * Standard output (stdout) displays on the monitor. Using redirection, 1 represents stdout.
      * Standard errors (stderr) display on the monitor. Using redirection, 2 represents stderr.
  * Linux commands use the greater than symbol (>) to show redirection of output, the less than symbol arrow (<) to indicate redirection of input, and the doulbe greater than symbol (>>) to append output to an existing file.
  * The **tee** command writes to stdout *and* redirects to a file.

  * Piping
    * *Piping* directs the output of one command into the input of another command. Pipes:
      * Use the pipe symbol (|).
      * Can combine several commands to make a text stream.

* The following table lists some common redirection commands and their results

| Command | Result |
| --- | --- |
| ls /usr > /tmp/deleteme | Writes the list of files in the /usr directory to a file named /tmp/deleteme |
| ls /nonesuch > /tmp/deleteme | Does not write anything to a file and sends an error message to the monitor '/nonesuch not found' |
| ls /nonesuch 2> /tmp/deleteme | Writes the stderr message to a file named /tmp/deleteme, only if an error message is generated |
| ls /bin /nonesuch > /tmp/deleteme | Writes contents of the /bin directory to the file, but sends error message to screen |
| ls /bin /nonesuch 2>&1> /tmp/deleteme | Writes contents of /bin directory to file but sends error message to screen because stderr messages are directed to the same place that stdout goes, but this is before the stdout has been directed to the file. |
| ls /bin >> /tmp/deleteme | Appends the list of files to the end of /tmp/deleteme |
| sort < unordered_file.txt > ordered_file.txt | Takes input from unordered_list file, sends it to the sort command, and then writes a new file named ordered_file.txt |
| cat /usr/wordlist1 /usr/wordlist2 \| sort | Sends the output of the cat command to the input of the sort command, resulting in a sorted list of all items in wordlist1 and wordlist2 |
| cat /usr/wordlist1 /usr/wordlist2 \| mail jdoe | Mails the combined list of words in wordlist1 and wordlist2 to the user jdoe. |
| ls /bin \| sort \| mail jdoe | Lists the contents of /bin then sorts the combined contents and mails them to jdoe. |
| cat /usr/wordlist1 /usr/wordlist2 \| sort \| tee sortedwordlist | Lists the contents of the files, then sorts the combined contents, then sends the results to the monitor and a file named sortedwordlist |
| cat /usr/wordlist1 \| tee log.txt | Writes to the stdout and the log.txt file. |

## 1.8 Directories

* The following table describes basic commands you can use to manage directories on a Linux system:
  * pwd - Displays the current working directory.
    * If you're in your home directory, pwd will display /home/YourUserName
  * cd - Changes the present working directory
    * **cd ..** changes to the parent directory
    * **cd /** changes to the root directory
    * **cd dir1** changes to dir1 within the current working directory (This is a *relative* path)
    * **cd /home/Fred/dir1** switches to dir1 in Fred's home directory. (This is an *absolute* path)
  * ls - Display the contents of a directory.
    * **-a** displays all directory contents, including hidden content
    * **-l** displays extended info, including owner, modified date, size and permissions
    * **-R** displays the contents of a directory and all of its subdirectories.
    * **-d** displays directories but not files
    * **-r** reverses the sort order.
  * mkdir - creates a new directory.
    * **-p** creates all directories within the specified path that do not already exist
  * cp -r - Copies directories.
  * mv - Moves or renames directories and files.
    * **-f** Overwites a directory that already exist.
    * **-i** Prompts before overwriting a directory
    * **-n** never overwrites files in the destination directory.
  * rmdir - Deletes an empty directory
  * rm - Removes the directory (and file) inode, but not actually delete the data.
    * **-r** deletes directories (and all files) in the directories
    * **-f** deletes without prompting

## 1.9 Files

## 1.10 Links

## 1.11 Filesystem Hierarchy Standard (FHS)

The Filesystem Hierarchy Standard (FHS) defines a consistent file system for Linux systems by defining a standard set of directories, subdirs, and files. FHS is a subset of the Linux Standards Base (LSB) which is an organization and a set of guidelines for promoting a set of standards to increase Linux distribution compatibility.

| Directory | Description |
| --- | --- |
| / | The **/** character represents the root directory. ALl other directories are located beneath the **/** (root) directory of the system. |
| /bin | **/bin** directory contains binary commands that are available to all users |
| /boot | **/boot** directory contains the kernel and bootloader files | 
| /dev | **/dev** directory contains device files that represent the devices used by the system, such as a hard drive, mouse, and printer. |
| /etc | **/etc** contains configuration files specific to the system. |
| /home | **/home** contains (by default) the user home directories. |
| /lib | **/lib** contains shared program libraries and kernel modules. |
| /media | **/media** is used to mount removable media |
| /mnt | **/mnt** is used for temporarily mounting remote file systems. |
| /opt | **/opt** contains additional programs on the system |
| /proc | **/proc** contains information about the system state and processes. |
| /root | **/root** is the root user's home directory, not to be confused with the root **/** of the file system. |
| /sbin | **/sbin** contains system binary commands. |
| /srv | **/srv** contains files for services such as HTTP and FTP servers |
| /sys | **/sys** contains the *sysfs* virtual file system which displays information about devices and drivers. |
| /tmp | **/tmp** contains temporary files created by programs during system use. |
| /usr | **/usr** contains system commands and utilities. |
| /var | **/var** directory contains data files that change constantly like user mailboxes, print queues, and log files. |

## 1.12 Locating and Searching Files