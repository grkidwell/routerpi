# Welcome to Routerpi
Tutorial for setting up raspberry pi as a wired and wireless router with wireguard vpn.

For repository of these insturctions see[github routerpi](https://github.com/grkidwell/routerpi)

# Components

1. Raspberry Pi Lite USB Image

2. Ethernet to USB Dongle

3. Autossh reverse ssh tunnel between raspberry pi and digital ocean server for maintenance.

4. Hostapd for settting up a wireless Access Point

5. Dnsmasq for assigning a static IP to the subnet

6. Dhcpcd for creating dhcp address assignments to client subnet

7. IPtables for creating a NAT

8. Systemd-Netword for creating a bridge between the client wifi and ethernet NICs

9. Wireguard to create secure encrypted VPN tunnel between multiple Routerpi's and other devices.


## Architecture

