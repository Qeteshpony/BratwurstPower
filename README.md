# BratwurstPower

[![CI](https://github.com/Qeteshpony/BratwurstPower/actions/workflows/ci.yml/badge.svg?branch=main)](https://github.com/Qeteshpony/BratwurstPower/actions/workflows/ci.yml)

![3D Render](https://qeteshpony.github.io/BratwurstPower/3D/BratwurstPower-3D_top.png)

[Hardware Documentation](https://qeteshpony.github.io/BratwurstPower)

A power supply for a complete, Raspberry Pi based ADS-B Receiver Setup with independent power rails for the different components.

We sometimes face the problem that a normal Raspberry Pi power supply does not deliver enough power for the Raspi itself, the SDR Stick and possible other components like a display or even an SSD. 

This board can be mounted underneath a Raspberry Pi and deliver stable 5.x V with up to 3 A to it. 

In addition to that it can supply two USB devices and another external device with also 5.x V and 3 A each, provided the input has enough power. 

Each outputs voltage can be calibrated from ~5.1 to ~5.5 V with a trimpot and the two USB outputs are passing USB2 signals from two USB-Mini connectors that can be hooked to the Raspberry Pi. If you need USB3, you can use an external Y-cable. 

There is an INA219 power monitor connected to each output with a 10mΩ shunt resistor to measure current and voltage. 

A PCA9557 I/O expander allows to switch off power to the USB-ports and the external power.

| Device  | I2C-Address |
|:----------|:----------|
| INA219 Raspi | 0x40   |
| INA219 USB1  | 0x41   |
| INA219 USB2  | 0x42   |
| INA219 EXT   | 0x43   |
| PCA9557      | 0x1F   |

| PCA9557 Pin | Function |
|:----------|:----------|
| IO0 | LED |
| IO1 | N/A |
| IO2 | N/A |
| IO3 | N/A |
| IO4 | N/A |
| IO5 | USB1 |
| IO6 | USB2 |
| IO7 | EXT |

