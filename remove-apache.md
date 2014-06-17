uninstall

    sudo apt-get remove apache2*
    sudo reboot
    
testing port 80

    sudo netstat -nltup | grep :80
    ...gets
    tcp6       0      0 :::80                   :::*                    LISTEN      1/systemd
    
