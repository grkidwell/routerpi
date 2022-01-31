## IPtables
    sudo DEBIAN_FRONTEND=noninteractive apt install -y netfilter-persistent iptables-persistent

    sudo iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE
    sudo netfilter-persistent save
    sudo nano /etc/sysctl.conf
#
```
net.ipv4.ip_forward=1
```