# Wireguard
## &nbsp;

## Install wireguard
digital ocean server
#
    geddy@tnfs_digocean:~$ sudo apt install wireguard

tnfspi
#
    pi@routerpi~$ sudo apt install wireguard


## Generate key-pairs
digital ocean server
#
    geddy@tnfs_digocean:~$ wg genkey |sudo tee private.key
    geddy@tnfs_digocean:~$ cat private.key|wg pubkey|sudo tee public.key

routerpi
#
    pi@routerpi:~$ wg genkey |sudo tee private.key
    pi@routerpi:~$ cat private.key|wg pubkey|sudo tee public.key

## Create wireguard config files
digital ocean server
#
    geddy@digocean:~$ sudo nano /etc/wireguard/wg0.conf

    [interface]
    PrivateKey = <digocean private key>
    Address = 10.14.0.1/24
    ListenPort=51820

    PostUp   = iptables -A FORWARD -i %i -j ACCEPT; iptables -A FORWARD -o %i -j ACCEPT; iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE
    PostDown = iptables -D FORWARD -i %i -j ACCEPT; iptables -D FORWARD -o %i -j ACCEPT; iptables -t nat -D POSTROUTING -o eth0 -j MASQUERADE

    #tnfspi
    [Peer]
    Publickey= <routerpi public key>
    AllowedIPs=10.14.0.9/32

routerpi
#
    pi@routerpi:~$ sudo nano /etc/wireguard/wg0.conf

    [Interface]
    Privatekey = <routerpi privatekey>
    Address = 10.14.0.9/24

    [Peer]
    Publickey = <digocean private key>
    Endpoint = <digocean status ip address>:51820
    AllowedIPs = 10.14.0.0/24

    PersistentKeepalive = 25

## Enable port forwarding
digital ocean server
#
    geddy@digocean:~$ sudo nano /etc/sysctl.conf

    net.ipv4.ip_forward=1

    geddy@digocean:~$ sudo sysctl -p /etc/sysctl.conf   # restart service
    geddy@digocean:~$ sysctl net.ipv4.ip_forward        # verifies ip forwarding is enabled. should return net.ipv4.ip_foward=1

routerpi
#
    pi@routerpi:~$ sudo nano /etc/sysctl.conf

    net.ipv4.ip_forward=1

    pi@routerpi:~$ sudo sysctl -p /etc/sysctl.conf   # restart service
    pi@routerpi:~$ sysctl net.ipv4.ip_forward        # verifies ip forwarding is enabled. should return net.ipv4.ip_foward=1

## Open server port 51820
    geddy@digocean:~$ sudo ufw allow 51820

## Start Wireguard
digital ocean server
#
    geddy@digocean:~$ sudo systemctl start wg-quick@wg0.service
    geddy@digocean:~$ sudo systemctl enable wg-quick@wg0.service

routerpi
#
    pi@routerpi:~$ sudo systemctl start wg-quick@wg0.service
    pi@routerpi:~$ sudo systemctl enable wg-quick@wg0.service

## Login to server from client
    pi@routerpi:~$ ssh -i .ssh/dopriveatesshkeyfile geddy@10.14.1.1
    geddy@digocean:~$
## Login to client from server
    geddy@digocean:~$ ssh pi@10.14.1.2
    pi@routerpi:~$ 