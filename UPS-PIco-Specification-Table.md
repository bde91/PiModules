# UPS PIco Specification Table

|Model|UPS PIco HV3.0 A Stack 450|UPS PIco HV3.0 A Stack 450 Plus|UPS PIco HV3.0 A Top End 450|
|:-------------------------------:|:-------------------------------:|:-------------------------------:|:-------------------------------:|
|**Compatibility Features**||||
|Raspberry Pi® System Compatibility|Raspberry Pi A+, B+, 2, 3 & Zero|Raspberry Pi A+, B+, 2, 3 & Zero|Raspberry Pi A+, B+, 2, 3 & Zero|
|Case Compatibility|PiModules PIco Case <br> ModMyPi Cases|PiModules PIco Case <br> ModMyPi Cases|Official RPi Case  <br>  PiModules PIco Case <br> ModMyPi Cases <br> Compact HAT Header|
|**GPIO Usage**| | | |
| Permanent use of I2C (User selectable addresses)|GND, 5V, SDA0, SCL0  <br> I2C Addresses: 68 69 6a 6b 6c <br> 6d 6e 6ff|GND, 5V, SDA0, SCL0  <br> I2C Addresses: 68 69 6a 6b 6c <br> 6d 6e 6ff|GND, 5V, SDA0, SCL0  <br> I2C Addresses: 68 69 6a 6b 6c <br> 6d 6e 6ff|
|Selectable use of Raspberry Pi® RS232|TXD0, RXD0|TXD0, RXD0|TXD0, RXD0|
|Selectable use of Raspberry Pi® GPIO|GPIO_GEN22: Pulse Train <br> GPIO_GEN27: Shutdown <br> GPIO_GEN18: IR Receiver <br> GPIO_GEN4: 1-Wire|GPIO_GEN22: Pulse Train <br> GPIO_GEN27: Shutdown <br> GPIO_GEN18: IR Receiver <br> GPIO_GEN4: 1-Wire|GPIO_GEN22: Pulse Train <br> GPIO_GEN27: Shutdown <br> GPIO_GEN18: IR Receiver <br> GPIO_GEN4: 1-Wire|
|**Battery and Charging** | | | |
|Charging Rate|Continuous @ 256 mAh|Automatic Dynamic Power Tracing <br> Charging Current: 50mA – 1A <br> (Triggered by voltage changes on the GPIO or External Source)|Continuous @ 256 mAh|
|Charging Mode |Automatically Selected : Full Charging Cycle & Trickle Charging|Automatically Selected : Full Charging Cycle & Trickle Charging|Automatically Selected : Full Charging Cycle & Trickle Charging|
|Battery Protection |On board cut-off protection system: thermal, over-charge or over-discharge|On board cut-off protection system: thermal, over-charge or over-discharge|On board cut-off protection system: thermal, over-charge or over-discharge|
|Battery Electrical Isolation System|Isolated until initial boot|Isolated until initial boot|Isolated until initial boot|
|System Battery Backup Output|5V 2.5A current continuous supply to Raspberry Pi via GPIO Pins|5V 2.5A current continuous supply to Raspberry Pi via GPIO Pins|5V 2.5A current continuous supply to Raspberry Pi via GPIO Pins|
|Auxiliary 5V Battery Backed Supply on PIco I/O Pins|5V @ 750 mA continuous supply on PIco I/O Pin. <br>Able to supply auxiliary devices with Raspberry Pi disconnected.<br>(Total system current should not exceed 3A)|5V @ 750 mA continuous supply on PIco I/O Pin. <br>Able to supply auxiliary devices with Raspberry Pi disconnected.<br>(Total system current should not exceed 3A)|5V @ 750 mA continuous supply on PIco I/O Pin. <br>Able to supply auxiliary devices with Raspberry Pi disconnected.<br>(Total system current should not exceed 3A)|
|**Battery Back-up Type**| | | |
|UPS| | | |
|Powering Monitoring Point| | | |
| | | | |
| | | | |
| | | | |
| | | | |

## Battery Options

|Battery Options|UPS PIco HV3.0 A Stack 450|UPS PIco HV3.0 A Stack 450 Plus|UPS PIco HV3.0 A Top End 450|
|:---:|:---:|:---:|:---:|
|**Standard**||||