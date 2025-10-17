## LVM volumes

With LVM, we are able to resize the filesystem without reboot our system. 

Is recommended to use LVM on storage volumes in virtual servers whenever possible.

### Volume groups

A volume group is a namespace given to all physical and logical volumes in the system. It is like a container.

We can have several volume groups. Each one with their own physical and logical volumes.


### Physical volume

A physical volume is a physical or virtual hard disk that is a member of a volume group.

### Logical volumes

A logical volume is similar in concept to partitions. A logical volume can take up a portion of, or an entire, disk. Additionally, they may span multiple disk, that means you can add storage space from different disks to obtain a single one.

