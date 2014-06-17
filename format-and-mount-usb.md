## howto

#### 1. find

    sudo find -l

#### 2. create mount point

    mkdir -p /home/usb
    
-p means make parent dir if hot existing.

#### 3. unmount

    sudo umount /dev/sda1

#### 4. format usb stick as ext4

    sudo mkfs.ext4 /dev/sda1

#### 5. add mount position to fstab so it properly mounts on boot

    sudo vim /etc/fstab

then add

    /dev/sda1 /home/usb ext4 rw,async,user,nofail 0 0

'nofail' means if the drive fails to boot, or simply isn't plugged in, it won't bring down the system.

#### 6. reboot

    sudo reboot
    
when it reboots login and run

    df -h
    
you should see /dev/sda1 has properly mounted to /home/git

## extra

### fdisk

    ..list drives
    sudo fdisk -l
    ..
    ..create partition for /dev/sda
    sudo fdisk /dev/sda

* p = list partitions
* d = delete partitions
* n = create partitions
* w = write partition changes

...create primary partition

### format

    ..format /dev/sda1 partition as ext4
    sudo mkfs.ext4 /dev/sda1

### mount

    sudo mkdir /media/storage
    sudo nano /etc/fstab
    ..add
    /dev/sda1 /media/storage ext4 rw,async,user,nofail 0 0
    
* nofail = don't stop boot even if the drive is disconnected

do **df -h** to make sure the drive has mounted correctly
