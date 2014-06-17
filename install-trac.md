### install

    sudo apt-get install sqlite3
    sudo apt-get install python
    wget https://bootstrap.pypa.io/ez_setup.py -O - | sudo python
    sudo easy_install Genshi
    sudo easy_install Trac==1.0

### configuration

* http://trac.edgewall.org/wiki/TracIni

    trac.ini located in <projectenv>/conf/trac.ini

#### nginx setup

* http://trac.edgewall.org/wiki/TracNginxRecipe
* http://serverfault.com/questions/197482/tracd-multiple-projectsnginx-reverse-proxy
* http://metz.gehn.net/2013/02/running-anything-on-nginx-with-uwsgi/

### plugins

* http://trac-hacks.org

#### enable git support

* http://trac.edgewall.org/wiki/TracGit

enable git support in trac.ini

    [components]
    tracopt.versioncontrol.git.* = enabled

#### spam filter

* http://trac.edgewall.org/wiki/SpamFilter

    sudo easy_install TracSpamFilter

add to trac.ini to throttle posts per hour

    [spam-filter]
    max_posts_by_ip = 5

#### account manager

* http://trac-hacks.org/wiki/AccountManagerPlugin

    sudo easy_install https://trac-hacks.org/svn/accountmanagerplugin/tags/acct_mgr-0.4.4
