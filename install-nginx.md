make sure apache is removed

    sudo apt-get remove apache2
    
# install nginx latest

    wget http://nginx.org/download/nginx-1.6.0.tar.gz
    tar -xzvf nginx-1.6.0.tar.gz
    cd nginx*
    ./configure
    make
    sudo make install
    sudo reboot
    sudo service nginx start

installs to /usr/local/nginx


