# RUBRIColor-Firmware-Upgrade
Firmware for the RUBRIColor

## Requires 
  Vescent SLICE_Firmware_Upgrade_Utility available at:
  
  https://github.com/Vescent/SLICE-FFC_Firmware_Upgrade_Utility
## Instructions
 
  Left click on SLICE_Firmware_Update_Instructions.pdf and then click 'Download' to download the instructions for use.

  The V1.42 firmware upgrader automatically retrieves the upgrade files from this repository. However, if your system does not allow this,  
  You may need to perform the following steps:  
  
       Left click on the upgrade package (RUBRIColor_Sx.xxx_LDx.xx_QTx.xxx.zip) and then click 'Download' to download the firmware package to your  
       hard drive.
  
       The 3 files in the .zip file need to be placed in the folder described in the instructions. DO NOT RENAME THEM!  
       
## Configuration S1.123_LD1.25_QT2.73 Prototype for test purposes
1.  LD Version 1.25 Implements fixes to LTC2440 high resolution temperature error ADC that have been added 
	to 90-00028 firmware after unlock events were observed on the RUBRIComb
2.  QT Version 2.73
	Adds case 38 to debug output for CMD_ReadTemp() to return the raw temperature ADC value
	Changes SPI D MOSI pin from pull up to pull down to help avoid sporatic LTC2440 timing changes.	
3.  S Version 1.123
	Includes support for #GRAPHDATAEN API fast data logging through serial port.
	Allows Setting SHG temperature setpoints on both the channel settings menu and the single channel summary page. 	
	Improve SHG cooldown performance
	Add support for *CLS API command so that on screen messages can be cleared without touching the touchscreen.
	Fixes ability to set the device serial number and some handling of color module type assignments.
	Fixes missing NO Temperature Control module identification on the touch screen
	### Uses the module identification API setting command outlined in the Configuration S1.114_LD1.23_QT2.71 below
	Where setting number of temperature controls to 0 indicates a non LD board in the module (channel)
	
## Configuration S1.119_LD1.24_QT2.72 Prototype for test purposes
1.  Adds support for original color module naming scheme so that units that are already in the customer's hands
    can be upgraded without needing the color modules to be renamed.
2.  Fixes issue determining temperature stability when one or more color modules are designated as HT NOTEMPERATURE models
3.  Fixes the failure to re-establish STANDBY stability after an interlock is cleared without needing to return to SYSTEM OFF
4.  Removes ghost querying of SHG channel temperature errors and Diode temperature errors when ONETEMP or NOTEMP color
    modules are configured.

## Configuration S1.118_LD1.24_QT2.72 Prototype for test purposes
1.  Fixes 24V Power Good dropout error messaging and error handling
2.  Fixes messed up Interlock error message handling if the interlock is opened 
    while in the general settings menu
3.  Revises the SHG channels' output current monitoring to re-zero when TEC / Heater current is in the off state.
4.  Fixes backlight and volume numeric level updating so that it responds to API setting
5.  Adds the System Controller firmware build configuration to the response for a #DEVICES API command

## Configuration S1.117_LD1.23_QT2.71 Prototype for test purposes
1.  Fixes Color Module Labeling so that a prefix only can be configured without a wavelength
    (Simply omit the wavelength argument when using the #RCOLORMODULE command.)
2.  Fixes missing thermistor type dropdown menu from Plant Settings screen
3.  Fixes NV saving of thermistor settings so that they persist through a power cycle
4.  Fixes I2C error reset if the touch screen is touched too soon after power on
5.  Adds the ability to adjust the color module current output setpoint for 0 temperature control color modules
6.  Some improvements to serial API for factory settings. Still needs more work. 
7.  Adds the system controller build configuration to the return from the #DEVICES API command

## Configuration S1.116_LD1.23_QT2.71 Prototype for test purposes
1.  Disables automatic system shutdown when internal temperature exceeds the 65C threshold 

## Configuration S1.115_LD1.23_QT2.71 Prototype for test purposes
1.  Fixes lockup when trying to access single channel summary screen for SHG channels when less than 4 color modules are installed


## Configuration S1.114_LD1.23_QT2.71 Prototype for test purposes
1.  Adds No Temperature Control color modules to the list of acceptable module types
2.  Changes API commands for chosing and labeling Color Modules.
  ### USE:
	To Set     #RCOLORMODULE [channel] [49382] [# temp controls] [prefix + wavelength]
 	To Read    #RCOLORMODULE? [channel]
    	Note: prefix is limited to 3 characters and no space between the prefix and wavelength
              Number of temp controls is 0, 1, or 2
              Example: Heterodyne SHG with a 525nm wavelength for channel 1
              Use this command: #RCOLORMODULE 1 49382 2 SHG525
              
              
## Configuration S1.113_LD1.21_QT2.71 Prototype for test purposes
1.  Fixes some API issues with setting color module type and other factory available settings commands.

## Configuration S1.112_LD1.21_QT2.70 Prototype for test purposes
1.  Blocks addess to diode setpoint readouts so diode setpoints will need to be adjusted through the API
2.  Adds Internal Temperature Safety Shutdown and Message presentation

## Configuration S1.111_LD1.21_QT2.69 Prototype for test purposes
1.  Changes configuration of Threshold Detection Input pin to Input Pull Down
2.  Blocks SHG API commands to Non HXXX and XXX modules which do not use the SSG channel

## Configuration S1.110_LD1.21_QT2.69 Prototype for test purposes
1.  Blocks access to Temperature and Current control on an individual channel basis
2.  Changes API commands to use "S" for SHG and "D" for Diode prefixes 
    Using the following format:
    [S/D][COMMAND][channel#][argument]

## Configuration S1.109_LD1.21_QT2.69 Prototype for test purposes
1.  Minor adjustments to the layout of the single channel temperature summary page

## Configuration S1.108_LD1.21_QT2.69 Prototype for test purposes
1.  Fixes Missing Saved laser current setpoint and diode temperature setpoints on startup
2.  Fixes momentary white text color when switching between settings and main screen while in a standby or laser mode

## Configuration S1.107_LD1.21_QT2.69 Prototype for test purposes
1.  Fixes bug that would leave some SHG temperature controls in an on state after the cooldown stage.
2.  Fixes bug that would change the frequency number for the color module label to 000 when the laser was in an on state
3.  Changes the Cool-down indicator from a flashing message on each channel's SHG readout to having the main control button flash "COOL DOWN" 
    until all channels have finished their cool down sequence.
4.  Adds GUI warning indicators for temperature controller out of range and laser temperature above limit.	

## Configuration S1.106_LD1.21_QT2.69 Prototype for test purposes
1.  Fixes bug that would leave the SHG temperature control in an on state after the cooldown stage.
2.  Fixes inoperative GUI feedback when using Serial API commands

## Configuration S1.105_LD1.21_QT2.69 Prototype for test purposes
1.	Adds:
	Cool-down stage for SHG temperature heaters. Based on a timer that calculates the time from current servo on temperature to 15C. 
	Keeps the channel servo enabled until the timer expires. 
	NOTE: ambient temperature will probably not be 15C so we might want to adjust this target
	This feature is only available for SHG temperature controls that have a non-zero slew rate enabled and a heater type selected in the Plant Thermistor settings.
2.	Adds:
	"#ADJCHAN" 1 API Command which unlocks access to all temperature channel settings from the single channel summary page.
	Power Cycling the device makes this access go away.
3.	Fixes the temperature servo current readout for diode channels to display negative current. 	

## Configuration S1.104_LD1.20_QT2.69 Prototype for test purposes
1.	Adds:
	Interlock warning functionality
2.	Adds:
	Threshold Detection Laser Current Gating and Warning on Loss of Threshold Input

