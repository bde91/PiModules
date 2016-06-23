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
|UPS|UPS Standby Type, with Switchover time of 360 uS, during switching time the protected system is powered by auxiliary online power source for maximum 10mS, therefore no power gap on GPIO during switching time|UPS Standby Type, with Switchover time of 360 uS, during switching time the protected system is powered by auxiliary online power source for maximum 10mS, therefore no power gap on GPIO during switching time|UPS Standby Type, with Switchover time of 360 uS, during switching time the protected system is powered by auxiliary online power source for maximum 10mS, therefore no power gap on GPIO during switching time|
|Powering Monitoring Point|Raspberry Pi® GPIO 5V|Raspberry Pi® GPIO 5V|Raspberry Pi® GPIO 5V|
|UPS Activation Powering Triggers|GPIO 5V pins <=4.65V Proprietary Algorithm of Falling Power Peak Analysis|GPIO 5V pins <=4.65V Proprietary Algorithm of Falling Power Peak Analysis|GPIO 5V pins <=4.65V Proprietary Algorithm of Falling Power Peak Analysis|
|Cable Powering Reactivation|After 3s of continuously cable powering (without spikes)|After 3s of continuously cable powering (without spikes) on any cable power source (GPIO or External)|After 3s of continuously cable powering (without spikes)|
|Power Source|GPIO Pins 5V @ 2.5A|GPIO Pins 5V @ 2.5A <br> External Input 6VDC - 28VDC @ 3A Max|GPIO Pins 5V @ 2.5A|
|**HAT Compliance**| | | |
|HAT EEPROM|Simulated HAT EEPROM on uC memory|Simulated HAT EEPROM on uC memory|Simulated HAT EEPROM on uC memory|
|HAT Dimension|Compliant|Compliant|Compliant|
|**PIco I/O Interface**| | | |
|Independent from Raspberry Pi ® 3.3 V supply @200 mA|Yes|Yes|Yes|
|ESD Protected 1-wire interface|Yes|Yes|Yes|
|Independent from Raspberry Pi ® 5.0 V supply @750 mA with battery Back-up (raspberry Pi ® can be OFF when this power source is running)|Yes|Yes|Yes|
|12 Bit A/D converters ESD protected, pre-scaled to 5V, 15V and 30V with Sampling rate 100K SPS, buffered|Yes|Yes|Yes|
|3V3/5V0  RS232 Port that can be programmed as: primary Raspberry Pi® Port Secondary (independent from the Raspberry Pi®)|Yes|Yes|Yes|
|Optical Isolated Interface (readable as digital or analogue)|No|Yes|No|
|Primary 3 Pin Bi-stable (Zero Power) Relay Interface|Yes (Relay Supplied Separately)|Yes (Relay Supplied Separately)|Yes (Relay Supplied Separately)|
|Relay Rating - Resistive|0.5A 125 VAC or 1A 30 VDC|0.5A 125 VAC or 1A 30 VDC|0.5A 125 VAC or 1A 30 VDC|
|Relay Rating - Max Switching Current|2A|2A|2A|
|Relay Rating - Max Switching Voltage|125VAC, 110VDC|125VAC, 110VDC|125VAC, 110VDC|
|**PIco Terminals Block Extension PCB (Supplied Separately)**| | | |
|12 V RS232 converter attached to primary or secondary Serial Port|Yes (Optional)|Yes (Optional)|Yes (Optional)|
|Terminal Block on Each PIco I/O Interface listed above|Valid only for existing Interfaces|Yes|Valid only for existing Interfaces|
|**PIco Plus Terminal Block Standard Interface**| | | |
|DC in 6 – 28 V with Power Tracking|No|Yes|No|
|Secondary 3 Pin Bi-stable (Zero Power) Relay Interface|Optional if Relay Installed|Yes|Optional if Relay Installed|
|**Hardware User Interface**| | | |
|System LEDs Indicators|UPS, BAT, CHG, HOT, FAN|UPS, BAT, CHG, HOT, FAN|UPS, BAT, CHG, HOT, FAN|
|User LEDs Indicators|Blue, White, Red|Blue, White, Red|Blue, White, Red|
|System Keys|RPiR, UPSR, FSSD|RPiR, UPSR, FSSD|RPiR, UPSR, FSSD|
|User Programmable Keys|AKEY, BKEY, CKEY|AKEY, BKEY, CKEY|AKEY, BKEY, CKEY|
|Audio Interface|Electromagnetic Transducer, with programmable sound duration and frequency, able to play music|Electromagnetic Transducer, with programmable sound duration and frequency, able to play music|Electromagnetic Transducer, with programmable sound duration and frequency, able to play music|
|**Basic Features**| | | |
|Battery Backed Hardware Real Time Clock and Calendar|Yes|Yes|Yes|
|Bi-Stable (Zero Power) Relay|Yes (Optional)|Yes|Yes (Optional)|
|Automatic Active Cooling System (FAN)|Yes (Optional)|Yes (Optional)|Yes (Optional)|
|Automatic File Safe Shutdown Functionality|Yes|Yes|Yes|
|Raspberry Pi® Reset via POGO Pin |Yes|Yes|Yes|
|Automatic Restart on Power Return|Yes|Yes|Yes|
|Events Triggered RTCC Based System Actions Scheduler|Yes|Yes|Yes|
|Real Time Raspberry Pi® current measure|No|Yes|No|
|Real Time Battery Capacity Measure|No|Yes <br>(System Current Consumption)|No|
|Secondary Serial Port (based on software driver)|Yes (Future Update)|Yes (Future Update)|Yes (Future Update)|
|IR interface|Yes (IR Sold Separately)|Yes (IR Sold Separately)|Yes (IR Sold Separately)|
|Optimised design for a very low noise A/D operation|Yes|Yes|Yes|
|Optimised Ultra Low Power design for a long time Battery System Operation|Yes|Yes|Yes|
|XTEA Encryption |Yes|Yes|Yes|
|Extended Raspberry Pi® Watch-Dog (Still Alive)|Yes|Yes|Yes|
|System Monitoring|Battery Voltage, Raspberry Pi® Voltage, Temperature|Battery Voltage, Raspberry Pi® Voltage, External Voltage, Current Consumption by Raspberry Pi®, Temperature|Battery Voltage, Raspberry Pi® Voltage, Temperature|
|I2C PIco Programmer Interface |Yes|Yes|Yes|
|RS232 @command Interface on Primary and Secondary Serial Port|Yes|Yes|Yes|
|Bootloader for Live Firmware Update|Yes|Yes|Yes|
|PCB Specification|4 Layers <br>2 OZ Cupper, 6mils/6mils <br>Immersion Gold Plated <br>PB Free Bismuth based alloy assembly|4 Layers <br>2 OZ Cupper, 6mils/6mils <br>Immersion Gold Plated <br>PB Free Bismuth based alloy assembly|4 Layers <br>2 OZ Cupper, 6mils/6mils <br>Immersion Gold Plated <br>PB Free Bismuth based alloy assembly|

## Battery Options

|Battery Options|UPS PIco HV3.0 A Stack 450|UPS PIco HV3.0 A Stack 450 Plus|UPS PIco HV3.0 A Top End 450|
|:---:|:---:|:---:|:---:|
|**Standard**||||