# raspberry-multi-room-audio

This is a collection/explanation of several steps when building a raspberry pi based multi-room-audio system.
The key feature therefore is the amazing software snapcast, written by badaix: https://github.com/badaix/snapcast

# Setting up Clients

Take raspberry pi (in my case model 3) and set up the snapclient.

## Setting up network
add your network information to "/etc/wpa_supplicant/wpa_supplicant.conf"
````
network={
 ssid="YourNetworkName"
 psk="YourNetworkPassword"
}
````
For static ip:

Make sure dhcpcd is active:
````
sudo service dhcpcd status
````
(otherwise enable it with:
`sudo service dhcpcd start;
sudo systemctl enable dhcpcd`)

add to "/etc/dhcpcd.conf":
````
interface wlan0
static ip_address=192.168.178.100/24
static routers=192.168.1.1
static domain_name_servers=192.168.1.1

timeout 5

````
choose a unique ip address.

## Setting up snapclient

follow instructionn in https://github.com/badaix/snapcast/blob/master/doc/build.md#linux-native

# SSH without password 

http://www.schlittermann.de/doc/ssh.html

# Autostart Scripts on Raspberry Pi 3

add the desired programs to 
/home/user/config/lxsession/LXDE-pi/autostart

# References

https://volumio.org/forum/multiroom-audio-output-from-volumio-with-snapcast-t3217.html
