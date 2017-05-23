# 7 Disk and File System Management

## 7.9 Permissions

Every file and directory in the Linux file system has an *inode* (information node) that stores info about the file or directory, including when it was last modified, size, data block location, permissions, and ownership. The portion of the inode that stores permission information is called the *mode*. The mode has three sections:

* User permissions (owner)
* Group permissions (group owner)
* Other permissions (everyone else on the Linux system who is not an owner or a member of the owning group)

There are three types of permissions contained in the mode, each of which is described in the table below:

| Permission | Letter Abbreviation | Octal Value | Allowed Actions on Files | Allowed Actions on Directories |
| --- | --- | --- | --- | --- |
| Read | r | 4 | Open and read the file | List directory contents if the execute permission is also present |
| Write | w | 2 | Edit the file and save the changes | Add, delete, and rename files if the execute permission is also present |
| Execute | x | 1 | Execute the file, if it's a program file or a shell script (must be used in conjunction with the read permission) | Enter the directory and access its contents |

Permissions are identified with either the letter abbreviation (**r, w,** or **x**), or the octal value that corresponds to the permission.

If permissions read: **-rwxrw-r--**, in order these mean:

* rwx = 4+2+1
   * The User permissions are 7
* rw- = 4+2
  * The Group permissions are 6
* r-- = 4
  * The Other permissions are 4

In the mode:

* A **d** preceding the permissions indicates that the object is a directory.
* A **-** dash preceeding the permissions identifies a file
* Permissions are grouped according to user, group, or other permissions.
* If a given permission has *not* been assined, a **-** dash takes its place in the mode.
* When using numbers to represent permissions, add the number together within each permission group. Then string the numbers together.
* The root user has all permissions to files and directories regardless of the mode settings.

Common commands for managing permissions:

* ls -l
  * View a long listing of files and directories. A long listing displays the permissions assigned to files and directories
* chmod
  * Change the permissions for the specified file.
  * The following syntax options exist:
    * **entity+permission** adds a permission for a user, group, or other to a file or directory
      * **chmod u+x,g+x,o+x myfile** addes execute to *myfile* for all entities.
    * **entity-permission** removes a permission for a user, group, or other from a file or directory
      * **chmod g-w,o-w myfile** removes write permissions for the group and other entities on *myfile*
    * **entity=permission** sets the permission equal to the permission specified for a user, group, or other for a file or directory
      * **chmod u=rwx myfile** grants the user read, write, and execute permissions for the *myfile* file.
    * **decimal_value** sets the permissions for the file according to the numbers represented for each mode entity.
      * **chmod 711** grants -rwx--x--x permissions on *myfile* file.
    * **-R** sets permissions recursively