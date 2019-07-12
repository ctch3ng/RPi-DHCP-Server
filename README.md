# RPi-DHCP-Server
This project aims to prepare a RPi 3 as a DHCP server for an intranet.

## Enable SSH (Optional)

```
sudo raspi-config
```
From the menu, select <b>5 Interfacing Options</b> --> <b>P2 SSH</b>.


## Install TightVNC<sup>1</sup> & XRDP<sup>2</sup> servers (Optional)

Note<sup>1</sup>: TightVNC is a cross-platform free and open-source remote desktop software application.

Note<sup>2</sup>: XRDP is an open-source implementation of Microsoft RDP (Remote Desktop Protocol) server.

```
sudo apt-get install tightvncserver -y
sudo apt-get install xrdp -y
```
 ## Install gedit<sup>3</sup> (Optional)
 
Note<sup>3</sup>:  gedit is a general-purpose text editor with a clean and simple GUI.
 
 ```
 sudo apt-get install gedit -y
```

## Install ISC DHCP server<sup>4</sup>

```
sudo apt-get install isc-dhcp-server -y
```
Note<sup>4</sup>: ISC DHCP server is a DHCP server program that operates as a daemon to provide Dynamic Host Configuration Protocol service to a network. 

### Assign static IP 192.168.1.1 to the RPi

Edit dhcpcd.conf with gedit (you can replace gedit with nano).
```
sudo gedit /etc/dhcpcd.conf
```
Add the following lines to the end of the document, save, and then exit.

```
interface eth0
static ip_address=192.168.1.1/24
static routers=192.168.1.1
```
### Setup the DHCP Server

Edit dhcpd.conf with gedit (you can replace gedit with nano).
```
sudo gedit /etc/dhcp/dhcpd.conf
```
Add the following lines to the end of the document, save, and then exit.

```
subnet 192.168.1.0 mask 255.255.255.0 {
range 192.168.1.16 192.168.1.239;
option routers 192.168.1.1;
}
```
The DHCP server will allocate IP addresses ranging from 192.168.1.16 to 192.168.1.239 to all clients connected to its eth0 which are running as DHCP clients.

Load the new settings and reboot.

```
sudo dhcpd -cf /etc/dhcp/dhcpd.conf
sudo reboot
```
