# VERSION 2.1 UPDATED WITH NEW FEATURES 
### BUY - https://www.tindie.com/products/28875/

## Description
ESP32 based board for temperature monitoring/PWM fan control/addressable LED control in 3D printer enclosures, audio-visual racks, and computer/networking racks. This ESP32 board features, the powerful ESP-WROOM-32E module, with integrated WiFi and Bluetooth functionality (BR/EDR/BLE). The ESP32 is a chip designed with TSMC ultra-low power management technology. The proven ESP32-D0WD-V3 chip is located in the core of the developed module. This board has a USB-C interface for download of firmware and power during development. The board is flashed with an ESPHome image to allow immediate inclusion onto your WiFi network and OTA programming. It also has headers that allow use with conventional D1 Mini style daughter boards and is therefore pin compatible with most accessories. The board has a JST SH connector with I2C and selectable (3.3/5V) power and ground compatible with Adafruit's STEMMA QT/ Sparkfun Qwiic sensors. With optional JST SH to JST PH cable, it also supports STEMMA and Grove interfaces This board also has four Molex KK (PC fan style) that has one 5v driven output, one 5v tolerant input, in addition to fan (typ. 12v) power and ground for 4.5+ amps per connector and up to 10 amps for all four connectors. It also has two, 3-pin screw connector for one-wire devices, each with 3.3v power and ground.

<img src="DesignFiles/3D_top_3_2.jpg" width=400> <img src="DesignFiles/3D_bot_3_2.jpg" width=400>

## Specifications:

* Size: 84mm x 44mm with 2mm mounting holes
* Processor: ESP32 on ESP32-WROOM-E module with WiFi and BT V4.2
* Power Input: 12v @ 10 amps max via 5.5mm x 2.1/2.5mm barrel connector or 5v via USB-C connector.
* 10 amp input power.
* On Board Regulation: 5v @ 2 amps switching regulator, 3.3v @ 1.0 amp.
* Onboard AHT20 Temperature and Humidity Sensor.
* Input/Output: One 5v tolerant input (1k pullup) and one 5v driven output, with 12V power (4.5+ amps per conn.) and ground on four, four-pin Molex KK series connectors. Compatible with most PWM PC style fans with speed return. Of course other use cases for these interfaces such as driving LED strings are available.
* I/O: Two screw down three position headers with common one-wire interface as well as 3.3v power and ground.
* I/O: USB 2.0 via USB-C connector using the CP2102N.
* I/O: Standard WEMOS daughter interface on two 1x8 pin headers.
* I/O: JST SH connector w/ I2C/PDM interface 3.3v/5.0v selectable power (compatible with Adafruit's STEMMA QT/ Sparkfun Qwiic sensors).
* I/O: Two-pin 2.54mm header with buffered open collector output.
* Add-ons: Relay - uses GPIO18 mapped to the WEMOS daughter interface.

Please note that some fans especially older ones do not conform with the "Intel 4-Wire PWM Controller Fans" specification. These fans do not stop spinning with a PWM duty cycle of 0% but spin at their minimum RPM. Below is a list of some of these fans currently known to us:
* Corsair 31-002319.
* Delta QFR1212GHE (and very possibly other Delta fans).

A 3D printed enclosure is also available: https://www.tindie.com/products/29364/

## Setup and Configuration

* DO NOT ATTEMPT TO POWER FANS FROM USB-C. Supplied power (5v-14V) to barrel connector
needs to match the voltage of the PWM fan (or other device) you are driving. Board has an onboard
self-resetting flex fuse rated at 12 amps.

* To place on WiFi network use 2.4G phone to connect to "AVFAN1 Fallback Hotspot" with password "esphome1" ("trek6666" in some factory flashes). Once connected to your WiFi network, to access the webpage of
the device browse to http://avfan1.local

* Device is flashed with an exmaple ESPhome binary image that has manual control over fans 
and automatic control which can be enabled based the target temperature setting.  Four temperature
sensors control each of the four PWM fan connectors.
Flashed binary image  has "api:" disabled, MQTT enabled.

* For customization, downlaod the example (flashed) code from 
https://github.com/fpovoski/ESP32-Temperature-Monitoring-PWM-Control-Board/blob/main/ESPhome/avfan1.yaml

* Also update WiFi and MQTT server credentials as required.

* Flash over USB or ethernet. To flash over USB use ESPhome Web Flasher https://web.esphome.io/
with the device powered and connected to your host machine.

* For Dallas style sensors (board preprogrammed with logger level: DEBUG), to get device ID follow
Seach for them in the initial logger output when connected to the USB port using ESPhome Web Flasher.
  - Connect your Dallas sensors with logger: DEBUG enabled (factory flash default).
  - Open the ESPHome webtool, connect to the ECB board, view the "Logs" window, hit "Reset",and search for Dallas scan addresses and replace the below addresses with your unique ones.
  - Example Scan:
  - [18:16:42][D][dallas.sensor:084]:     0x8b3ca8f64935b228 4
  - [18:16:42][D][dallas.sensor:084]:     0x783c0af6490d3628 2
  - [18:16:42][D][dallas.sensor:084]:     0xc13c01f09642c928 1
  - [18:16:42][D][dallas.sensor:084]:     0x043c6ef649772f28 3
  - dallasaddress1: "0xc13c01f09642c928"
  - dallasaddress2: "0x783c0af6490d3628"
  - dallasaddress3: "0x043c6ef649772f28"
  - dallasaddress4: "0x8b3ca8f64935b228"  

* For adding Wemos style boards (i.e., relay) with the case installed  use the long (19mm) provided pins.

## Connector to GPIO Mapping.

<img src="work/Fan_Control_Board.0.8.B_rot.PNG" width=400>

### Buffer Open-Collector Ouput on 2.54mm Header J3
| CONNECTOR | PIN1 | PIN2 |
| --------- | ---- | ---- |
| J1 | GND | IO26(OC) |

### Dallas One-wire Screw Terminal Connectors J1-J3
| CONNECTOR | PIN1 | PIN2 | PIN3 |
| --------- | ---- | ---- | ---- |
| J2 | +3.3V | IO27 | GND |
| J3 | +3.3V | IO27 | GND |

### PWM Fan/LED KK Style Connectors J4-J7
- PIN3 - Input 5V tolerant with 1K pullup resistor
- PIN4 - Output 5V drive.
- PWR - Matches input voltage on J9. Rated to 4.5 amps.
			
| CONNECTOR | PIN1 | PIN2 | PIN3 | PIN4 |
| --------- | ---- | ---- | ---- | ---- |
| J4 | GND | PWR | IO33 | IO13 |
| J5 | GND | PWR | IO34 | IO14 |
| J6 | GND | PWR | IO35 | IO25 |
| J7 | GND | PWR | IO39 | IO32 |

### USB-C Connector J8
- USB 2.0, 5V, 2amps.

### Power Jack Connector J9
- +5-14V 12 amps max.
- Directly supplies J4-J7 PWR
- Must match your fan or LED voltage.

| CONNECTOR | Center | Perimeter |
| --------- | ---- | ---- |
| J9 | GND | +5-14V | GND |

### I2C/PDM JST SH Connector J10
- Direct Interface for STEMMA and QWIIC boards typically using I2C or PDM.
- Available for other functions than I2C or PDM.
- PWR - Either +3.3V or +5.0V selectable by J11.

| CONNECTOR | PIN1 | PIN2 | PIN3 | PIN4 |
| --------- | ---- | ---- | ---- | ---- |
| J10 | GND | PWR | IO21/SDA/PDMDATA | IO22/SCL/PDMCLK |

### Power Selection J11
- Voltage level selection for J10.
- Jumper Pin 1 and 2: +5V
- Jumber Pin 3 and 2: +3.3V

| CONNECTOR | PIN1 | PIN2 | PIN3 |
| --------- | ---- | ---- | ---- |
| J11 | +5V | J10.1 | +3.3V |
  
### WeMos D1 Mini Plug P1 and P2

| CONNECTOR | PIN1 | PIN2 | PIN3 | PIN4 | PIN5 | PIN6 | PIN7 | PIN8 |
| --------- | ---- | ---- | ---- | ---- | ---- | ---- | ---- | ---- |
| P1 | +5V | GND | IO16 | IO17 | IO21 | IO22 | RXD/IO03 | TXD/IO01 |
| P2 | +3.3V | IO05 | IO23| IO19 | IO18 | IO26 | IO36 | EN |

## Customer Created Projects Utilizing The ECB
Ando Roots: https://www.printables.com/model/702072-1u-rack-fan-shelf
