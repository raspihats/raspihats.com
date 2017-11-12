---
layout: product
title: DI6acDQ6rly I2C-HAT
category: I2C-HAT
images: images/products/i2c-hats/di6acdq6rly
price: €40.00
relation_rank: 3
short_description: 6 isolated digital input channels and 6 relay output channels Raspberry Pi add-on board
features: | 
    * 6 isolated digital input channels
    * Source and sink type for digital input channels
    * Internal 32-bit counters for all digital input channels
    * 6 relay output channels(5A@250VAC)
    * Configurable relay PowerOnValue
    * Configurable relay SafetyValue
    * Dual watchdog(system and communication)
    * Form A power relay
    * 2000 VAC isolation voltage
    * Temperature operating range: -25 ~ +75°C
    * Stackable, up to 16x
badges:
    - name : python
      link : https://pypi.python.org/pypi/raspihats
    - name : node-js 
      link : https://www.npmjs.com/package/raspihats
    - name : node-red
      link : https://www.npmjs.com/package/node-red-contrib-raspihats
    - name : homeassistant
      link : https://home-assistant.io/components/raspihats
permalink: /products/i2c-hats/di6acdq6rly
---


### Description

The DI6acDQ6rly I2C-HAT is a 6 digital input channels and 6 relay Raspberry Pi add-on board that uses the I2C bus for communication with Raspberry Pi. The DI6acDQ6rly offers 6 sink/source isolated digital input channels and 6 Form A power relay output channels. The input channels can be used as edge counters, every input channel has an two 32-bit counters attached, one for counting rising edges and the other for counting falling edges. The DI6acDQ6rly also has 6 LED indicators for digital inputs status monitoring and 6 LED indicators for power relay outputs status monitoring.

Users can stack up to 16x DI6acDQ6rly I2C-HATs on one Raspberry Pi. Make sure every DI6acDQ6rly from the stack has a unique I2C bus address. Setting the address value is accomplished using the on board I2C address jumpers.

### Power Consumption

This type of HAT consumes a little more power than other types, check specs for power consumption. The reason for the power consumption is the high number of relays. Be careful when stacking multiple HATs that have relays in general.

### Specs

|:------------------------|:-----------------------------------------------------------------------------|
| **General**             |                                                                              |
| Power Consumption       | 0.75W(150mA@5V) max.                                                         |
| Voltage Supply          | 5V                                                                           |
| Operating Temperature   | -25 to 75°C                                                                  |
| Watchdog Timer          | System and Communication                                                     |
| **Digital Inputs**      |                                                                              |
| Digital Input Channels  | 6                                                                            |
| Signal Type             | Sink, Source, isolated channels with common ground or power                  |
| On Voltage Level        | +3 to +30V                                                                   |
| Off Voltage Level       | +1V max.                                                                     |
| Counter Channels        | 12(6rising & 6 falling), 32-bit, Max. Input Frequency : 100Hz, Min. Pulse Width : 5ms |
| Isolation Voltage       | 2000 VAC                                                                     |
| Input Resistance        | 5.6K                                                                         |
| **Relay Outputs**       |                                                                              |
| Relay Channels          | 6                                                                            |
| Relay Type              | Form A relay SPST (N.O.)                                                     |
| Contact Rating          | 5A @ 250VAC/30VDC                                                            |
| Breakdown Voltage       | 2000 VAC                                                                     |
| Operate Time            | 10ms                                                                         |
| Release Time            | 5ms                                                                          |

### Connectors

![connectors]({{site.baseurl}}/{{page.images}}/connectors.svg "DI6acDQ6rly I2C-HAT connectors")

The DI6acDQ6rly I2C-HAT has 2 connectors(8 pin and 12 pin, 3.81mm pitch, detachable screw terminal). 

The first connector(8 pin) is used by the 6 Digital Input channels, it has 6 Digital Input pins and 1 Common pin. Every input channel uses 2 pins:
 1. Ix, where x is the channel index, range [0..5]
 2. COM

The second connector(12 pin) is used by the 6 Relay Output channels. Every Relay Output channel uses 2 pins:

 1. NOx – NormalOpen
 2. COMx – Common
where x is the channel index, range is [0..5]

For details about wiring diagrams check the Digital Inputs Sink/Source Types and Relay Outputs in the [Application Wiring post][application-wiring]

[application-wiring]: {{site.baseurl}}/i2c-hat/2016/02/21/application-wiring.html