# Groups management

Groups Management notes and commands. Execute man command or --help to get more usege information.

    man groups
    groups --help

## See to which groups belongs a user

This line without a username tells you which groups your current logged in user belongs.

    groups <user>

## Groups tracking file: /etc/group

There is an important file where groups information is stored, the /etc/group.

group file content example

    docker:x:999:night
    alex:x:1001:

column 1: The name of the group  
column 2: Password of the group (if any)  
column 3: GID or Group Id  
column 4: Actual members of the group  

## Add a group command

    groupadd <group>

## Delete a group command

    groupdel <group>

## Add a user to a group

This command appends a user to a group.

    usermod -aG <group> <user>

or

    gpasswd -a <user> <group>

The flags "-aG" append a new group to the complementary group list.

> alex : alex complementary complementary2

The flag "-G" overwrites the complementary groups list.

> alex : alex new_complementary_group

The flag "-g" modifies the primary group only.

> alex : new_primary_group complementary complementary2

## Remove user from a group

    gpasswd -d <user> <group>