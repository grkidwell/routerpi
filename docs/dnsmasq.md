## DNSmasq
DNSmasq uses dhcp to provide ip addresses to clients
#
    sudo apt install dnsmasq
    sudo nano /etc/dnsmasq.conf
#
```
#interface=br0    
# Listening interface
interface=br0

dhcp-range=192.168.9.2,192.168.9.20,255.255.255.0,24h
                # Pool of IP addresses served via DHCP
domain=wlan     # Local wireless DNS domain
address=/gw.wlan/192.168.9.1
                # Alias for this router

```
