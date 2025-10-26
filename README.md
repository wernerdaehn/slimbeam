# SlimBeam of NOHRD

The SlimBeam Cable Machine has all the sensors to measure the pull distance and the lifted weigth built in already, so adding a ESP32 to broadcast the values wirelessly is pretty easy. Even the sensor- and power-cables can be reused.

## Partlist

 - 1x [Powersupply](https://www.amazon.de/dp/B00MUI7ROW): 5V DC, 4.0mm x 1.7mm plug, the same as the Sony PSP is using.
 - 1x [Micro-MaTch 4pin header](https://www.conrad.at/de/p/te-connectivity-stiftleiste-standard-micro-match-polzahl-gesamt-6-rastermass-1-27-mm-7-215083-6-1-st-747917.html) (male) 1.27mm, PartNr 7-215083-4
 - 1x [Micro-MaTch 6pin header](https://www.conrad.at/de/p/te-connectivity-stiftleiste-standard-micro-match-polzahl-gesamt-6-rastermass-1-27-mm-7-215083-6-1-st-747917.html) (male) 1.27mm, PartNr 7-215083-6
 - 1x Ribbon cable 6pins, 0.6m
 - 1x ESP32 MiniKit or similar; no headers; rather on the small side

One the MCU no pin headers have been used and the cables are soldered directly to the MCU.

Note: Buy more Micro-MaTch headers. I broke one of each when crimping to the cable. They are tiny and brittle.

## Pins

For the weight measurements, two AtmelQT1070, with 7 sensors each, are used and connected via two separate I²C ports. The cable to the MCU is built in already.
```
 1 GND
 2 SCL1
 3 RESET
 4 SDA1
 5 VDD
 6 SCL2
 7 N/C
 8 SDA2
```

The distance sensor is a rotary encoder for the left and right pully each. Both are connected to the 6pin ribbon cable, the one sensor has the 6pin header, the other the 4pin header.

```
 1 VDD
 2 GND
 3 Sig R1
 4 Sig R2
 5 Sig L1
 6 Sig L2
```

The MCU is powered by the 5V VCC, the sensors get the 3.3V power from the MCU.

```
 1 GND
 2 26 (SCL1)
 3 34 (RESET)
 4 18 (SDA1)
 5 3V3
 6 19 (SCL2)
 7 NC
 8 23 (SDA2)

 1 3V3
 2 GND
 3 16 (Sig R1)
 4 17 (Sig R2)
 5 21 (Sig L1)
 6 22 (Sig L2)

 1 5V red wire (VCC)
 2 GND black wire (GND)
```




