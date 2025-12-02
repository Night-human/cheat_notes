# Assigning static IP Addresses

There are two ways of assigning a fixed addess to a network host, including servers.

> Static IP assignement

Grab an IP address and then configure the server with to use that address.

> Static Lease | DHCP Reservation

Configure the DHCP server to assign a specific IP address to specific host when they ask for one.

## Static assignment

### In older ubuntu servers(<18.04)

Edit the file under /etc/network directory:

    /etc/network/interfaces

    ### Output example

    auto enp0s3
    iface enp0s3 inet static
        address 10.10.96.1
        netmask 255.255.252.0
        broadcast 10.10.96.255
        dns-search local.lan
        dns-nameservers 10.10.96.1

Then restart the network service:

    sudo systemctl restart networking.service

In ubuntu servers before systemd:

    /etc/init.d/networking restart



### In newer ubuntu servers

Edit the file under /etc/netplan directory:

    /etc/netplan/00-installer-config.yaml

    ### Output example

    network:
    ethernets:
        enp0s3:
        dhcp4: false
        addresses:
            - 192.168.1.98/24
        routes: 
            - to: default
            via: 192.168.1.1
        nameservers:
            addresses: [8.8.8.8, 8.8.4.4]
        dhcp6: true
        match:
            macaddress: 08:00:27:5e:15:3e

Then apply:

    sudo netplan apply

## Install tmux

Tmux keeps your session alive after lossing the ssh connection or after being droped. Useful when we are working with remote servers.

    sudo apt install tmux
