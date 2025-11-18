# Setting the hostname

Often, hostnames have naming conventions managed by organizations. But we can choose whatever we want when there are no restrictions.

The hostname identifies our server to the rest of the newtwork. Each server must have a unique and descriptive name.

View hostname:

    hostname


Change hostname command:

    # Modifies /etc/hostname

    hostnamectl set-hostname my.hostname.org

You need to modify the hosts file too:
    
    nano /etc/hosts
    
    127.0.1.1 my.hostname.org

