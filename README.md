# RPi-DHCP-Server
This project aims to prepare a RPi 3 as a DHCP server for an intranet.

## Enable SSH (Optional)

```
sudo raspi-config
```
From the menu, select <b>5 Interfacing Options</b> --> <b>P2 SSH</b>.


## Install TightVNC & XRDP servers

Note<sup>1</sup>: TightVNC is a cross-platform free and open-source remote desktop software application

Note: XRDP is an open-source implementation of Microsoft RDP (Remote Desktop Protocol) server

```
sudo apt-get install tightvncserver
```
