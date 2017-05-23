# 6 Users and Groups

## 6.1 Users and Groups Overview

*User* accounts control the ability to log on to a system, access resources, and perform certain actions.

*Groups* provide a means of grouping users for administrative purposes such as assigning permissions to files.

* Different types of users and groups:
  * Standard user
    * Standard user accounts can log into the system.
    * Have friendly usernames created by an Administrator
    * Have an ID of 500 or more (on some distributions) or 1000 or more (on others). The ID is automatically assigned by the system when the account is created.
  * System user
    * System user accounts are created by default during the Linux Installation
    * Used by the systme for specific roles.
    * Have names that correspond with their roles, such as ftp and mail.
    * Cannot be used to log into the system.
    * Have an ID of 500/1000 or less and is automatically assigned by the system when the account is created.
    * The root user account is created by default and has a UID of 0; however, it can be used to log into a system.
  * Primary Group
    * Created by default on most Linux distros when a standard user is created and are used to manage access to files and directories.
    * Have the corresponding user as the only member.
    * Are automatically assigned as the owner of files and directories when they are created in the file system.
    * Are similar to any other group. The only difference is that the group is identified as the primary group in the user account's configuration.
  * Secondary group
    * Also used to manage access to files and directories.
    * Are not automatically assigned user accounts as members.
    * Receive their membership as assigned by the system administrator.

User and group databases are stored in the following files:

* /etc/passwd
  * Holds user account information.
  * Each entry identifies a user account
  * Each entry contains multiple fields, with each field seperated by a colon.
  * The following line is a sample entry in the **/etc/passwd** file:
    * pclark:x:501:501:Petunia Clark:/home/pclark:/bin/bash
  * The fields within this line are as follow:
    * username
    * Password
    * UID
    * GID
    * Description
    * Home Directory Path
    * Path to Default Shell
* /etc/shadow
  * Holds passwords and password expiration information for user accounts.
  * Using the **/etc/shadow** file to seperate usernames from passwords icreases the security of the user passwords
  * Each entry corresponds to a user account and each entry contains multiple fields, with each field seperated by a colon.
  * The following line is a sample entry in the /etc/shadow file:
    * pclark:$ab7098guuoiu:12567:0:99999:7:::
  * The fields within this line are as follows:
    * User account name
    * Password
      * $ preceding the password identifies the password as encrypted
      * ! or !! indicate the account is locked
      * * indicates a system account entry and connot be used to log in
    * Last change - The date of the most recent password change, measured in the number of days since 1/1/1970
    * Minimum password age - user must wait before changing password
    * Maximum password age - The max days between password changes
    * Password change warning - Number of days a user is warned before the password must be changed
    * Grace logins - The number of days the user can log in without changing password
    * Disable time - The number of days since 1/1/1970 after the account will be disabled.
* /etc/group
  * Holds group information including the group name, GID, and group membership information.
  * Each entry identifies a group
  * Each entry contains multiple fields, with each field separated by a colon.
  * Sample entry in /etc/group:
    * sales:x:510:pclark,mmckay,hsamson
  * The fields within this line are as follows:
    1. Group name
    1. Group password. An x indicates the group passwords are contained in the /etc/gshadow file.
    1. Group ID
    1. Group members. Contains a comma-separated list of user accounts that are members of the group.
* /etc/gshadow
  * Holds passwords for groups.
  * Each line corresponds to a group
  * Each line consists of fields separated by colons.
  * Sample entry in /etc/gshadow:
    * sales:!:pclark:pclark,mmckay,hsamson
  * The fields within this line are as follow:
    1. Group name
    1. Group password. The group password allows users to add themselves as members of the account. If this field contains:
      * ! - the group account cannot be accessed using the password.
      * !! - no password has been assigned to the group account (and it cannot be accessed using the password)
      * No Value - Only group members can log in to the group account
    1. Administrators - Contains a comma-separated list of users who have authorization to administer the account
    1. Group members. A comma-separated list of user accounts that are members of the group.

Additional commands for managing file entries include:

* **pwck** command verifies the entries in the **/etc/passwd** and **/etc/shadow** files. Errors are displayed on the screen, and entries may be deleted to solve the errors.
* The **pwconv** command synchronizes the entries in the **/etc/passwd** and **/etc/shadow** files.

## 6.2 User Management

Be aware of the following configuration files when managing user accounts:

* /etc/default/useradd
  * Contains default values used by the useradd utility when creating a user account, including:
    * Group ID
    * Home directory
    * Account expiration
    * Default shell
    * Secondary group membership
    * Skeleton directory
* /etc/login.defs
  * Defines:
    * Values used to define allowed group and user ID numbers.
    * Protocols to be used for password encryption in the shadow file.
    * Password aging values for user accounts.
    * The path to the default mailbox directory
    * Whether a home directory should be created by default.
* /etc/skel
  * Contains a set of configuration file templates that are copied into a new user's home directory when it is created, including the following files:
    * .bashrc
    * .bash_logout
    * .bash_profile
    * .kshrc

Although it is possible to edit the **/etc/passwd** and **/etc/shadow** files manually to manage user accounts, doing so can disable your system. Instead, use the following ocmmands to manage user accounts:

* useradd
  * creates a user account.
  * The following options override the settings found in **/etc/default/useradd**:
    * **-c** add text for the account in the description field of **/etc/passwd**. This is commonly used to specify the user's full name.
    * **-d** assigns an absolute pathname to a custom home directory location
    * **-D** displays the default values specified in the **/etc/default/useradd** file.
    * **-e** specifies the date on which the user account will be disabled.
    * **-f** specifies the number of days after a password expires until the account is permanently disabled.
    * **-g** defines the primary group membership
    * **-G** defines the secondary group membership
    * **-M** does not create the user's home directory.
    * **-m** creates the user's home directory (if it does not exist)
    * **-n (Red Hat), N (Fedora)** does not create a group with the same name as the user
    * **-p** defines the encrypted password.
    * **-r** specifies that the user account is a system user.
    * **-s** defines the default shell.
    * **-u** assigns the user a custom UID.
  * Example use:
    * **useradd pmaxwell** creates the *pmaxwell* user account.
    * **useradd -c "Paul Morril" pmorril** creates the *pmorril* account with a comment.
    * **useradd -d /tmpuser/sales1 sales1** creates the *sales1* user account with the home directory located at */tmpusr/sales1*.
    * **useradd -u 789 dphillips** creates *dphillips* account with UID 789.
* passwd
  * Assign or change a password for a user.
  * **passwd** without a username changes the current user's password.
  * Users can change their own passwords. The root user can execute all other **passwd** commands.
  * Be aware of the following options:
    * **-S** *username* displays the status of the user account.
      * LK indicates that the user account is locked.
      * PS indicates that the user account has a password.
    * **-l** disables (locks) an account. (Inserts !! before the password in **/etc/shadow** file.)
    * **-u** enables (unlocks) an account.
    * **-d** removes the password from an account.
    * **-n** sets the minimum number of days a password exists before it can be changed.
    * **-x** sets the number of days before a user must change the password (password expiration time)
    * **-w** sets the number of days before the password expires that the user is warned.
    * **-i** sets the number of days following the password expiration that the account will be disabled.
  * Example use:
    * **passwd jsmith** changes the password for jsmith
    * **passwd -x 40 jsmith** requires jsmith to change his password every 40 days.
    * **passwd -n 10 jsmith** means that jsmith cannot change his password for 10 days following a change.
    * **passwd -w 2 jsmith** means that jsmith will be warned 2 days before his password expires.
* usermod
  * Modify an existing user account. **usermod** uses several of the same switches as **useradd**.
* userdel
  * Remove the user from the system.
  * Be aware of the following options:
    * **userdel *username*** removes the user account
    * **-r** removes the user's home directory.
    * **-f** forces the removal of the user account even when the user is logged into the system.

## 6.3 Group Management

Use the following commands and options to manage group accounts and group membership:

* groupadd
  * Create a new group
  * The following options override the settings found in /etc/login.defs:
    * **-g** defines the group ID (GID)
    * **-p** defines the group password
    * **-r** creates a system group
  * Example:
    * **groupadd sales** creates the sales group
* groupmod
  * Modify a group definition.
  * Options include:
    * **-n** changes the name of a group.
    * **-A** adds specified users from the group (not available in all distros)
    * **-R** removes specified users from teh group (not available in all distros)
  * Examples:
    * **groupmod -n sales2 sales** renames the sales group to sales2
    * **groupmod -R rsem sales** removes the rsem account from the sales group.
* groupdel
  * Delete a group
  * Example:
    * **groupdel mktg** deletes the mktg group
* gpasswd
  * Change a group password
  * Specifying a *groupname* prompts for a new password
  * **-r** removes a group password
  * Example:
    * **gpasswd sales** prompts for a new group password
* newgrp
  * Log in to a new group with the group password
  * Example:
    * **newgrp sales** prompts for the password for the sales group before logging in.
* usermod
  * Modifying group membership for the user account.
  * Be aware of the following options:
    * **-g** assigns a user to a primary group
    * **-G** assigns a user to a secondary group (or groups). Follow the command with a comma-separated list of groups. If the user already belongs to any secondary groups, the user will be removed from those groups if the groups are not in the list.
    * **-aG** assigns a user to a secondary group (or groups) by appending them to any groups the user already belongs to. Follow the command with a comma-separated list of groups.
    * **-G ""** removes the user from all secondary group memberships.
* groups
  * Display the primary and secondary group membership for the specified user account.
  * Example:
    * **groups pmaxwell** displays group membership for the pmaxwell account.