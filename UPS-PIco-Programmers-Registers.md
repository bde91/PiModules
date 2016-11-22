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

### 0x69 Variable Table

|**Address**| **Name**|**Size**|**Type**|**R/W**|**Explanation of Register Function**|
|:---:|:----:|:---:|:---:|:---:|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------:|
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

## 0x6A -\> UPS PIco Hardware RTC Registers Direct Access Specification

### 0x6A Variable Table

|**Address**| **Name** | **Size** | **Type** | **R/W** | **Explanation**  |
|:---:|:----:|:---:|:---:|:---:|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------:|
|**0x00**|seconds|Byte     | Mirror   | Read    | seconds in BCD   |
|**0x01**|minutes|Byte     | Mirror   | Read    | minutes in BCD   |
|**0x02**|hours|Byte     | Mirror   | Read    | hours in BCD     |
|**0x03**|wday |Byte     | Mirror   | Read    | week day in BCD  |
|**0x04**|mday|Byte     | Mirror   | Read    | month day in BCD |
|**0x05**|month|Byte     | Mirror   | Read    | month in BCD     |
|**0x06**|year|Byte     | Mirror   | Read    | year in BCD      |

## 0x6B -\> UPS PIco Module Commands

### 0x6B Variable Table

| **Address** | **Name**        | **Size** | **Type** | **R/W** | **Explanation**|
|:---:|:----:|:---:|:---:|:---:|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------:|
|**0x00**|pico_state|Byte|Common|R/W|**Write: 0xcc** – Unconditional File Safe Shutdown and (and Power OFF when battery powered) **Write: 0xdd** - then restore factory defaults Will stay in the values of 0xdd until factory defaults restored, and then will be set to 0x00 **Write: 0xee** - Reset the UPS PIco CPU, it cause start-up values i.e. RTC will be set to 01/01/2000 **Write:** 0xff - Call the UPS PIco Bootloader, **Orange** Led will be light. Recover from this state can be done **only** by pressing the RST button, new firmware upload or automatically after 16 seconds if nothing happen. All interrupts are disabled during this procedure. It should be used with RPi Uploading firmware script. Use it very carefully and only when is needed – when firmware uploading. Do not play with it; this is not toy functionality. **Powering of the pair UPS PIco+RPi must be done via RPi micro USB socket during boot loading process due to following UPS PIco Resets after firmware uploading or when returning from this mode.**  **Due to required protection for the RPi from the unconditional reset (files corruption), it is not possible to enter to this mode when system is powered in a different way than in RPI Powering Mode.**|
|**0x01**|bat_run_time|Byte|Common|R/W|**On Battery Powering Running Time when cable power loses or not exist. After that time a File Safe Shut Down Procedure will be executed and System will be shut downed without restart. Battery power will be disconnected. System is in sleep mode (LPR) and RTC is running. If Raspberry Pi cable power returns again system will be start automatically.**  **If during the sleep mode (LPR) the F button will be pressed for longer time than 2 seconds (with battery or cable powering) Raspberry Pi will re-start again.**  **Value of 0xff (255) disable this timer, and system will be running on battery powering until battery discharge to 3.4V for LP battery and 2.8V fro LF Battery type. Factory default value is 60 seconds Value higher than 15 seconds are only accepted Each number represent 1 minute of Battery Running. Default Value is 0, and the highest Value is 0xFE. If user will enter i.e. 2, the Battery Running time will be 60 seconds + 2 x 60 seconds = 180 seconds. After that time system will be shutdown. If user after that will press again F button system will restart and run for 180 seconds again and then shutdown. Read:** Anytime, Return actual **fssd\_timeout** value **Write:** 0x00 – 0xFF **Any change on this register will cause immediate writing of the new value to the PIco EEPROM**|
|**0x09**|User LED Orange|Byte|Common|R/W|**User LED Orange ON - Write:** 0x01 **User LED Orange OFF - Write:** 0x00|
|**0x0A**|User LED Green|Byte|Common|R/W|**User LED Green ON - Write:** 0x01 **User LED Green OFF - Write:** 0x00|
|**0x0B**|User LED Blue|Byte|Common|R/W|**User LED Blue ON - Write:** 0x01 **User LED Blue OFF - Write:** 0x00|
|**0x0C**|brelay|Byte|Common|R/W|**Zero Power Bi Stable Relay**  **Write:** 0x01 Set **Write:** 0x01 Reset|
|**0x0D**|bmode|Byte|Common|R/W|**Integrated Sounder Mode Read:** Anytime, Return actual **bmode** value **Write:** 0x00 – Unconditional Disable the Sounder **Write:** 0x01 – Unconditional Enable the Sounder|
|**0x0E**|bfreq|Word|Common|R/W| **Frequency of sound in Hz**|
|**0x10**|bdur|Byte|Common|R/W| **Duration of sound in 10th of ms (10 = 100 ms)**|
|**0x11**|fmode|Byte|Common|R/W| **Integrated Fan Running Mode Read:** Anytime, Return actual **fmode** value **Write:** 0x00 – Unconditional Disable the FAN with selected speed from the **fspeed Write:** 0x01 – Unconditional Enable the FAN FAN with selected speed from the **fspeed** When UPS PIco is going down to the LPR mode, the FAN is automatically disabled, and enabled again when the UPS PIco returns to normal work|
|**0x12**|fspeed|Byte|Common|R/W|**Integrated Fan Speed Read:** Anytime, Return actual **fspeed** value **Write:** 00 – Selected speed when ON is 0% (not running) **Write:** 100 – Selected speed when ON is 100% (full speed running) **Any other (0-100) number is allowed and means % of speed and current consumption**|
|**0x13**|fstat|Byte|Mirror|Read| **Read:** Anytime, Return actual **if FAN** is actually running or not (for remote users)|

## **Events Triggered RTC Based System Actions Scheduler**

**Not Unlocked in the firmware yet**

## 0x6c -\> Start Time Stamp

**Not Unlocked in the firmware yet**

| **Address** | **Name** | **Size** | **Type** | **R/W** | **Explanation**                                              |
|:---:|:----:|:---:|:---:|:---:|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------:|
| **0x00**    | active   | Byte     | Common   | R/W     | Activation Stamp 0x00 not active(Start), 0xff active (Start) |
| **0x01**    | minute   | Byte     | Common   | R/W     | Starting Minute of hour in BCD - 2 digits (0-59) i.e. 22     |
| **0x02**    | hour     | Byte     | Common   | R/W     | Starting Hour of the Day in BCD - 2 digits (0-23) i.e. 22    |
| **0x03**    | mday     | Byte     | Common   | R/W     | Starting Day of the Month in BCD - 2 digits (1-31) i.e. 22   |
| **0x04**    | month    | Byte     | Common   | R/W     | Starting Month in BCD - 2 digits (1-12) i.e. 12              |
| **0x05**    | year     | Byte     | Common   | R/W     | Starting Year in BCD - 2 digits (0-99) i.e. 16               |

##0x6d -\> Running Time Stamp

| **Address**       | **Name**      | **Size** | **Type** | **R/W** | **Explanation**|
|:---:|:----:|:---:|:---:|:---:|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------:|
| **0** or **0x00** | D\_repetition | Byte     | Common   | R/W     | Days repetition in BCD 2 digits (0-99) every XX days: 00 – not repeated (only once if all repetitions are 0) 1-99 – every 1-99 days i.e. 7 means every week (i.e. every Monday) i.e. 10 means every 10 days i.e. 1 means every day |
| **1** or **0x01** | H\_repetition | Byte     | Common   | R/W     | In BCD 2 digits (0-23) every XX days: 00 – not repeated (only once if all repetitions are 0) 1-23 – every 1-23 hours i.e. 7 means every 7 hours                                                                                    |
| **2** or **0x02** | M\_repetition | Byte     | Common   | R/W     | In BCD 2 digits (1-59) every XX minutes: 00 – not repeated (only once if all repetitions are 0) 1-59 – every 1-59 minutes i.e. 7 means every 7 minutes                                                                             |
| **3** or **0x03** | H\_Duration   | Byte     | Common   | R/W     | In BCD 2 digits hours 1-24 hours                                                                                                                                                                                                   |
| **4** or **0x04** | M\_Duration   | Byte     | Common   | R/W     | In BCD 2 digits minutes 0-59                                                                                                                                                                                                       |

0x6e -\> Events Stamp (NOT implemented yet)
-------------------------------------------

| **Address** | **Name** | **Size** | **Type** | **R/W** | **Explanation** |
|:---:|:----:|:---:|:---:|:---:|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------:|
|             |          |          |          |         |                 |

0x6f -\> Actions Stamp (NOT implemented yet)
--------------------------------------------

Currently Implemented only Power Up System – permanently selected.

Future implementation: FAN, Charger, Relay

| **Address** | **Name** | **Size** | **Type** | **R/W** | **Explanation** |
|:---:|:----:|:---:|:---:|:---:|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------:|
|             |          |          |          |         |                 |
