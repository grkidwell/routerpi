## Systemd-Networkd
    cd /etc/systemd/network
    sudo nano br0.netdev
#
```
[NetDev]
Name=br0
Kind=bridge

```
#
    sudo nano br0.network
#
```
[Match]
Name=eth1


[Network]
Bridge=br0
```
#
    sudo systemctl enable systemd-networkd