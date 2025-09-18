# Password management

Password Management notes and commands. Execute man command or --help to get more usege information.

    man groups
    passwd --help

 ## Lock an account

    passwd -l <user>

## Unlock an account

    passwd -u <user>

> Note: Locked users will be able to login over SSH. Remove them from SSH group is one way to solve the problem.

## See password information

    chage -l <user>

## Force users to change their passwords after the first login. 

Expiration days left 0 in this example.

    chage -d 0 <user>

## Setting up account expiration

Users require a password change after a maximum number of days

    chage -M 90 <user>

Users require a password change after a minimum number of days

    chage -m 80 <user>


> Users will not be able to change their passwords before the minimum number of days has passed.

## Setting up password policies

First, install the Pluggable Authentication Module(PAM).

    apt-get install libpam-cracklib

