---
layout: post
title:  Application Wiring
date:   2016-02-21 14:14:02 +0300
categories: I2C-HAT
---

In the following diagrams there are two sections:
  * External (wiring that should be used)
  * Internal (represents a simplified version of the on-board circuit)

## 1.Digital Inputs

### 1.1 Bi-directional opto-coupler input 

Wiring a button:

![di_button]({{site.baseurl}}/images/posts/di_button.svg "Wiring a button to a digital input")

You need an external power supply different from the one used by Raspberry Pi, in this way the input circuitry is isolated from Raspberry Pi. You could use the power supply from Raspberry Pi but the trade-off is losing the isolation(not recommended). The Button and DC Source can be interchanged.


## 2. Digital Outputs

### 2.1 Relay Outputs

The LOAD element in the following diagrams can be a motor, a light bulb, a heating element or something else.

Wiring a LOAD with a DC source:

![dq_rly_dc_source]({{site.baseurl}}/images/posts/dq_rly_dc_source.svg "Wiring a relay output")

The DC Source polarity doesn't matter from the relay output point of view, it can matter for the LOAD element. The positions of the LOAD and DC Source can be interchanged.

Wiring a LOAD with an AC source: 

![dq_rly_ac_source]({{site.baseurl}}/images/posts/dq_rly_ac_source.svg "Wiring a relay output")

The positions of the LOAD and AC Source can be interchanged.
