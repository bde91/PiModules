# UPS PIco Fan Kit Assembly

One of the addons available for the UPS PIco is the Fan Kit, containing both a fan and a TO92 temperature sensor. These instructions will guide you through the installation of the TO92 and fan.

A script is also available to automatically set fan speeds based on the temperature.

### Fan Kit Contents
![fan kit contents](https://www.modmypi.com/image/data/rpi-products/breakout-boards/modmypi/pico/wiki/fan_kit_contents.jpg)

**Step 1**
![fan header](https://www.modmypi.com/image/data/rpi-products/breakout-boards/modmypi/pico/wiki/fan-header-1.jpg)

Start by soldering the fan connector to the PIco PCB

![fan header](https://www.modmypi.com/image/data/rpi-products/breakout-boards/modmypi/pico/wiki/fan-header-2.jpg)

![fan header](https://www.modmypi.com/image/data/rpi-products/breakout-boards/modmypi/pico/wiki/fan-header-3.jpg)

**Step 2**
![to92](https://www.modmypi.com/image/data/rpi-products/breakout-boards/modmypi/pico/wiki/to92-1.jpg)

Next, we'll solder on the TO92 Temperature Sensor.

Start by inserting the TO92 into the 3 through holes on the PCB.

![to92](https://www.modmypi.com/image/data/rpi-products/breakout-boards/modmypi/pico/wiki/to92-2.jpg)

Flip the PIco over and bend the legs out slightly to hold the TO92 in place.

![to92](https://www.modmypi.com/image/data/rpi-products/breakout-boards/modmypi/pico/wiki/to92-3.jpg)

Solder and trim the legs.

![to92](https://www.modmypi.com/image/data/rpi-products/breakout-boards/modmypi/pico/wiki/to92-4.jpg)

**Step 3**
![fan](https://www.modmypi.com/image/data/rpi-products/breakout-boards/modmypi/pico/wiki/fan-1.jpg)

Now its time to add the fan.

Start by pressing the four studs through the fan mounting holes, from the top of the PIco

![fan](https://www.modmypi.com/image/data/rpi-products/breakout-boards/modmypi/pico/wiki/fan-2.jpg)

Flip the PIco over.

![fan](https://www.modmypi.com/image/data/rpi-products/breakout-boards/modmypi/pico/wiki/fan-3.jpg)

Add a spacer to each of the studs.

![fan](https://www.modmypi.com/image/data/rpi-products/breakout-boards/modmypi/pico/wiki/fan-4.jpg)

Finally, add the fan and connect the fan wire up. The fan blows air towards the label on the fan, we decided to have this facing down the blow cold air directly onto the SoC of the Pi. It's up to you which way round you put the fan.

![fan](https://www.modmypi.com/image/data/rpi-products/breakout-boards/modmypi/pico/wiki/fan-5.jpg)

## Temperature Controlled Fan Script

Included in this repository is a simple script to automatically adjust the speed of the fan based on the temperature reported from the TO92 sensor.

You can either just run the script when you want it or you can set it to run on boot!

To run the script manually, make sure you are in the scripts directory:

`cd /home/pi/PiModules/temp_fan`

Then run the script like any other python script:

`sudo python pico_HV3.0_temp_fan_v1.0.py`

If you want to make the script run on boot simply edit the rc.local file:

`sudo nano /etc/rc.local`

And add the following line, just before the exit 0:

`(sleep 10;python /home/pi/PiModules/temp_fan/pico_HV3.0_temp_fan_v1.0.py)&`