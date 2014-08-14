#### install latest node for ARM

##### doesn't work

https://learn.adafruit.com/raspberry-pi-hosting-node-red/setting-up-node-dot-js

    sudo wget http://node-arm.herokuapp.com/node_latest_armhf.deb
    sudo dpkg -i node_latest_armhf.deb
    node -v
    => v0.10.29
    curl -L https://npmjs.org/install.sh | sudo sh
    npm -v
    => 1.4.23

##### does

...this would work but there's problems with identifying the processor under ARM, so best to install a pre-built package

https://github.com/joyent/node/wiki/installing-node.js-via-package-manager

    sudo su
    apt-get install curl lsb-release
    curl -sL https://deb.nodesource.com/setup | bash -
    apt-get install nodejs nodejs-legacy npm
