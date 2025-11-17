# ESP8266-Proxmox-Remote
Tiny ESP8266-based remote control with 128x64 OLED for Proxmox, which can detect existing VMs on the PXE host and retrieve their power and lock status. This remote control allows you to detect failed VMs and start them or shut them down again if necessary.
Access everything without having to open an app on your phone or a pxe web interface on your desktop PC.

![](https://github.com/HOCKULUS/ESP8266-Proxmox-Remote/blob/5a12dc9f08c67870fae8e61c2bca5520daa3e0fa/01.jpeg?raw=true)

## Hardware:
- ESP8266
- 128x64 OLED Display
- 3 push buttons (at least 2)
- wires to wire everything up (e.g. jump wires)
- breadboard (400 points)


## Setup
1. open esp8266_PXE_Remote.ino in ardurino ide
2. set the variables:
   - ssid (wifi name)
   - password (wifi password)
   - proxmoxHost (your pxe dns hostname, often identical to the Proxmox internal instance)
   - nodeName (Proxmox internal instance name, often identical to the DNS hostname)
   - token (Here is a HowTo to get the API key: https://github.com/CREW8/ESP8266-Proxmox-API)
  
3. add esp8266 board manager ([http://arduino.esp8266.com/stable/package_esp8266com_index.json](https://github.com/esp8266/Arduino?tab=readme-ov-file#installing-with-boards-manager)) 


