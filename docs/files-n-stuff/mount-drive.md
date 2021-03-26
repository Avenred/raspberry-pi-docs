# How to mount an external HDD on your Raspberry Pi
To mount your external hard drive, first plug in the hard drive into your Raspberry Pi. Then type `sudo lsblk -o UUID,NAME,FSTYPE,SIZE,MOUNTPOINT,LABEL,MODEL` into the terminal. You'll see something like this:

```
UUID                                 NAME        FSTYPE   SIZE MOUNTPOINT         LABEL    MODEL
                                     sda                  7.3T                             ST8000DM004-2CX188
                                     ├─sda1               128M                             
267D-CA2F                            └─sda2      exfat    7.3T /media/pi/SG Drive SG Drive
                                     sdb                596.2G                             ST9640320AS
7AA3-BE64                            └─sdb1      exfat  596.2G                    Media    
                                     mmcblk0             29.7G                             
6284-658D                            ├─mmcblk0p1 vfat     256M /boot              boot     
3a324232-335f-4617-84c3-d4889840dc93 └─mmcblk0p2 ext4    29.5G /                  rootfs
```

Look at the `SIZE` column, and look for the size that matches your external hard drive, then look at the correlating name on the left.
In this example, we will use sda2, since it matches the size of our external hard drive (which is 8TB or 7.3TiB).

Next we'll need to identify the file system of the external hard drive. On the same row as your external drive, look for the `FSTYPE`.
If you see `exfat` as your `FSTYPE` (file system), you will need to install the exFAT driver.

```
sudo apt update
sudo apt install exfat-fuse
```
If you see `ntfs` as your `FSTYPE` (file system), you will need to install the NTFS driver.

```
sudo apt update
sudo apt install ntfs-3g
```

Next, we'll need to find where the disk partition is, to do this, type `sudo blkid` into the terminal. You should see something like this:

```
/dev/mmcblk0p1: LABEL_FATBOOT="boot" LABEL="boot" UUID="6284-658D" TYPE="vfat" PARTUUID="20b72c34-01"
/dev/mmcblk0p2: LABEL="rootfs" UUID="3a324232-335f-4617-84c3-d4889840dc93" TYPE="ext4" PARTUUID="20b72c34-02"
/dev/mmcblk0: PTUUID="20b72c34" PTTYPE="dos"
/dev/sdb1: LABEL="Media" UUID="7AA3-BE64" TYPE="exfat" PARTLABEL="Basic data partition" PARTUUID="0af000e6-66a8-4497-aedc-a51a07e42f64"
/dev/sda1: PARTLABEL="Microsoft reserved partition" PARTUUID="390edc39-98b5-4330-8c18-884ba8d964bc"
/dev/sda2: LABEL="SG Drive" UUID="267D-CA2F" TYPE="exfat" PTTYPE="atari" PARTLABEL="Basic data partition" PARTUUID="4b0334e4-4e27-4c7d-8d77-44d7174cc2f7"
```

We have already identified that the external hard drive we wish to use is the one with the label "SG Drive". If you do not know the label your external hard drive, see the above section on identifying your external hard drive and pay attention to the `LABEL` column.

Next, look for the part all the way on the left, you should see something similar to `dev/sda1` or `dev/sda2`. This is the location of your external hard drive.

Now we'll create a location for the external hard drive to be mounted. This is the "folder" that your external hard drive will live in. You can mount your HDD to the /mnt folder or to the /media/pi folder. In this example, we'll mount the HDD to the /mnt folder.

`sudo mkdir /mnt/myhdd`

You may wish to replace `myhdd` with a different name so it's easier to identify.

After the mount location/folder has been created, we'll mount the drive.

`sudo mount /dev/sda2 /mnt/myhdd`

To very that the drive has mounted successfully, view the files:

`ls /mnt/myhdd`

And you're done! Your external hard drive is now successfully mounted.
