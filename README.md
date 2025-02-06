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

