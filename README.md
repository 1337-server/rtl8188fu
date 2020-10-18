For Kernel 4.15.x ~ 5.8.x (Linux Mint, Ubuntu or Debian Derivatives)

------------------

## How to install (for arm devices)

`sudo apt-get install build-essential git dkms linux-headers-$(uname -r)`

`git clone -b arm https://github.com/kelebek333/rtl8188fu rtl8188fu-arm`

`sudo dkms add ./rtl8188fu-arm`

`sudo dkms build rtl8188fu/1.0`

`sudo dkms install rtl8188fu/1.0`

`sudo cp ./rtl8188fu/firmware/rtl8188fufw.bin /lib/firmware/rtlwifi/`

------------------
## For installation on RPi-LibreELEC
 Follow instructions here to add a new package
--> https://forum.libreelec.tv/thread/17704-odroid-c2-compile-kernel-for-0bda-f179-support/?postID=145448#post145448
 after Pi boots you will need to SSH into RPI via Ethernet cable and Follow this instructions as the GUI will not work
--> https://gist.github.com/maoueh/8260199 OR https://gist.github.com/maoueh/8260199#file-gistfile1-md


Run following commands for disable power management and plugging/replugging issues.

`sudo mkdir -p /etc/modprobe.d/`

`sudo touch /etc/modprobe.d/rtl8188fu.conf`

`echo "options rtl8188fu rtw_power_mgnt=0 rtw_enusbss=0" | sudo tee /etc/modprobe.d/rtl8188fu.conf`


Run following commands for disable MAC Address Spoofing (No need Ubuntu based distributions. MAC Address Spoofing is already disable on Ubuntu base).

`sudo mkdir -p /etc/NetworkManager/conf.d/`

`sudo touch /etc/NetworkManager/conf.d/disable-random-mac.conf`

`echo -e "[device]\nwifi.scan-rand-mac-address=no" | sudo tee /etc/NetworkManager/conf.d/disable-random-mac.conf`

------------------

## How to uninstall

`sudo dkms remove rtl8188fu/1.0 --all`

`sudo rm -f /lib/firmware/rtlwifi/rtl8188fufw.bin`

`sudo rm -f /etc/modprobe.d/rtl8188fu.conf`


