# Managing network interfaces

## Show IP

Show IP address:

    ip addr show

In older systems:

    ifconfig


## Managing the state of an interface

    ip link set <interface-name> <down|up>

In older systems:

    ifconfig <interface-name> <up|down>

## Network names overview

In older versions of ubuntu server, there is a directory called udev for managing network interface names. Persisten net rules file makes sure that your network interface names always be the same.

/etc/udev/rules.d/70-persisten-net-rules

en: Ethernet  

wl: Wireless  

enp0s3: Wired card(ethernet). The 'p' references which bus is used, so p0 refers to the system's first bus. s3 means placed in PCI slot 3.





