---
layout: post
title:  I2C-HAT firmware update
date:   2016-02-17 12:04:02 +0300
categories: I2C-HAT
---

## STM32 integrated bootloader

All `I2C-HATs` are based on STM32 ARM chips which have the integrated STM32 I2C bootloader, this enables firmware update via I2C bus.

**IMPORTANT!!!** - Before fimware update:
  1. Disconnect everything that’s connected to board inputs/outputs.
  2. Make sure you have the right I2C clock stretching timeout value, check this [post][i2c-clkst-post].

## Download and install `stm32flash` on Raspberry Pi

`stm32flash` is the tool you need to update the firmware on the `I2C-HATs`.

Open a terminal on Raspberry Pi and go to the directory where you want to download `stm32flash`, type the following commands to download and install:

```
wget http://downloads.sourceforge.net/project/stm32flash/stm32flash-0.5.tar.gz
tar -zxvf stm32flash-0.5.tar.gz
cd stm32flash
make
sudo make install
```
## Enable the I2C-HAT bootloader

Install the `BOOT` jumper **before** powering up the `I2C-HAT` on which you wish the firmware to be updated, the I2C address for the bootloader is specified in the following table:

| I2C-HAT                        | ST Micro     | Bootloader I2C Address            |
|:-------------------------------|:-------------|----------------------------------:|
| [DI16ac][di16ac]               | STM32F042    | 0x3E                              |
| [DQ10rly][dq10rly]             | STM32F042    | 0x3E                              |
| [DI6acDQ6rly][di6acdq6rly]     | STM32F042    | 0x3E                              |
| Di16(*)                        | STM32F042    | 0x3E                              |
| Rly10(*)                       | STM32F042    | 0x3E                              |
| Di6Rly6(*)                     | STM32F042    | 0x3E                              |

(*) - obsolete

Use the folowing command to scan the I2C1 bus on Raspberry Pi:

`sudo i2cdetect -y 1`

Command and output:
```
sudo i2cdetect -y 1

0 1 2 3 4 5 6 7 8 9 a b c d e f
00: -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- --
10: -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- --
20: -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- --
30: -- -- -- -- -- -- -- -- -- -- -- -- -- -- 3e --
40: -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- --
50: -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- --
60: -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- --
70: -- -- -- -- -- -- -- --
```
If you can find the bootloader address 0x3E(or 0x39) in the i2cdetect output, than it’s ok to proceed to the next step.

## Download the firmware file

Go to the folder where you want to download the firmware file and type the following command:
```
wget https://github.com/raspihats/i2c-hat/releases/download/v1.1.3/DQ10rly.bin
```
You can find all firmware releases on [Github][github]

## Write the new firmware

Remove the `BOOT` jumper. The next command will write and start the new firmware:
```
stm32flash -w DQ10rly.bin -v -g 0x00 -a 0x3e /dev/i2c-1
```

[i2c-clkst-post]: {{site.baseurl}}/i2c-hat/2016/02/16/raspberry-pi-i2c-clock-stretch-timeout.html
[di16ac]: {{site.baseurl}}/products/i2c-hats/di16ac
[dq10rly]: {{site.baseurl}}/products/i2c-hats/dq10rly
[di6acdq6rly]: {{site.baseurl}}/products/i2c-hats/di6acdq6rly
[github]: https://github.com/raspihats/i2c-hat/releases