# Setting permissions on files and directories

Permissions notes and commands. Execute man command or --help to get more usege information.

    man chmod
    chmod --help

    man chown
    chown --help

## Resources information

There is useful information when you list resources:

    ls -l
    //output
    drwxr-xr-x 2 night night 4096 Sep 26 18:17 Documents
    -rw-r--r-- 1 night night    0 Sep 26 18:16 welcome.txt

column 1: premission string  
column 2: link count for the resource  
column 3: the owner of the resouce  
column 4: the group that owns the resource  
column 5: the size in bytes  
column 6: the last date the file was modified  
column 7: the name of the file  

Type of Permissions

- r -> read file | view content of directory
- w -> write file | content altered of directory
- x -> execute file | cd inside directory

Type of resources:

- d for document
- \- for file
- l for Link

| type | User  | Group  | World |
|---|---|---|---|
| d | rwx | r-x | r-x |
| - | rw- | r--  | r-- |

## Modify permissions

There are few ways to modify permissions. One of them is as follows:

### First way

Removes the read and write permissions from the current user.

    chmod u-rw <file path>

Adds the read and execute permissions for the group.

    chmod g+rx <file path>

### Second way

You can add the permissions, each number is for user, group, other.

- r = 4
- w = 2
- x = 1

In this example, the directory applies recursive permissions. User has all of them, group is able to read only and, finally, other users have the write and execute permissions.

    chmod 743 -R <path>

You can find and apply permissions this way:

    find /path/to/dir/ -type f -exec chmod 644 {} \;

## Change ownership

Change user owner recursively over directories and their files.

    chown -R <user> <file>

Change the group with the following syntax.

    chown <user>:<group> <file>
    or
    chgrp <group> <file>