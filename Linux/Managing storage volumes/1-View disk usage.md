# viewing disk usage

Use the next command to perform that task. List all the mounted volumes to see how much space is left on each.

    df -h

## Inodes

Inodes contain information about the actual items stored. There is a limit that you can use. Even if there is space left on the volume, if you reach the inode limit, the system will tell you that there is  not enough space left.

    df -hi

## Scanning directories space

Use du to scanning directories to see how much space are being used.

    du -hcs <directory/ies>

## Ncurses Disk usage Utility(ncdu)

This is an specialized and interactive tool to navigate through the directory tree.

Install

    apt install ncdu

Execute (-x on the current filesystem only).

    ncdu -x <directory>