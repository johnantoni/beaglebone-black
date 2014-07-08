#### install

    sudo apt-get remove git-core git
    sudo apt-get install libcurl4-gnutls-dev libexpat1-dev gettext libz-dev libssl-dev build-essential
    sudo apt-get install unzip
    wget https://github.com/git/git/archive/v2.0.0.zip
    unzip v2.0.0.zip
    cd v2.0.0
    make prefix=/usr/local all
    sudo make prefix=/usr/local install

Last two commands make it global.

#### check

Now logout and login as a normal user and do

    git --version
    ==> git version 2.0.0

