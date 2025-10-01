# Adding additional storage volumes

We need to determine the name of the device, format it, and mount it.

When a new disk is attached to our server, the system will give it a name. in most cases /dev/sda, /dev/sdb, and so on. If there is a number at the end, it refers to the number of the partition: /dev/sda1.

In other cases, such as virtual disks, this will be diferent, such as /dev/vda, /dev/xda, and others.

The fdisk command is used for creating and deleting partitions, but it will allow us to determine which device name our new disk received\

Disk information

    fdisk -l

or

    lsblk

key questions before expand disk space:

- How much space do I need?
- What is the name of the new attached disk?
- How do I want it formatted? (Ext 4 most common)
- Where do I want it mounted?