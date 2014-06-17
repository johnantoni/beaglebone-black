#### init

    cd /home/trac
    mkdir git
    mkdir app
    chown -R debian /home/trac

#### create

    trac-admin /home/trac/app/bookmark initenv

will create ini in => **/home/trac/app/bookmark/conf/trac.ini**

#### test-drive

    tracd --port 8000 /home/trac/app/bookmark

if running thru a firewall make sure port 8000 is mapped to your beaglebone box

#### add user

    htpasswd -c /home/trac/app/bookmark/.htpasswd admin
    trac-admin /home/trac/app/bookmark permission add admin TRAC_ADMIN    
