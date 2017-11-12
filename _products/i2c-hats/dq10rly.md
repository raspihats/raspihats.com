---
layout: product
title: DQ10rly I2C-HAT
category: I2C-HAT
images: images/products/i2c-hats/dq10rly
price: €43.00
relation_rank: 3
short_description: 10 relay output channels Raspberry Pi add-on board
features: |
    * 10 relay output channels(5A@250VAC)
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
permalink: /products/i2c-hats/dq10rly
---


### Description

The DQ10rly I2C-HAT is a 10 relay Raspberry Pi add-on board that uses the I2C bus for communication with Raspberry Pi. The DQ10rly offers 10 channel Form A power relay outputs, it also has 10 LED indicators for power relay output state monitoring.

Users can stack up to 16x DQ10rly I2C-HATs on one Raspberry Pi. Make sure every DQ10rly from the stack has a unique I2C bus address. Setting the address value is accomplished using the on board I2C address jumpers.

### Power Consumption

This type of HAT consumes a little more power than other types, check specs for power consumption. The reason for the power consumption is the high number of relays. Be careful when stacking multiple HATs that have relays in general.

### Specs

|:------------------------|:-----------------------------------------------------------------------------|
| **General**             |                                                                              |
| Power Consumption       | 1.5W(300mA@5v) max.                                                          |
| Voltage Supply          | 5V                                                                           |
| Operating Temperature   | -25 to 75°C                                                                  |
| Watchdog Timer          | System and Communication                                                     |
| **Relay Outputs**       |                                                                              |
| Relay Channels          | 10                                                                           |
| Relay Type              | Form A relay SPST (N.O.)                                                     |
| Contact Rating          | 5A @ 250VAC/30VDC                                                            |
| Breakdown Voltage       | 2000 VAC                                                                     |
| Operate Time            | 10ms                                                                         |
| Release Time            | 5ms                                                                          |

### Connectors

![connectors]({{site.baseurl}}/{{page.images}}/connectors.svg "DQ10rly I2C-HAT connectors")

The DI6acDQ6rly I2C-HAT has 2 connectors(each has 10 pin, 3.81mm pitch, detachable screw terminal). 

First connector(10 pin) is used by the first 5 Relay Output channels, the second connector(10 pin) is used by the remaining 5 Relay Output channels. Every Relay Output channel uses 2 pins:

 1. NOx – NormalOpen
 2. COMx – Common
where x is the channel index, range is [0..9]

For details about wiring diagrams check the Relay Outputs in the [Application Wiring post][application-wiring]


[application-wiring]: {{site.baseurl}}/i2c-hat/2016/02/21/application-wiring.html