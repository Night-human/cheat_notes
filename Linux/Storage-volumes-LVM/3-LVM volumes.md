# LVM volumes

With LVM, we are able to resize the filesystem without reboot our system. 

Is recommended to use LVM on storage volumes in virtual servers whenever possible.

## Volume groups

A volume group is a namespace given to all physical and logical volumes in the system. It is like a container.

We can have several volume groups. Each one with their own physical and logical volumes.


### Physical volume

A physical volume is a physical or virtual hard disk that is a member of a volume group.

### Logical volumes

A logical volume is similar in concept to partitions. A logical volume can take up a portion of, or an entire, disk. Additionally, they may span multiple disk, that means you can add storage space from different disks to obtain a single one.

## Set up volumes

### Set up physical volumes

Install lvm2

    apt get install lvm2

Create a physical volume

    pvcreate <disk path>

Display PV information

    pvdisplay

### Create Volume group

Create a VG, give it a name and assign it a PV

    vgcreate <vg-name> <disk path>

Display VG information

    vgdisplay


### Create a Logical volume

Create a logical volume and assign it to a VG

    lvcreate -n <lv-name> -L 2g <vg-name>

Display LV information

    lvdisplay

### Find the name for our LV

    ls /dev/mapper

## Formatting and mounting

    mkfs.ext4 /dev/mapper/<GV found above>

    mount /dev/mapper/<GV> <mount path>

## Extend space

First

    lvextend -n /dev/mapper/<GV> -l 100%FREE -r

    or

    lvextend -L+10g <GV-path> -r
    lvextend -L 10g <GV-path> -r

Then(only if the flag -r is ommited above)

    resize2fs /dev/mapper/<VG>

> This command will take all the free space from the multiple PVs assigned to the VG.

## Extend Volume Groups

Make sure to have PV disk ready.

    vgextend <vg-name> <disk-path>


## Delete Logical, Physical and volume Groups

    vgremove <vg-path>

    lvremove <lv-path>

    pvremove <pv-path>

> This action may wipe your data


## Create Snapshot

Snapshots are useful when we have to make changes in our original files. If we make a mistake, we can easily recover the original state of our data from an snapshot.

> Mount the snapshot is not needed.

###  Creating snapshots

We need an lv as a target volume to copy their current state to the snapshot volume.

    lvcreate -s -n snapshot -L 500m <lv-path>

### Recover our original state

We need to unmount the original volume first. Then use:

    lvconvert --merge <snapshot-path>

If you make a mistake and tried to merge the snapshot with the original volume mounted yet, try this:

    lvchange --refresh <VG-name>

> This action will erase our snapshot volume.

### Recover data manually

Do this by mounting de snapshot and copy the files you want to recover their original state.