# UPS PIco Terminal Block

The UPS PIco HV3.0 Terminal Blocks PCB is an advanced Terminal Blocks PCB that adds a wealth of extra functionality and development features to the innovative UPS PIco HV3.0! 

![](https://www.modmypi.com/image/data/git/ups-pico/pico-terminal-block-6.png)

The following listed features are offered by the UPS PIco HV3.0 Terminal Blocks PCB:

* Terminal Block Connectivity on Independent from Raspberry Pi, and battery backed-up 3.3V 200mA supply (available also when Raspberry Pi is not powered)
* Terminal Block Connectivity on ESD protected 1-wire interface
* Terminal Block Connectivity on Independent from Raspberry Pi and battery backed-up 5V source 750 mA (available also when Raspberry Pi is not powered)
* 12V RS232 Interface Level Converter connectable to the Raspberry Pi Primary Serial Port or Independent Secondary Serial Port offered by UPS PIco HV3.0A with Terminal Block Connectivity
* Terminal Block Connectivity on Auxiliary interface to the bi-stable (zero power) Relay offered by the UPS PIco HV3.0A
* Terminal Block Connectivity on Optical Isolated Interface – readable as digital or analog input offered by the UPS PIco HV3.0A
* Terminal Block Connectivity on ESD Protected 12 bit A/D converters pre-scaled to: 5V, 15V and 30V (user selectable) accessed by I2C on Raspberry Pi 
* Voltage Followed and scaled of 0 - 4.8V A/D with Terminal Block Connectivity

![](https://www.modmypi.com/image/data/git/ups-pico/pico-terminal-block-1.png)

### What is a Voltage Follower?

![](https://www.modmypi.com/image/data/git/ups-pico/pico-terminal-block-2.png)

A voltage follower (also called a unity-gain amplifier, a buffer amplifier, and an isolation amplifier) is a op-amp circuit which has a voltage gain of 1.

This means that the op amp does not provide any amplification to the signal. The reason it is called a voltage follower is because the output voltage directly follows the input voltage, meaning the output voltage is the same as the input voltage. Thus, for example, if 10V goes into the op amp as input, 10V comes out as output. A voltage follower acts as a buffer, providing no amplification or attenuation to the signal. 

![](https://www.modmypi.com/image/data/git/ups-pico/pico-terminal-block-3.png)

### What is the Purpose of a Voltage Follower?

One may ask then, what is the purpose of a voltage follower? Since it outputs the same signal it inputs, what is its purpose in a circuit? This will now be explained.

An op amp circuit is a circuit with very high input impedance. This high input impedance is the reason voltage followers are used. This will now be explained. 

**Voltage Followers Draw Very Little Current**

When a circuit has a very high input impedance, very little current is drawn from the circuit. If you know ohm's law, you know that current, I=V/R. Thus, the greater the resistance, the less current is drawn from a power source. Thus, the power of the circuit isn't affected when current is feeding a high impedance load.

Let's look at both illustrations below. The below circuit is a circuit in which a power source feeds a low-impedance load. 

![](https://www.modmypi.com/image/data/git/ups-pico/pico-terminal-block-4.png)

In this circuit above, the load demands and draws a huge amount of current, because the load is low impedance. According to ohm's law, again, current, I=V/R. If a load has very low resistance, it draws huge amounts of current. This causes huge amounts of power to be drawn from the power source and, because of this, causes high disturbances and use of the power source powering the load.

Now let's look at the circuit below, connected to an op-amp voltage follower:

![](https://www.modmypi.com/image/data/git/ups-pico/pico-terminal-block-5.png)

This circuit above now draws very little current from the power source above. Because the op amp has such high impedance, it draws very little current. And because an op amp that has no feedback resistors gives the same output, the circuit outputs the same signal that is fed in.
This is one of the reasons voltage followers are used. They draw very little current, not disturbing the original circuit, and give the same voltage signal as output. They act as isolation buffers, isolating a circuit so that the power of the circuit is disturbed very little. 

**Voltage Followers Consume Practically All of the Voltage from a Voltage Divider Circuit**

So current, as explained above, is one of the reasons voltage followers are used. They simply don't draw a lot of current, so they do not load down the power source.

Another reason voltage followers are used is because of voltage dividers. This again deals with ohm's law. According to ohm's law, voltage= current x resistance (V=IR).

In a circuit, voltage divides up or is allocated according to the resistance or impedance of components.

Because an op amp has a very high input impedance, the majority of voltage will fall across ut, since it's so high impedance. So it's very valuable when used in a voltage divider because it guarantees that it will receive the majority of voltage if placed in a voltage divider circuit.

This will now be illustrated so you can see.

So let's say we have a circuit shown below which represents a voltage divider with a load attached to the output. 
