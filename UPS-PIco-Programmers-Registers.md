# Editing UPS PIco Programmers Registers

## Downloads

[28.03.2017 Register List](https://www.modmypi.com/download/pimodules/_28_03_2017-register-list.docx)

The Peripherals I2C Control, "The PICo Interface", is an implementation of I2C interface adapted for control of the peripherals connected to the Raspberry Pi via the command line or through programming language.  By using simple commands, control of UPS PIco peripherals is made extremely simple. Control at programming language level is also possible and easy. The core concept of the PICo interface is that all peripheral device control and data exchange between it and the Raspberry Pi variables are common for the I2C interface and any connected peripherals. Therefore any changes by either party, Raspberry Pi or the peripheral, causes immediate update and action.

Two types of variables are available:
* Common - where data is stored in the same place and any change on it will cause action on the UPS PIco Module
* Mirror - where a copy of data is stored on internal variables of the UPS PIco HV3.0 Module. They are protected, so changes on it will not impact the UPS PIco HV3.0 Module functionality and will be only be overwritten when the UPS PIco HV3.0 Module recognised changes on them.

Variables can be accessed using the [i2cget](https://linux.die.net/man/8/i2cget) (when reading the variable) and [i2cset](https://linux.die.net/man/8/i2cset) (when writing to the variable) commands from the Raspberry Pi command line. Each command follows a similar command, using i2cget or i2cset depending on whether you want to read or write:

    sudo i2cget -y 1 VARIABLE ADDRESS COMMAND

For example, when using the 0x69 Variable:

To read the powering mode: 1 or 2

    sudo i2cget -y 1 0x69 0x00 b

To read the battery level Battery Level value in 10th of mili volts

    sudo i2cget -y 1 0x69 0x08 w
