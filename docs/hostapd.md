## Hostapd
Hostapd is use to create a wireless accesspoint for clients to wirelessly connect to the raspberry pi.  Both the Raspberry Pi3 and Raspberry Pi4 have built in wifi so don't require an external usb2wifi dongle.
#
    sudo apt install hostapd
    sudo nano /etc/hostapd/hostapd.conf
#
```
country_code=US
interface=wlan0
bridge=br0
ssid=routerpi

hw_mode=g
channel=4

ieee80211d=1
ieee80211n=1

logger_syslog=-1

macaddr_acl=0
auth_algs=1
ignore_broadcast_ssid=0
wpa=2
wpa_passphrase=stoutlore
wpa_key_mgmt=WPA-PSK
wpa_pairwise=TKIP
rsn_pairwise=CCMP

```
#
    sudo systemctl unmask hostapd
    sudo systemctl enable hostapd
    sudo systemctl start hostapd
