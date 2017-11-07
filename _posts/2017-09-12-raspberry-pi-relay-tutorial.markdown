---
layout: post
title:  "Raspberry Pi relay tutorial"
date:   2017-09-12 14:14:02 +0300
categories: i2c-hat usage
---

## INTRO

I’m writing this tutorial to highlight the advantages of using the [`DQ10rly I2C-HAT`][dq10rly], a relay board specifically designed as an add-on for Raspberry Pi, rather than using a generic relay board.

Advantages:
  * easy install, just mount [`DQ10rly I2C-HAT`][dq10rly] on top of Raspberry Pi using the [`mounting kit`][mounting-kit], no wires required
  * stackable up to 16x, use the [`mounting kit extension`][mounting-kit-ext] to stack more [`DQ10rly's`][dq10rly] on the same Raspberry Pi, just like in this [`video`][stack-video]
  * the only GPIOs that are used are the I2C bus pins, pin 3(GPIO02) and pin 5(GPIO03), all the other GPIOs are free to use for other purposes.

Materials needed:
  1. Raspberry Pi
  2. DQ10rly I2C-HAT
  3. I2C-HAT mounting kit

  ![Alt]

[dq10rly]: https://raspihats.com/product/dq10rly-i2c-hat/
[mounting-kit]: https://raspihats.com/product/mounting-kit-i2c-hat/
[mounting-kit-ext]: https://raspihats.com/product/mounting-kit-extension-i2c-hat/
[stack-video]: https://www.youtube.com/watch?v=HTDh2RCGw3I
