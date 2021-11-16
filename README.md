# Afterburner Toolhead PCB - Neo v1.0 #

## Description ##
The goal of this PCB was to replace the LED with a NeoPixel and add an additionnal connector for Adressable LED.  
This version is a spiritual successor to both original Hartk Afterburner PCB.  

I created this version of the PCB with the following ideas in mind:
* Maintain Hartk ERCF Toolhead PCB form factor
* Replace the LED by a NeoPixel (WS2812B RGB LED)
* Keep wiring diagram and layout as close as possible to the Hartk's ERCF Toolhead PCB
* Add a jump solder for the BAT85 

I'm FlisherOfatale#0042 on the VORONDesign Discord Server if you need more information.

Comprehensive list of the PCB I know about, comparison are VS Hartk's V4.0
|Model|Feature|Note|Input|Voltage|LED|Designer|
|-|-|-|-|-|-|-|
|3.2|Standard|Mount with M3 washers|14 pins|24v|Red|Hartk|
|[4.0](https://github.com/VoronDesign/Voron-Hardware/tree/master/Afterburner_Toolhead_PCB/)|Standard|improved traces width|14 pins|24v|Red|Hartk|
|[ERCF](https://github.com/VoronDesign/Voron-Hardware/tree/master/Afterburner_Toolhead_PCB/)|+Filament Sensor||14+2 pins|5/24v<br>jump solder/cut|Red|Hartk|
|[Neo](./Production%20Files/ERCF/)|+Filament Sensor<br>+Neo Pixel on board<br>LED connector<br>XES merged with FS||14+2 pins|24v<br>5v LED|RGB|Flisher|
|[Neo XL](./Production%20Files/ERCF/)|Neo's Feature<br>+5/12v options|complex to use|18 pins|5/24v<br>jump solder|RGB|Flisher|

Personal Note: 
* There is no real reason to not use the ERCF VS v4.0, even if you don't have the additionnal 2 wires
* Replacing an ERCF for a Neo should be really simple for the following scenarios with only configuration:
    * ERCF Setup / no XES 
    * Non-ERCF Setup

![Neo v1.0](Neo/Images/pcb-layout.png)

## DISCLAIMER ## 
As of 2021-11-15, this PCB WAS NOT TESTED IN A LIVE PRINTER.  
The design was done by Flisher with guidance from Hartk.  
DRC Checking during the design phase.  
Continuity test were performed with a meeter on a real PCB.  
The Neopixel and LED port were tested with success too.  

IMPORTANT:
This PCB reuse most of the ERCF wiring pattern, EXCEPT the XES.
The XES pin is reused for the LED.  For many person, this won't require any wiring at all, unless XES was used.
Note taht you can't have both XES and FS at the same time with this PCB, considering XES is rarely used, this PCB should be polyvalent enought for most people.
## Pinout ##
### LEFT ROW FROM TOP ##
* PROBE/ABL  - Probe Signal Pin
* 24V  - HE0 +V 
* PCF  - Part Cooling Fan -V
* AGND - Hotend Thermistor -V
* TH0  - Hotend Thermistor Signal Pin (TH0)
* GND  - PSU -V (NOT MAINS GND)
* LED  - WS2812 / NeoPixel LED Input Wire (was XES on Hartk's PCB)

### RIGHT ROW FROM TOP ##
* HE0  - Hotend Heater -V    
* CT   - Chamber Thermistor Signal Pin (TH1)
* HEF  - Hotend Cooling Fan -V
* S2B  - Black Stepper Wire 
* S2A  - Green Stepper Wire
* S1A  - Red Stepper Wire
* S1B  - Blue Stepper Wire

### Microfit 2 pin In:
* 5V   - required for NeoPixel and optional jump solder
* FS  - Filament Sensor / XES - X Endstop Signal Pin

## BOM ##
* a BAT85 Diode for abl probe (Original Afterburner BOM)
* 2 Pins Microfit 3.0 for the heater
   * PCB: [Molex 436500200](https://www.digikey.ca/en/products/detail/molex/0436500200/268989)
   * Wires: [Molex 0436450200](https://www.digikey.ca/en/products/detail/molex/0436450200/268974)
* 14 Pins Microfit 3.0 for the main harness: 
   * PCB: [Molex 0430451801](https://www.digikey.ca/en/products/detail/molex/0430451400/531423)
   * Harness: [Molex 0430251800](https://www.digikey.ca/en/products/detail/molex/0430251400/531405)
* 18 x [Microfit 3.0 Female Crimp 0430300007](https://www.digikey.ca/en/products/detail/molex/0430300007/252479)
* 3 x JST-XH 2 PIN (PCB, wire and crimp)
* 3 x JST-XH 3 PIN (PCB, wire and crimp)
* Same mounting kit and screw than [Hartk Afterburner PCB V4.0](https://github.com/VoronDesign/Voron-Hardware/blob/master/Afterburner_Toolhead_PCB)

## WIRING RECOMMENDATION ##
* 20awg should be fine for 24v and HE0 
* 24awg for everything else 
     
## HOW-TO NEOPIXEL ##
You can use any NeoPixel or WS2812 LED macros or configuration already documented for your Voron.

A super simple to use sample of code can be found [here](https://github.com/hartk1213/DoomConfig/blob/master/led.cfg).
Please reach out to me if you have interesting script to suggest, I'll add them to the repository.  


# Afterburner Toolhead PCB - Neo XL v1.0 #
The Neo XL variant was created with the following idea in mind:
* Maintain Hartk ERCF Toolhead PCB form factor
* Add features such have voltage option, NeoPixel, Led Strip.
* The only version know to have been produced where labeled ERCFv2 and distributed by Flisher for testing purpose.
* This version doesn't support standard Hartk's PCB wiring.
* File from the production server are still flagged as ERCFv2, will be fixed once someone confirm the design work.
Details about this version  [Here](./NeoPlus/README.md)
This is an PCB more complex version without any backward compatibilities
Note that I'm not intenting to support this version in the long run, the regular Neo will do the trick for most.

