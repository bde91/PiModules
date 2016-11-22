The Peripherals I2C Control, "The PICo Interface", is an implementation of I2C interface adapted for control of the peripherals connected to the Raspberry Pi via the command line or through programming language.  By using simple commands, control of UPS PIco peripherals is made extremely simple. Control at programming language level is also possible and easy. The core concept of the PICo interface is that all peripheral device control and data exchange between it and the Raspberry Pi variables are common for the I2C interface and any connected peripherals. Therefore any changes by either party, Raspberry Pi or the peripheral, causes immediate update and action.

Two types of variables are available:
* Common - where data is stored in the same place and any change on it will cause action on the UPS PIco Module
* Mirror - where a copy of data is stored on internal variables of the UPS PIco HV3.0 Module. They are protected, so changes on it will not impact the UPS PIco HV3.0 Module functionality and will be only be overwritten when the UPS PIco HV3.0 Module recognised changes on them.

The following PICo addresses are assigned to the following entities:

## 0x69 ->UPS PIco HV3.0 Module Status Registers Specification

In order to access the 0x69 variables the following commands need to be executed from the OS command line or programming language interface, for example:

To find the powering mode: 1 or 2

    sudo i2cget -y 1 0x69 0x00 b

To find the battery level Battery Level value in 10th of mili volts

    sudo i2cget -y 1 0x69 0x08 w

## 0x69 Variable Table

|**Address**| **Name**|**Size**|**Type**|**R/W**|**Explanation of Register Function**|
|:---:|:----:|:---:|:---:|:---:|:---:|
|**0x00**|mode|Byte|Mirror|Read|Powering Mode – Read ONLY, Writing has no effect on the system and will be overwritten by UPS PIco HV3.0 with the new value 0x01 - RPI\_MODE (means cable powering mode) 0x02 - BAT\_MODE|
|**0x08**|batlevel|Word|Mirror|Read|Means value of Battery Voltage in 10th of mV in BCD format|
|**0x0a** |rpilevel|Word|Mirror|Read|Means value of Voltage supplying RPi on J8 5V Pin in 10th of mV in BCD format|
|**0x0c**|eprlevel|Word|Mirror|Read|Means value of Extended Voltage supplying RPi on Extended Voltage input (7-28VDC) in 10th of mV in BCD format|
|**0x14**|a5v0level|Word|Mirror|Read|Means value of the first A/D converter pre scaled to 5.2V. Higher voltage could not be supplied without a resistor divider. Readings are in 10th of mV in BCD format|
|**0x1b**|ntc|Byte|Mirror|Read|Temperature in Celsius degree of the embedded NTC1 sensor placed on the top of PCB. Values in BCD format.|
|**0x1c**|TO92|Byte|Mirror|Read|Temperature in Celsius degree of the TO-92 sensor placed on the bottom of PCB. It is valid only if this sensor is soldered. It is available in the PIco Fan Kit. Values in BCD format.|
|**0x22**|pico_is_running|Word| Mirror   | Read    | It is a 16 bit unsigned variable that value of it, is changing every 1 ms within the main loop of the firmware. Reading two times of this variable must return a different value (with interval longer than 1 ms), if not, means that system hangs-up, and need to be reset, if not restarted by other PIco protection internal mechanism (watch-dog, and supervising watch dog). As these protection mechanisms are always restarting the system when something goes wrong, reason of existence of this variable is just to confirm to the remote user that everything is working well and give feedback to the remote user that system is running properly. As it is a mirror variable, writing to it nothing change, will be again re-written with the newer internal value.|
|**0x24**|pv|-|-|-|PCB Version - current available versions: A|
|**0x25**|bv|-|-|-|Bootloader Version - current available versions: S - BL\_PIco HV 3.0A Stack/TopEnd default LP Battery F - BL\_PIco HV 3.0A Stack/TopEnd default LF Battery P - BL\_PIco HV 3.0A Plus default LP Battery Q - BL\_PIco HV 3.0A Plus default LF Battery|
|**0x26**|fv|-|-|-|Firmware Version: current 0x0E dated 01/11/2016|
