
Note that as of 2021-10-22, this PCB was not tested in a live printer.  
The design and trace were reviewed by Flisher and Hart.    
DRC Checking during the design, and continuity test were performed with a real PCB.  
The Neopixel and LED port where tested with success too.  

## ERCFv2
![PCB](../../Images/ERCFv2/1.png)

The [wiring diagram](../Images/Rev3.2/wiringDiagram.png) was designed for the regular V4.0 version but you can get an idea of the wiring by looking at it.
 
### Pinout (LEFT ROW FROM TOP)
* PROBE/ABL  - Probe Signal Pin
* PCF  - Part Cooling Fan -V
* CT   - Chamber Thermistor Signal Pin (TH1)
* FS  - Filament Sensor
* GND  - PSU -V (NOT MAINS GND)
* AGND - Hotend Thermistor -V
* 5V   - required for NeoPixel and optional jump solder
* HE0  - Hotend Heater -V    
* 24V  - HE0 +V 

### Pinout (RIGHT ROW FROM TOP)
* 12V - 12 V+
* XES  - X Endstop Signal Pin    
* HEF  - Hotend Cooling Fan -V
* TH0  - Hotend Thermistor Signal Pin (TH0)
* S2B  - Black Stepper Wire 
* S2A  - Green Stepper Wire
* S1A  - Red Stepper Wire
* S1B  - Blue Stepper Wire
* LED  - WS2812 / NeoPixel LED Input Wire
    
    
## The board require: ##
* a BAT85 Diode for abl probe
* 2 Pins Microfit 3.0 for the heater
* 18 Pins Microfit 3.0 for the main harness
* Solder jumper for HEC, PCF and Probe.  Default in Voron is 24v for evey one

## The board features: ##
 - RGB NeoPixel LED, configurable via macro or script.  This LED is the first one of the sequence when using the LED connectors
 - 2/3 pin headers for most components on the toolhead
 - 0805 pkg thermistor to be used as a chamber temperature 
 - the main wiring harness connector is [Here](https://www.molex.com/molex/products/part-detail/crimp_housings/0430251400) <--- to be revised
 - 20awg should be fine for 24v and HE0, 24awg for everything else 

## HOW-TO NEOPIXEL ##
You can use any NeoPixel or WS2812 LED macros or configuration already documented for your Voron.

A super simple to use sample of code can be found [here](https://github.com/hartk1213/DoomConfig/blob/master/led.cfg).

## JUIMP SOLDER CONFIGURATION
Example of Solder Solder Jumper for default configuration in most Vorom (24v fan and probe)
![PCB](../../Images/ERCFv2/solderjumper.png)
![Instruction](../../Images/ERCFv2/solderjumper-example.png)

## TODO ##
Add Molex part numbers
