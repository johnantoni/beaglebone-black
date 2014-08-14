#### install latest node for ARM

first enable backports

    sudo su
    vim /etc/apt/sources.list
    ...then enable backports
    
    apt-get update
    apt-get install nodejs
    nodejs --version
    => 0.10.29
    
now you'll have nodejs installed, but it will be installed as nodejs, not node as there's a package conflict with node

so you'll have to make a symlink to node in order to install npm

http://stackoverflow.com/questions/18130164/nodejs-vs-node-on-ubuntu-12-04

    sudo ln -s /usr/bin/nodejs /usr/bin/node
    curl http://npmjs.org/install.sh | sh
    npm --version
    => 1.4.23

then if your building packages for say ghost, run

    cd ghost
    sudo npm install --production
