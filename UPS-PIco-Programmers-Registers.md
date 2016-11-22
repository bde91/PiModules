The Peripherals I2C Control, "The PICo Interface", is an implementation of I2C interface adapted for control of the peripherals connected to the Raspberry Pi via the command line or through programming language.  By using simple commands, control of UPS PIco peripherals is made extremely simple. Control at programming language level is also possible and easy. The core concept of the PICo interface is that all peripheral device control and data exchange between it and the Raspberry Pi variables are common for the I2C interface and any connected peripherals. Therefore any changes by either party, Raspberry Pi or the peripheral, causes immediate update and action.

Two types of variables are available:
* Common - where data is stored in the same place and any change on it will cause action on the UPS PIco Module
* Mirror - where a copy of data is stored on internal variables of the UPS PIco HV3.0 Module. They are protected, so changes on it will not impact the UPS PIco HV3.0 Module functionality and will be only be overwritten when the UPS PIco HV3.0 Module recognised changes on them.

The following PICo addresses are assigned to the following entities:

## 0x69 ->UPS PIco HV3.0 Module Status Registers Specification

|Address|Name|Size|Type|R/W|Explanation|
|:---:|:----:|:---:|:---:|:---:|:---:|

