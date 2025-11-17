# ESP8266-Proxmox-Remote

Tiny ESP8266-based remote control with 128x64 OLED for Proxmox, which can detect existing VMs on the PXE host and retrieve their power and lock status. This remote control allows you to detect failed VMs and start them or shut them down again if necessary.
Access everything without having to open an app on your phone or a pxe web interface on your desktop PC.

![](https://raw.githubusercontent.com/HOCKULUS/ESP8266-Proxmox-Remote/refs/heads/main/preview.GIF?raw=true)![](https://github.com/HOCKULUS/ESP8266-Proxmox-Remote/blob/5a12dc9f08c67870fae8e61c2bca5520daa3e0fa/01.jpeg?raw=true)

## How it works:
The ESP module connects to the Proxmox host via HTTP request through the API and queries a series of predefined IDs. If an ID returns a result, it is added to the list. After this start-up process, the list is displayed. At short intervals, each VM is queried again “in the background” to retrieve the current status (this process may interrupt user input). If you hold down the power button, VMs can be marked as locked (lock icon) and the VM is also tagged as “locked” to save this setting. This is helpful to prevent important VMs from being shut down unintentionally. After a short period of inactivity, the display goes into "sleep mode" and turns off and API requests are paused until a button is pressed.

## Hardware:
- ESP8266
- 128x64 OLED Display
- 3 push buttons (at least 2)
- wires to wire everything up (e.g. 11 jump wires)
- breadboard (400 points)


## Setup
1. open esp8266_PXE_Remote.ino in ardurino ide
2. search and set these variables:
   - ssid (wifi name)
   - password (wifi password)
   - proxmoxHost (your pxe dns hostname, often identical to the Proxmox internal instance)
   - nodeName (Proxmox internal instance name, often identical to the DNS hostname)
   - token (Here is a HowTo to get the API key: https://github.com/CREW8/ESP8266-Proxmox-API)
3. add and install esp8266 board manager http://arduino.esp8266.com/stable/package_esp8266com_index.json
   (HowTo: https://github.com/esp8266/Arduino?tab=readme-ov-file#installing-with-boards-manager)
5. add these librarys in arduino ide:
   - https://github.com/ekstrand/ESP8266wifi?tab=readme-ov-file
   - https://github.com/adafruit/Adafruit-GFX-Library
   - https://github.com/adafruit/Adafruit_BusIO
   - https://github.com/adafruit/Adafruit_SSD1306
   - https://github.com/thomasfredericks/Bounce2
6. wire your esp8266 up:

   ESP -> OLED
   | ESP | OLED |
   |-----|------|
   | 3V3 | VDD |
   | 5V | GND |
   | D1 | SCK |
   | D1 | SDA |
   
   ESP -> Button Up (optional)
   | ESP | Button |
   |-----|--------|
   | D5 | Top |
   | 5V | Bottom |
   
   ESP -> Button Down
   | ESP | Button |
   |-----|--------|
   | D6 | Top |
   | 5V | Bottom |
   
   ESP -> Button Power / Lock
   | ESP | Button |
   |-----|--------|
   | D7 | Top |
   | 5V | Bottom |
   
7. connect your esp8266 via usb, select your esp8266 com port and upload

## Usage
1. select your vm with up and down buttons
2. hard stop or start with power/lock button
3. lock vm by press & hold power/lock button to avoid unwanted power actions
4. wake display after timeout with up or down button
