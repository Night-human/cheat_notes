# User management

User Management notes and commands. Execute man command or --help to get more usege information.

    man useradd
    useradd --help

## Add a user basic command

This line adds a new user called night, create and assignes it a directory.

    useradd -d /home/<user> -m <user>

## Delete a user

Deletes a user and home directory(-r)

    userdel <user> -r

## Set a user password

Prompt new user password input

    passwd <user>

## Change a user directory

Moves all user files from old directory to the new one.

    usermod -d /home/<new_directory> <user> -m

## Update username

    usermod -l <new_user> <user>


## User tracking files: /etc/passwd and /etc/shadow

There are two important files where user account information is stored, the /etc/passwd and /etc/shadow.

### Passwd file content example

    night:x:1000:1000:Night,,,:/home/night:/bin/bash

column 1: username  
column 2: x refers that the users password is encrypted and stored in /etc/shadow file.  
column 3: UID or User ID  
column 4: GID or Group ID  
column 5: User information such last name, age, etc  
column 6: Directory  
column 7: Command line, shell designated to the user. If an invalid shell is entered, users would not be able to logging in.

### Shadow file content example

    night:$y$j9T$WeoATU5PsXJvTVOvgtgbuk55:20187:0:99999:7:::

column 1: username  
column 2: Hash for the user password or !  
column 3: Number of days since the last password change  
column 4: Number of days required to pass before the user will be able to change their password  
column 5: the maximum nomber of days that can pass between password changes  
column 6: Numbers of days that will elapse before warn the user that is required to change their password  
column 7: Number of days that can pass after the password expires and the account will be disabled  
column 8: Number of days since the UNIX Epoch that 
will elapse before the account is disabled  

> Note: root account has an ! in the second column. That means this account is locked to logging in directly. You need to login from another account first, then switch to the root account.

## Default configuration files /etc/skel(skeleton)

Files are copied into the home directory of the created users. It provides recomended configuration and you can add more if requiered, they will be copied too.  

## Switching between users

Set the root user password(Not recommended)

    sudo passwd

Switch to root user

    sudo su

Switch to another user

    su <user>

Switch without a user password

    sudo su <user>

