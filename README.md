# raspberry-multi-room-audio

This is a collection/explanation of several steps when trying to build a multi-room-audio system raspberry pi based.
The key feature therefore is the amazing software snapcast, written by badaix: https://github.com/badaix/snapcast

# Setting up Clients

Take raspberry pi (in my case model 3) and set up the snapclient.

## Setting up network
add your network information to "/etc/wpa_supplicant/wpa_supplicant.conf"
network = {
 ssid="YourNetworkName"
 psk="YourNetworkPassword"
 key_mgmt=WPA-PSK
}
(Automated: wget ... /etc/wpa_supplicant/wpa_supplicant.conf, ATTENTION! you overwrite your previous configured file!)

For static ip:

Make sure dhcpcd is active:
sudo service dhcpcd status
(otherwise enable it with:
sudo service dhcpcd start
sudo systemctl enable dhcpcd)

add to "/etc/dhcpcd.conf":
interface eth0
static ip_address=192.168.178.100/24
static routers=192.168.1.1
static domain_name_servers=192.168.1.1

choose a unique ip address.
(Automate: wget ... /etc/dhcpcd.conf, ATTENTION! you overwrite your previous configured file!)
