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
sudo apt-get install tightvncserver
sudo apt-get install xrdp
```
 ## Install gedit<sup>3</sup> (Optional)
 
Note<sup>3</sup>:  gedit is a general-purpose text editor with a clean and simple GUI.
 
 ```
 sudo apt-get install gedit
```
### Assign static IP 192.168.1.1 to the RPi

```
sudo gedit /etc/dhcpcd.conf //you can use nano instead of gedit
```
Add the following lines to the end of the document, save, and then exit.

```
interface eth0
static ip_address=192.168.1.1/24
static routers=192.168.1.1
```
