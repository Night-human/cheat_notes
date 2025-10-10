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

## Mounting and unmounting storage volumes

There are two directories to mount volumes by default. Both of them are suggestions that the FHS recommends, but you can mount the storage in any empty directory.

- \/mnt  
for temporary volumes as network attached storage, additional hard drives, virtual hard disks, etc. 

- /media  
    for removable devices as external hard drives, flash drives, CD-ROM, etc.

Mount command

    mount <hard drive path> <mount path>

Unmount command

    umount <mount path
   
> Note: Keep an eye over disk path before and after partitioning. Labels tends to change.

## /etc/fstab file

This file is used to define which volumes will be automatically mounted at boot time, even system volumes.

Output example from / partition line:

    UUID=1eb7b086-d119-4263-8def-53c83a7333bf  /  ext4 defaults 0 1

column 1: UUID  
column 2: mount point  
column 3: type  
column 4: options  

defaults

- rw: Device will be mounted read/write
- exec: Allow files within this volume to be executed as programs
- auto: Automatically mount the device at boot time
- nouser: Only root is able to mount the filesystem
- async: Output to the device should be asynchronous

column 5: dump  
column 6: pass  

UUID of the volumes can be found by executing:

    sudo blkid

> Note: fstab is not ideal for Removable devices or dynamic mounts.

Mount devices set with auto.

    mount -a

Mount devices set with noauto.

    mount <mount path only>

## Managing swap

Adding swap to the fstab file will not mount it automatically with the previous command: mount -a.
We do it this way:

    swapon -a

The flow is simple, first find, then mount and finally activate it. If you want the opposite action enter the next command.

    swapoff -a

To check the free memory available, use this:

    free -m

### Create swap file

There are few ways to create swap memory, one of them is by creating a swapfile. Then prepare it to be used as swap.

    #Create swap file
    fallocate -l 4G /swapfile

    #Prepare
    mkswap /swapfile

Finally add it to fstab file and execute the swapon -a command.

> Remember to unmount swap memory before.

### Create swap from disk or virtual memory

Execute

    fdisk </dev/disk>

- Select n for new partition
- Select p for primary partition
- Give it the space you need
- Select t for type of partition
- Select w to save

Prepare the swap partition:

    mkswap </dev/swap partition>

Finally add it to the fstab and then use swapon -a.