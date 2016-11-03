# UPS PIco Firmware Update

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

To re-enable it when you have finished updating firmware:

    sudo systemctl enable serial-getty@ttyAMA0.service

To start it without rebooting:

    sudo systemctl start serial-getty@ttyAMA0.service
