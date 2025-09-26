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

> Is recommended to have a terminal with root access opened while modifying files related to authentication in case something go wrong.

### Enable password history

Edit the file: /etc/pam.d/common-password

This lines prevent users to reuse the last 99 password.

    password    required    pam_pwhistory.so
    remember=99 use_authok

## Configuring administrator access with sudo

Users can have sudo access by being added to the sudo group. They are able to do everything that root user can do unless
they became limited.

The /etc/sudoers file contains the configuration wich governs sudo access.

It is recommender editing this file with visudo command. This will help you to check the syntax and prevents destroying the file.

    visudo /etc/sudoers

To change the default editor(nano) for using visudo, vim in this case:

    Editor=vim visudo

> Some distributions require you to install sudo manually. Sudo group name could be different too.

The next line is the configuration that enables sudo access to anyone who is a member of the sudo group. The group name can be changed but make sure to create that group and add you before make this.

    %sudo ALL=(ALL:ALL) ALL

The next line enables sudo access to an specific user:

    root ALL=(ALL:ALL) ALL

- The first ALL means that root is able to use sudo from any machine.
- The second one means that root can use sudo to impersonate any other user -u.
- The third one means that root can impersonate any other group -g.
- The last one refers to what commands this user is able to do.

        <user/%group> host_machine=(RunAsUser:RunAsGroup) commands

Example:

    alex Desktop-001=(luis:ALL) /usr/sbin/shutdown,<More commands>

User alex can use sudo from Desktop-001 and is able to execute shutdown command only from the system binaries. Is able to impersonate all groups and impersonate luis user only.