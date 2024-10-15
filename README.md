# BratwurstPower

[![CI](https://github.com/Qeteshpony/BratwurstPower/actions/workflows/ci.yml/badge.svg?branch=main)](https://github.com/Qeteshpony/BratwurstPower/actions/workflows/ci.yml)

![3D Render Top](https://qeteshpony.github.io/BratwurstPower/3D/BratwurstPower-3D_top.png)
![3D Render Bottom](https://qeteshpony.github.io/BratwurstPower/3D/BratwurstPower-3D_bottom.png)

[Hardware Documentation](https://qeteshpony.github.io/BratwurstPower)

### What's this?

A power supply for a complete, Raspberry Pi based ADS-B Receiver Setup with independent power rails for the different components.

We sometimes face the problem that a normal Raspberry Pi power supply does not deliver enough power for the Raspi itself, the SDR Stick and possible other components like a display or even an SSD. 

This board can be mounted underneath a Raspberry Pi and deliver stable 5.x V with up to 3 A to it. 

In addition to that it can supply two USB devices and another external device with also 5.x V and 3 A each, provided the input has enough power and the maximum input current does not surpass 5A. 

Each outputs voltage can be calibrated from ~5.06 to ~5.6 V with a trimpot and the two USB outputs are passing USB2 signals from two USB-C connectors that can be hooked up to the Raspberry Pi. If you need USB3, you can use an external Y-cable. 

## What else is on the board?

The onboard circuitry is powered by its own 3.3V LDO regulator which is fed by the power rail for the Raspberry Pi since that one is always running. The LDO can provide a maximum of 200mA to also power small external loads on the GPIO connector. 

There is an INA219 power monitor connected to the main input and each output with a 10mΩ shunt resistor to measure current and voltage. 

The onboard I2C bus is connected to all of the INA219 and a PCA9557

| Device  | I2C-Address |
|:--------|:------------|
| INA219 Raspi | 0x40   |
| INA219 USB1  | 0x41   |
| INA219 USB2  | 0x42   |
| INA219 EXT   | 0x43   |
| INA219 Main  | 0x44   |
| PCA9557      | 0x1F   |

The PCA9557 I/O expander allows to switch off power to the USB-ports and the external power. It also has an LED connected that can be used for showing a warning state or similar. The other 4 pins are broken out on a header.

| PCA9557 Pin | Function |
|:------------|:---------|
| IO0 | LED  |
| IO1 | GPIO 1 (Opt: Raspi EN) |
| IO2 | GPIO 2 |
| IO3 | GPIO 3 |
| IO4 | GPIO 4 |
| IO5 | USB2 EN |
| IO6 | USB1 EN |
| IO7 | EXT EN |

Each voltage channel has a solder jumper to force-enable it. The USB power rails are also enabled as soon as their input usb port gets connected to the Raspberry Pi. In addition to that, all three external power connections can be controlled by the PCA9557 and there is an optional connection through a solder jumper to even give control over the Raspberry Pi power supply in case the I2C components on this board are controlled externally e.g. by an ESP. 

### External connections and jumpers
| Designator | Function |
|:----------|:---------|
| IN | Main Power supply - can be powered with 7 to 17V DC with a maximum of 5A. Nominal Power: 12V. |
| Raspi | Power supply for the Raspberry Pi. This is the only port that is by default always on. |
| USB1/2 in | USB input for external connections. Connect these to the Raspberry pi with normal USB cables. |
| USB1/2 out | Powered USB output for external components, each with its own power supply. |
| EXT | Power supply for other external components, also independently powered. Needs to be enabled through its solder jumper or by the PCA9557. |
| 2x I2C | I2C connection to either the Raspberry Pi or an external controller. The 3.3V connection is just a path-through between the connectors. |
| OTG | Optional connector to access the Raspberry Pis USB-OTG functionality. |
| GPIO | Optional header to use the free pins of the PCA9557. Keep in mind that the onboard 3.3V LDO can not provide more than 200mA. |
| USB1/2 EN | Solder jumper to force-enable the USB power supplies in case you want to use them without a connection to the Raspberry Pi. |
| EXT EN | Solder jumper to enable the EXT power supply. |
| Raspi EN | Solder jumper to connect the EN pin if the Raspi power supply with IO1 of the PCA9557. This can be used to externally hard-reset the Raspberry Pi and should only be used when the board is controlled by an external controller like an ESP. |
| TP1 | Test point to measure the voltage on the Raspberry Pi power supply. |
| TP2 | Test point to measure the voltage on the USB1 power supply. |
| TP3 | Test point to measure the voltage on the USB2 power supply. |
| TP4 | Test point to measure the voltage on the EXT power supply. |
| RV1 | Calibration Potentiometer for the Raspberry Pi power supply. |
| RV2 | Calibration Potentiometer for the USB1 power supply. |
| RV3 | Calibration Potentiometer for the USB2 power supply. |
| RV4 | Calibration Potentiometer for the EXT power supply. |
