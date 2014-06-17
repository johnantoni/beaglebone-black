## edit interfaces

    sudo nano /etc/network/interfaces

## disable dhcp

    # disable dhcp
    # iface eth0 inet dhcp

## set static ip

    auto eth0
    iface eth0 inet static
    address 10.0.1.90
    gateway 10.0.1.1
    netmask 255.255.255.0
    network 10.0.1.0
    broadcast 10.0.1.255
    
## restart network

    sudo /etc/init.d/networking restart
    sudo /etc/init.d/networking reload
