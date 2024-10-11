# BratwurstPower

[![CI](https://github.com/Qeteshpony/BratwurstPower/actions/workflows/ci.yml/badge.svg?branch=main)](https://github.com/Qeteshpony/BratwurstPower/actions/workflows/ci.yml)

![3D Render Top](https://qeteshpony.github.io/BratwurstPower/3D/BratwurstPower-3D_top.png)
![3D Render Bottom](https://qeteshpony.github.io/BratwurstPower/3D/BratwurstPower-3D_bottom.png)

[Hardware Documentation](https://qeteshpony.github.io/BratwurstPower)

A power supply for a complete, Raspberry Pi based ADS-B Receiver Setup with independent power rails for the different components.

We sometimes face the problem that a normal Raspberry Pi power supply does not deliver enough power for the Raspi itself, the SDR Stick and possible other components like a display or even an SSD. 

This board can be mounted underneath a Raspberry Pi and deliver stable 5.x V with up to 3 A to it. 

In addition to that it can supply two USB devices and another external device with also 5.x V and 3 A each, provided the input has enough power. 

Each outputs voltage can be calibrated from ~5.1 to ~5.5 V with a trimpot and the two USB outputs are passing USB2 signals from two USB-C connectors that can be hooked up to the Raspberry Pi. If you need USB3, you can use an external Y-cable. 

There is an INA219 power monitor connected to the main input and each output with a 10mΩ shunt resistor to measure current and voltage. 

| Device  | I2C-Address |
|:----------|:----------|
| INA219 Raspi | 0x40   |
| INA219 USB1  | 0x41   |
| INA219 USB2  | 0x42   |
| INA219 EXT   | 0x43   |
| INA219 Main  | 0x44   |
| PCA9557      | 0x1F   |

A PCA9557 I/O expander allows to switch off power to the USB-ports and the external power. It also has an LED connected that can be used for showing a warning state or similar. The other 4 pins are broken out on a header.

| PCA9557 Pin | Function |
|:----------|:----------|
| IO0 | LED |
| IO1 | PIN |
| IO2 | PIN |
| IO3 | PIN |
| IO4 | PIN |
| IO5 | USB2 |
| IO6 | USB1 |
| IO7 | EXT |

