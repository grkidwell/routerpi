# Install Raspberry PI OS image 
on Raspberry Pi 

## &nbsp;

Follow [Getting Started](https://www.raspberrypi.com/documentation/computers/getting-started.html) instructions on official raspberrypi.com website

Strongly recommend using the Raspberry PI Imager and selecting
"Raspberry Pi OS Lite (32-bit)"


![Screenshot](img/raspios1.png)

select "Raspberry Pi OS (other)"

![Screenshot](img/raspios2.png)

select "Raspberry Pi OS Lite (32-bit)"

![Screenshot](img/raspios3.png)





    
## Launch Raspi-Config
from raspberry pi terminal
#
    pi@raspberrypi:~$ sudo raspi-config
   

![Screenshot](img/raspios4.png)

## System Options
you may want to change Password and Hostname
![Screenshot](img/raspios5.png)

## Interface Options
enable SSH for remote access
![Screenshot](img/raspios6.png)

## Localization Options
![Screenshot](img/raspios7.png)
#
Under Locale, use spacebar to deselect "en_GB.UTF-8 UTF-8"
![Screenshot](img/raspios8.png)
and select "en_US.UTF-8 UTF-8 
![Screenshot](img/raspios9.png)
none
![Screenshot](img/raspios10.png)
Timezone
![Screenshot](img/raspios11.png)
US
![Screenshot](img/raspios12.png)
As we are favored enough to live in the The Republic of Texas
![Screenshot](img/raspios13.png)
Keyboard
![Screenshot](img/raspios14.png)
Generic 105-key PC (intl.)
![Screenshot](img/raspios15.png)
Other
![Screenshot](img/raspios16.png)
English (US)
![Screenshot](img/raspios17.png)
Scroll up to English (US)
![Screenshot](img/raspios18.png)
Default "Enter" the 2 screens then Finish
![Screenshot](img/raspios19.png)
## Remote ssh login 
from PC terminal you can now remote login to your routerpi
##
    alex@xanadu_pc:~$ ssh pi@routerpi.local
    pi@routerpi:~$ 

## Update and Upgrade
##
    sudo apt update
    sudo apt upgrade