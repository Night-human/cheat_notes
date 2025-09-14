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