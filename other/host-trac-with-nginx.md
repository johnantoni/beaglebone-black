#### fix permissions

    sudo chown -R www-data: /home/trac

#### configure nginx

Edit **/usr/local/nginx/conf/nginx.conf**

    server {
      listen 80;
      proxy_pass http://localhost:10001/;
      auth_basic "Dev";
      auth_basic_user_file htpasswd;
      proxy_pass_header Authorization;
    }

Create a new init.d script: /etc/init.d/tracd

    #! /bin/sh
    ### BEGIN INIT INFO
    # Provides:          tracd
    # Required-Start:    $all
    # Required-Stop:     $all
    # Default-Start:     2 3 4 5
    # Default-Stop:      0 1 6
    # Short-Description: starts the tracd web server
    # Description:       starts tracd using start-stop-daemon
    ### END INIT INFO
     
    PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin
    DAEMON=/usr/bin/tracd
    NAME=tracd
    DESC=tracd
    DAEMON_OPTS="-p 10001 --protocol=http -e /var/trac --basic-auth *,/etc/nginx/htpasswd,Dev"
     
    test -x $DAEMON || exit 0
     
    # Include tracd defaults if available
    if [ -f /etc/default/tracd ] ; then
            . /etc/default/tracd
    fi
     
    set -e
     
    case "$1" in
      start)
            echo -n "Starting $DESC: "
            start-stop-daemon --start --quiet --pidfile /var/run/$NAME.pid \
                    --chuid www-data --background --make-pidfile \
                    --exec $DAEMON -- $DAEMON_OPTS
            echo "$NAME."
            ;;
      stop)
            echo -n "Stopping $DESC: "
            start-stop-daemon --stop --quiet --pidfile /var/run/$NAME.pid
            echo "$NAME."
            ;;
      restart|force-reload)
            echo -n "Restarting $DESC: "
            start-stop-daemon --stop --quiet --pidfile /var/run/$NAME.pid
            sleep 1
            start-stop-daemon --start --quiet --pidfile /var/run/$NAME.pid \
                    --chuid www-data --background --make-pidfile \
                    --exec $DAEMON -- $DAEMON_OPTS
            echo "$NAME."
            ;;
      *)
            N=/etc/init.d/$NAME
            echo "Usage: $N {start|stop|restart|reload|force-reload}" >&2
            exit 1
            ;;
    esac
    
    exit 0

enable and start

    sudo chmod +x /etc/init.d/tracd
    sudo /usr/sbin/update-rc.d -f tracd defaults

remove with

    sudo /usr/sbin/update-rc.d -f tracd remove

start & status

    sudo service nginx start
    sudo service nginx status

#### nginx: [emerg] bind() to 0.0.0.0:80 failed (98: Address already in use)

temporarily kill whatever's grabbing port 80

    sudo fuser -k 80/tcp


http://sammyjenkis.com:443/bookmark/wiki/TracFastCgi
