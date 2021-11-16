# Afterburner Toolhead PCB Neo Plus 1.0 #


# DISCLAIMER #1 #
While it should work properly, I can't guarantee it will work or not break something until I or someone test it in a live printer.  

As of 2021-11-15, this PCB WAS NOT TESTED IN A LIVE PRINTER.  

The design was done by Flisher with guidance from Hartk.  
DRC Checking during the design phase.  
Continuity test were performed with a meeter on a real PCB.  
The Neopixel and LED port were tested with success too.  

# DISCLAIMER #2 # 
CURRENT PRODUCTION FILE AND IMAGES ARE LABELED ERCFv2, BUT THIS PCB IS IN THE PROCESS OF BEING RENAMED to NEO
PICTURE AND PRODUCTION FILE WILL BE UPDATED SHORTLY< PLEASE DONT SEND THE CURRENT VERSION TO PRODUCTION TO AVOID CONFUSION


The design was done byt Flisher with guidance from Hartk.  
DRC Checking during the design.  
Continuity test were performed with a meeter on a real PCB.  
The Neopixel and LED port where tested with success too.  


FlisherOfatale#0042 on the VORONDesign Discord Server have some PCB available if you want to test it (Canada prefered, US possible)

# Afterburner Toolhead PCB - Neo XL v1.0 #
## Description ##
The goal of this PCB was to replace the LED with a NeoPixel and add an additionnal connector for Adressable LED.  
This version is a spiritual successor to the both original Hartk Afterburner PCB.  

## Features ##
 - Same form factor than the original Hartk Afterburner PCB ERCF (compatible with the v4.0 mount)
 - RGB NeoPixel LED, configurable via macro or script.  This LED is the first one of the sequence when using the LED connectors
 - 2/3 pin JST-XH headers for most components on the toolhead JST-XH
 - 0805 pkg thermistor to be used as a chamber temperature 
 
While effort were made to maintain the same form factor than the ERCF version to maintain compatibility with other mods, the following change were required:
* Main harness bumped from 14/14+2 to 18 pin
* Main harness pinout changed from the original PCB
* Connectors where moved around on the PCB on the PCB had to be changed

![PCB](/Images/pcb-layout.png)

This [wiring diagram](https://github.com/VoronDesign/Voron-Hardware/blob/master/Afterburner_Toolhead_PCB/Images/Wiring/ERCF-Toolhead%20SKR%201_4%20wiring.png) was designed for the regular V4.0 version but you can get an idea of the wiring by looking at it.

## Pinout ##
### LEFT ROW FROM TOP ##
* PROBE/ABL  - Probe Signal Pin
* PCF  - Part Cooling Fan -V
* CT   - Chamber Thermistor Signal Pin (TH1)
* FS  - Filament Sensor
* GND  - PSU -V (NOT MAINS GND)
* AGND - Hotend Thermistor -V
* 5V   - required for NeoPixel and optional jump solder
* HE0  - Hotend Heater -V    
* 24V  - HE0 +V 

### RIGHT ROW FROM TOP ##
* 12V - 12 V+
* XES  - X Endstop Signal Pin    
* HEF  - Hotend Cooling Fan -V
* TH0  - Hotend Thermistor Signal Pin (TH0)
* S2B  - Black Stepper Wire 
* S2A  - Green Stepper Wire
* S1A  - Red Stepper Wire
* S1B  - Blue Stepper Wire
* LED  - WS2812 / NeoPixel LED Input Wire
     

## BOM ##
* a BAT85 Diode for abl probe (Original Afterburner BOM)
* 2 Pins Microfit 3.0 for the heater
   * PCB: [Molex 436500200](https://www.digikey.ca/en/products/detail/molex/0436500200/268989)
   * Wires: [Molex 0436450200](https://www.digikey.ca/en/products/detail/molex/0436450200/268974)
* 18 Pins Microfit 3.0 for the main harness: 
   * PCB: [Molex 0430451801](https://www.digikey.ca/en/products/detail/molex/0430451801/3310258?4)
   * Harness: [Molex 0430251800](https://www.digikey.ca/en/products/detail/molex/0430251800/531407)
* 20 x [Microfit 3.0 Female Crimp 0430300007](https://www.digikey.ca/en/products/detail/molex/0430300007/252479)
* 4 x JST-XH 2 PIN (PCB, wire and crimp)
* 3 x JST-XH 3 PIN (PCB, wire and crimp)
* Same mounting kit and screw than [Hartk Afterburner PCB V4.0](https://github.com/VoronDesign/Voron-Hardware/blob/master/Afterburner_Toolhead_PCB)

## WIRING RECOMMENDATION ##
* 20awg should be fine for 24v and HE0 
* 20awg is recommended for 5v and 12v wire (future proof in case you need more power in future mod...)
* 24awg for everything else 

Important Note related to wiring requirement :
* the 5v wire is required for the NeoPixel and LED connector
* the 12v is only required if you plan to use 12v on fan or probe, but, I would still pass the wire even if not in use to avoir rewiring a wire later...


## HOW-TO NEOPIXEL ##
You can use any NeoPixel or WS2812 LED macros or configuration already documented for your Voron.

A super simple to use sample of code can be found [here](https://github.com/hartk1213/DoomConfig/blob/master/led.cfg).

## JUMP SOLDER CONFIGURATION
## WARNING - WARNING ##
* Please validate you are jump soldering the right voltage for your usage.  Refer to the image below for example
* DO NOT solder jumper 2 differents voltage to the same 
* When soldering 12/24v, doublecheck the connectivity with the unused pad and the middle one to be sure you did not short 12 and 24v together.
 

Example of Solder Solder Jumper for default configuration in most Vorom (24v fan and probe)
![PCB](/solderjumper-example.png)
*Note that the picture label ERCFv2, which was the name during prototyping phase, it's the same than the Neo v1.0 

![Instruction](/Images/solderjumper-instructions.png)

Special thank to Hartk for his guidance and help.  Is original work can be found [here](https://github.com/hartk1213/Voron-Hardware/tree/master/Afterburner_Toolhead_PCB)
