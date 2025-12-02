# Linux name resolution

DNS matches human-understandable domain names to IP address.

Get information about the order in which ubuntu server checks resourses to resolve names:

    //Look for the line 'hosts'
    cat nsswitch.conf | grep hosts

Output:

    hosts:  files dns

The server is configured to first check the local files, then DNS if the request is not found.

## Install openssh

OpenSSH let's you connect to remote linux servers using your termina.

Install OpenSSH in the server:

    apt install openssh-server

Install OpenSSH client:

    apt install openssh-client

Basic connection command:

    ssh user@host -p 22

## SSH security

You can stablish the connection using a password but this not the best approach because you were trasmiting your password over the network.

Use Public Key Authentication instead and disable password authentication.

When you create an SSH key-pair, two files are being generated: a Public key and a Private key, mathematically linked.

## Generate key:

Generate your keys in your own personal machine(not servers if it is not required). You will be asked for a passphrase, optional but more secure.

> Keys will be under /home/\<username>/.ssh

    ssh-keygen

Private key never should leave the machine where it was generated or your keys can no longer be thrusted. They are only valid for the user who created it.

Once created, copy the public key to the server you want to connect over ssh:

    ssh-copy-id -i <your pulic key.pub> -p <port> username@host

Then try to log in to the server over ssh normally. If you have configured a passphrase, you will be asked for it.
