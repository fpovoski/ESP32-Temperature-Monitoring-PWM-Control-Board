# VERSION 2.0 UPDATED WITH NEW FEATURES 
## Shipping: 12/27/23 GET ON THE WAITLIST: https://www.tindie.com/products/28875/

ESP32 based board for temperature monitoring/PWM fan control/addressable LED control in 3D printer enclosures, audio-visual racks, and computer/networking racks. This ESP32 board features, the powerful ESP-WROOM-32E module, with integrated WiFi and Bluetooth functionality (BR/EDR/BLE). The ESP32 is a chip designed with TSMC ultra-low power management technology. The proven ESP32-D0WD-V3 chip is located in the core of the developed module. This board has a USB-C interface for download of firmware and power during development. The board is flashed with an ESPHome image to allow immediate inclusion onto your WiFi network and OTA programming. It also has headers that allow use with conventional D1 Mini style daughter boards and is therefore pin compatible with most accessories. The board has a JST SH connector with I2C and selectable (3.3/5V) power and ground compatible with Adafruit's STEMMA QT/ Sparkfun Qwiic sensors. With optional JST SH to JST PH cable, it also supports STEMMA and Grove interfaces This board also has four Molex KK (PC fan style) that has one 5v driven output, one 5v tolerant input, in addition to fan (typ. 12v) power and ground for 7 amps per connector and up to 12 amps for all four connectors. It also has three, 3-pin screw connector for one-wire devices, each with 3.3v power and ground. Specifications:

* Size: 84mm x 44mm with 2mm mounting holes
* Processor: ESP32 on ESP32-WROOM-E module with WiFi and BT V4.2
* Power Input: 12v @ 12 amps max via 5.5mm x 2.1/2.5mm barrel connector or 5v via USB-C connector.
* 12 amp resettable fused input power.
* On Board Regulation: 5v @ 2 amps switching regulator, 3.3v @ 1.0 amp.
* Input/Output: One 5v tolerant input (1k pullup) and one 5v driven output, with 12V power (7+ amps per conn.) and ground on four, four-pin Molex KK series connectors. Compatible with most PWM PC style fans with speed return. Of course other use cases for these interfaces such as driving LED strings are available.
* I/O: Three screw down three position headers with common one-wire interface as well as 3.3v power and ground.
* I/O: USB 2.0 via USB-C connector using the CP2102N.
* I/O: Standard WEMOS daughter interface on two 1x8 pin headers.
* I/O: JST SH conn w/ I2C interface 3.3v/5.0v selectable power (compatible with Adafruit's STEMMA QT/ Sparkfun Qwiic sensors).

A 3D printed enclosure is also available: https://www.tindie.com/products/29364/

## Setup and Configuration

* DO NOT ATTEMPT TO POWER FANS FROM USB-C. Supplied power (5v-14V) to barrel connector
needs to match the voltage of the PWM fan (or other device) you are driving. Board has an onboard
self-resetting flex fuse rated at 12 amps.

* To place on WiFi network use 2.4G phone to connect to "AVFAN1 Fallback Hotspot" and
update SSID and PASSWORD. Once connected to your WiFi network, to access the webpage of
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
the ESPhome instructions: https://esphome.io/components/sensor/dallas.html.

* For adding Wemos style boards (i.e., relay) with the case installed  use the long (19mm) provided pins.

### Connector to GPIO Mapping.

GPIO	PIN	CONNECTOR		Input	Output	Notes

0	25			pulled up	OK	outputs PWM signal at boot,
						 must be LOW to enter flashing mode
       
1	35	P2.1		TX pin	OK	debug output at boot

2	24			OK	OK	connected to on-board LED, must be left
						 floating or LOW to enter flashing mode
       
3	34	P2.2		OK	RX pin	HIGH at boot

4	26			OK	OK

5	29	P1.7		OK	OK	outputs PWM signal at boot, strapping pin

6	20			x	x	connected to the integrated SPI flash

7	21			x	x	connected to the integrated SPI flash

8	22			x	x	connected to the integrated SPI flash

9	17			x	x	connected to the integrated SPI flash

10	18			x	x	connected to the integrated SPI flash

11	19			x	x	connected to the integrated SPI flash

12	14			OK	OK	boot fails if pulled high, strapping pin

13	16	PWM1-(J4)	OK	OK

14	13	PWM2-(J5)	OK	OK	outputs PWM signal at boot

15	23			OK	OK	outputs PWM signal at boot, strapping pin

16	27	P2.6		OK	OK

17	28	P2.5		OK	OK

18	30	P1.4		OK	OK

19	31	P1.5		OK	OK

20

21	33	P2.4		OK	OK

22	36	P2.3		OK	OK

23	37	P1.6		OK	OK
24

25	10	PWM3-(J6)	OK	OK

26	11	P1.3		OK	OK

27	12	1WIRE		OK	OK

32	8	PWM4-(J7)	OK	OK

33	9	RPM1-(J4)	OK	OK

34	6	RPM2-(J5)	OK		input only

35	7	RPM3-(J6)	OK		input only

36	4	P1.2		OK		input only

39	5	RPM4-(J7)	OK		input only

EN	3	P1.1

3.3	2	P1.8

GND	1	P2.7

GND	15

GND	38

NC	32

+5		P2.8


### Dallas One-wire Connectors
CONN	PIN1	PIN2	PIN3

J1	+3.3V	IO27	GND

J2	+3.3V	IO27	GND

J2	+3.3V	IO27	GND


### PWM PC Style Headers
			PIN3 - Fan Speed Input, 5V Tolerant, 1K Pullup Resistor
			PIN4 - Fan PWM Output, 5V Drive
			
CONN	PIN1	PIN2	PIN3	PIN4

J4	GND	+5/12V	IO33	IO13

J5	GND	+5/12V	IO34	IO14

J6	GND	+5/12V	IO35	IO25

J7	GND	+5/12V	IO39	IO32


J8 	USB2.0 on USB-C (USB can be connected when when barrel connector power  but not advised).

J9	+5/12V 	12 amps Max. to board and fans. (5-14v range, needs to match devices on J4-J7)


P1 and P2  - Standard WEMOS D1 Expansion Header
