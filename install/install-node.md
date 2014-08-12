#### install latest node for ARM

https://learn.adafruit.com/raspberry-pi-hosting-node-red/setting-up-node-dot-js

    sudo wget http://node-arm.herokuapp.com/node_latest_armhf.deb
    sudo dpkg -i node_latest_armhf.deb
    node -v
    => v0.10.29
    curl -L https://npmjs.org/install.sh | sudo sh
    npm -v
    => 1.4.23
