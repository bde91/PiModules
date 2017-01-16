# UPS PIco Fan Control

There are currently 5 fan speeds available:

0 = Off<br />
25%<br />
50%<br />
75%<br />
100% 

To set the fan speed make sure you set the fan **OFF** first:

    sudo i2cset -y 1 0x6b 0x11 0

Once the fan has been set to **OFF**, you can then change the fan speed, in this example 50%:

    sudo i2cset -y 1 0x6b 0x12 50

With the new fan speed set, you can then turn the fan **ON**:

    sudo i2cset -y 1 0x6b 0x11 1