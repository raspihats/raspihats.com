---
layout: product
title: DI16ac I2C-HAT
category: I2C-HAT
images: images/products/i2c-hats/di16ac
price: €34
short_description: 16 isolated digital input channels Raspberry Pi add-on board
features: |
    * 16 isolated digital input channels
    * Source and sink type for digital input channels
    * Internal 32-bit counters for all digital input channels
    * 2000 VAC isolation voltage
    * Temperature operating range: -25 ~ +75°C
    * Stackable, up to 16x
permalink: /products/i2c-hats/di16ac
---


### Description

The DI16ac I2C-HAT is a 16 digital input channels Raspberry Pi add-on board that uses the I2C bus for communication with Raspberry Pi. It offers 16 isolated source/sink digital input channels. The input channels can be used to count edges, every input channel has two internal 32-bit counter attached, one for counting rising edges and the other for counting falling edges. The DI16ac also has 16 LED indicators for digital inputs status monitoring.

The wide operating input voltage of the digital inputs is perfect for most applications. The isolation protects your Raspberry Pi from the harsh external environment.
Users can stack up to 16x DI16ac I2C-HATs on one Raspberry Pi. Make sure every DI16ac from the stack has a unique I2C bus address. Setting the address value is accomplished using the on board I2C address jumpers.

### Specs

|:------------------------|:-----------------------------------------------------------------------------|
| **General**             |                                                                              |
| Power Consumption       | 0.25W(50mA@5V) max.                                                          |
| Voltage Supply          | 5V                                                                           |
| Operating Temperature   | -25 to 75°C                                                                  |
| Watchdog Timer          | System and Communication                                                     |
| **Digital Inputs**      |                                                                              |
| Digital Input Channels  | 16                                                                           |
| Signal Type             | Sink, Source, isolated channels with common ground or power                  |
| On Voltage Level        | +3 to +30V                                                                   |
| Off Voltage Level       | +1V max.                                                                     |
| Counter Channels        | 32(16 rising, 16 falling), 32-bit, Max. Input Frequency: 100Hz, Min. Pulse Width : 5ms |
| Isolation Voltage       | 2000 VAC                                                                     |
| Input Resistance        | 5.6K                                                                         |

## Connectors

![connectors]({{site.baseurl}}/{{page.images}}/connectors.svg "DI16ac I2C-HAT connectors")

The DI16ac I2C-HAT has 2 connectors(each has 10 pin, 3.81mm pitch, detachable screw terminal). Their pins are divided into 4 blocks, 2 blocks on each of the connectors. Every block has 5 pins, 4 Digital Input pins and 1 Common pin.

Every input channel uses 2 pins:
 1. Ix, where x is the channel index, range [0..15].
 2. COMy, where y is pin block index, range [0..3]

Input channels I0 to I3 use COM0, input channels I4 to I7 use COM1 and so on.

For details about wiring diagrams check the Digital Inputs Sink/Source Types in the Application Wiring post