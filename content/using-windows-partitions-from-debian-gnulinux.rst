Using Windows partitions from Debian GNU/Linux
##############################################
:date: 2007-04-05 03:23
:author: admin
:category: Linux, technology
:slug: using-windows-partitions-from-debian-gnulinux

My friend `Arun <http://digitalpbk.blogspot.com/>`__ recently blogged
about `Automounting filesystems in
Linux <http://digitalpbk.blogspot.com/2007/03/auto-mounting-file-systems-in-linux.html>`__
from a
`Fedora <http://en.wikipedia.org/wiki/Fedora_%28Linux_distribution%29>`__
perspective. For those of you who want an alternative method (especially
`Debian <http://en.wikipedia.org/wiki/Debian>`__ users), here goes...

I'll explain how I did it - it's much easier to understand from an
example.

First of all, I used fdisk so I could know which were all the partitions
in my system and what they were called.

    debian-indraprastha:/home/anirudh# fdisk -l

    | Disk /dev/sda: 40.0 GB, 40060403712 bytes
    |  255 heads, 63 sectors/track, 4870 cylinders
    |  Units = cylinders of 16065 \* 512 = 8225280 bytes

    | Device Boot Start End Blocks Id System
    |  /dev/sda1 \* 1 1912 15358108+ c W95 FAT32 (LBA)
    |  /dev/sda2 1913 3960 16450560 f W95 Ext'd (LBA)
    |  /dev/sda3 3961 4870 7309575 83 Linux
    |  /dev/sda5 1913 3187 10241406 b W95 FAT32
    |  /dev/sda6 3917 3960 353398+ 82 Linux swap / Solaris
    |  /dev/sda7 3188 3916 5855661 83 Linux

Now take the first entry. That partition is called /dev/sda1 and is the
C: drive on Windows. Now I use the mount command to mount the partition.
Mounting means that I attach a physical device to a directory, so that
the directory itself becomes the device. It's a concept that you get
used to once you are familiar with all this. To mount the partition, I
need a mount point. This is any directory that I create.

    debian-indraprastha:/home/anirudh# mkdir /disks/c

Now I mount /dev/sda1 to /disks/c

    debian-indraprastha:/home/anirudh# mount /dev/sda1 /disks/c

You can check if it has been mounted using the df command.

    | debian-indraprastha:/home/anirudh# df -h
    |  Filesystem Size Used Avail Use% Mounted on
    |  /dev/sda3 6.9G 4.7G 1.9G 71% /
    |  tmpfs 253M 0 253M 0% /dev/shm
    |  /dev/sda5 9.8G 7.9G 1.9G 81% /disks/d
    |  /dev/sda7 5.5G 4.6G 702M 87% /disks/s7
    |  tmpfs 10M 716K 9.4M 7% /dev
    |  /dev/sda1 15G 13G 2.4G 84% /disks/c

See the last entry? That shows that /dev/sda1 (the C: drive) has been
mounted on /disks/c. Its total size is 15 GB of which 84%(13GB) has been
used and 2.4GB is available.

Now there's a file called /etc/fstab that comes in very handy. This
mounting business is temporary. It gets "unmounted" after I shutdown. I
would like to automatically mount it each time. I do that by modifying
the /etc/fstab file. The /etc/fstab file keeps static information about
the filesystems(refer $man fstab). Another file that comes in handy is
/etc/mtab. This file keeps info about all the devices that have been
mounted. After I mount /dev/sda1, an entry is made in /etc/mtab
automatically.

    /dev/sda1 /disks/c vfat rw 0 0

Now I copy this line into my /etc/fstab, with some modifications.

    /dev/sda1 /disks/c vfat auto,exec,rw 0 0

Now each time the system boots, that drive will be mounted
automatically.

Now, suppose I don't want it to be mounted now? I use unmount.

    debian-indraprastha:/home/anirudh# umount /dev/sda1

To disable the mounting of the paritition automatically, just remove
that particular entry from /etc/fstab or uncomment it.

Have fun :-)
