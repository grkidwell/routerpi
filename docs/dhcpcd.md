## DHCPCD
    sudo nano /etc/dhcpcd.conf
#
```
denyinterfaces wlan0 eth1 

interface br0
  static ip_address=192.168.9.1/24
  nohook wpa_supplicant

```