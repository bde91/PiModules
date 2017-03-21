# UPS PIco Firmware Update

### [Firmware Download](http://forum.modmypi.com/technical-support/ups-pico-firmware-update-troubleshooting-t1106.html)
### [Alternative Firmware Download](http://www.forum.pimodules.com/viewforum.php?f=25)

The UPS PiCo features an embedded serial bootloader which allows users to manually update the unit’s firmware via a dedicated python script.

Bootloader is small piece of firmware stored permanently in the micro controller flash memory of the UPS Pico, located in the special protected area. It can not be erased by user without dedicated hardware tools. In order to upload new firmware, an invocation of the bootloader routine is needed. It can be done manually or automatically if I2C-tools is running and installed. 

The bootloader functionality ensures that the UPS PIco is up-to-date, and allows users to report various changes that can be implemented on the user’s side. It is extremely useful functionality, and ensures that the product has longevity.
It is mandatory to have previously installed python and I2C-tools on the Raspberry Pi. You will install these during initial PiCo setup outlined previously in this document. Please install smbus support for python to enable additional functionality. Simply run the following command (with an internet connection):

    sudo apt-get install python-smbus

As the bootloader uses the Raspberry Pi Serial Port (RS232), it is mandatory to have it free on the Raspberry Pi (without any hardware occupying it). It is also important that you ensure that there is no software using it. As well If minicom has been used, please restart the Raspberry Pi, as minicom keeps the RS232 interface occupied.
The first task which is done by the UPS PIco after reset is to check if bootloader has been requested. If not, then the rest of the firmware runs. Otherwise, the UPS PIco lights the big RED LED and waits for the firmware upload from the Raspbeerry Pi.

There are two ways to invoke the bootloader mode and to upload the new firmware, automatic and manual.

## Firmware Update Prerequisite - Clear the UART

To update the firmware on the UPS PIco, the Raspberry Pi must have no access to UART. This requires Bluetooth and serial console to be disabled:

First disable Bluetooth by editing /boot/config.txt file:

    sudo nano /boot/config.txt

Then add the following line to the end of the file to disable Bluetooth:

    dtoverlay=pi3-disable-bt

Remember to save the file before exiting.

Do this to stop Bluetooth trying to use UART:

    sudo systemctl disable hciuart

Disable the serial console. Do this to stop the serial console on the UART:

    sudo systemctl stop serial-getty@ttyAMA0.service

To stop it from starting again when rebooted:

    sudo systemctl disable serial-getty@ttyAMA0.service

To re-enable it when you have finished (**ONLY DO THIS AFTER THE FIRMWARE UPDATE**):

    sudo systemctl enable serial-getty@ttyAMA0.service

To start it without rebooting (**ONLY DO THIS AFTER THE FIRMWARE UPDATE**):

    sudo systemctl start serial-getty@ttyAMA0.service

## Automatic Firmware Update

To update the firmware automatically you need to invoke the bootloader with the following commands:

    sudo i2cset -y 1 0x6b 0x00 0xff

The UPS_PIco_HV3.0_main.hex should be replaced with the name of the last firmware update, or the firmware you wish to use.
When firmware starts the upload procedure, the Orange User LED will lit, and then when firmware starts uploading the User Blue Led will Lit and UPS LED will be blinking.

    sudo python 9600_picofuHV3.0.py -v -f UPS_PIco_HV3.0_main.hex

Once complete the system with output ALL Done :) Ready to go. . .

We would recommend that you now shutdown your Pi and UPS PiCo completely in order to ensure that all changes are integrated. Once you’ve rebooted your system, you can check the UPS PiCo firmware version using the following command:

    sudo i2cget -y 1 0x69 0x26

In this case the system should output 0xXX, signifying that the firmware has updated correctly.

## Manual Firmware Update

The UPS PiCo has the ability to invoke the bootloader manually, via the on board buttons. You can do this instead of using the automatic initiation outlined above.

The following procedure needs to be followed:

* Press and hold the UR button
* Continue to hold the UR button, and press and hold the F button.
* Release the UR button, but keep holding the F button
* Release the F button
* The User Orange LED will light, and system will be able to receive the firmware update

Then write the following command on the Raspberry Pi command line:

The UPS_PIco_HV3.0_main.hex should be replaced with the name of the last firmware update, or the firmware you wish to use.
When firmware starts the upload procedure, the Orange User LED will lit, and then when firmware starts uploading the User Blue Led will Lit and UPS LED will be blinking.

    sudo python 9600_picofuHV3.0.py -v -f UPS_PIco_HV3.0_main.hex

If within 16 second after bootloader initiation the firmware will be not initiated the UPS PIco HV3.0 will be reset to normal working conditions by internal Watch Dog mechanism. This has been implemented for security reasons, if firmware is uploaded remotely. 