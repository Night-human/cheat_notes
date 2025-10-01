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

## Partitioning and formatting volumes

Executing the next command will prompt a warning alert, but make sure to unmount the disk first. Press m to display the menu.

	fdisk <path to the disk>

> Note: the path to the hardware is /dev/ in all distributions.

- Choose the partition type(MBR or GPT).
- Press n to create a new partition .
- Select the default partition label.
- Choose the initial sector of the partition(always use the default 2048 for the first partition).
- Choose the final sector of the partition -1. Use G, M or K if you are not working with sectors.
- Press w to save.

> Note: Initial and final sectors are inclusive. Is recommended to use G, M or K instead.

Once everything is set up, execute the mkfs command followed with the partition format and the partition path.

Example:

New partition format: ext4  
Disk: /dev/sdz  
New partition label: /dev/sdz1  

    mkfs.ext4 /dev/sdz1

