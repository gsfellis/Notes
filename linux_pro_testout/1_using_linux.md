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