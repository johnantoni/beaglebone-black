### iso to usb stick instructions

    diskutil list
    diskutil unmountDisk /dev/diskN
    sudo dd if=/path/to/downloaded.iso of=/dev/rdiskN bs=1m
    diskutil eject /dev/diskN
    
