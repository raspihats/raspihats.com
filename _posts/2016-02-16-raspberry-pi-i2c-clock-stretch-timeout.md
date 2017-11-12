---
layout: post
title:  Raspberry Pi I2C clock stretch timeout
date:   2016-02-16 12:13:02 +0300
categories: I2C-HAT
---

## Important!!!
Every step described in this post is automatically performed by the setup script of the [raspihats python package][raspihats-package]. Just install the [raspihats package][raspihats-package] and the I2C clock stretch timeout should be set to the right value for operating the I2C-HATs. 

## Clock stretch timeout register – CLKT

The `TOUT` field from `CLKT` register provides a timeout on how long the master waits for the slave to stretch the clock before deciding that the slave has hung, the default value for `TOUT` is 0x40(64 decimal), it is 16 bit long, this is from [BCM2835-ARM-Peripherals doc][BCM2835-ARM-Peripherals].

Calculating timeout for the default baudrate(100kbps):

timeout = `TOUT` * 1/baudrate = 64 * 0.01ms = 0,64ms

During normal operation this clock stretch timeout can be too small, for example when the I2C-HAT is requested to save a parameter in on-board flash, like DigitalOutputs Safety Value, PowerOn Value or the Communication Watchdog Period Value, the flash saving operation may imply a mass erase operation which has the longest duration of the flash operations, about 40ms on STM32 micro present on the I2C-HAT, this is why the default clock stretch timeout value of 0,64ms is too small.

Clock stretching is also heavily used during I2C-HAT firmware update, also implying mass erase.

An appropriate value for the clock stretching timeout should be 200ms, it’s selected to be 5 times greater than 40ms, just for safety.

`TOUT` = 200ms / 0.01ms =  20000(0x4E20), for the default baudrate of 100kbps

## Some C code

The next two pieces of C code are used to set/get the clock stretching timeout value on the Raspberry Pi:

  1. [i2c1_set_clkt_tout.c][i2c-clkst-setter]
  2. [i2c1_get_clkt_tout.c][i2c-clkst-getter]

Open a terminal on Raspberry Pi, go to the desired folder and download the two files:
{% highlight console %}
wget http://raspihats.com/downloads/i2c1_set_clkt_tout.c
wget http://raspihats.com/downloads/i2c1_get_clkt_tout.c
{% endhighlight %}

Compile and link source files into executables:
{% highlight console %}
gcc -o i2c1_set_clkt_tout i2c1_set_clkt_tout.c
gcc -o i2c1_get_clkt_tout i2c1_get_clkt_tout.c
{% endhighlight %}

Run the getter first, to see the value of your `CLKT.TOUT`, should be 64(default value):
{% highlight console %}
sudo ./i2c1_get_clkt_tout
{% endhighlight %}

To set the 200ms desired clock stretching timeout run the following command:
{% highlight console %}
sudo ./i2c1_set_clkt_tout 20000
{% endhighlight %}

This value will be used until next time Raspberry Pi boots.

## Set desired clock stretching timeout at boot

You probably want to automatically set the clock stretching timeout every time Raspberry Pi boots. To do this you must edit your /etc/rc.local. More on runnig a script on startup you can find [here][startup-script] 

I’m using nano for editing the rc.local file.
{% highlight console %}
sudo nano /etc/rc.local
{% endhighlight %}

Add the following line just before “exit 0”:

/home/pi/workspace/i2c1_set_clkt_tout 20000

You should modify /home/pi/workspace/ path to point where you’ve build the executable with gcc.

Don’t forget to save the file using “Ctrl + O” than “Enter”. Exit nano with “Ctrl + X” and reboot.
{% highlight console %}
sudo reboot
{% endhighlight %}

After reboot you should use the getter to check that the value for CLKT.TOUT is 20000
{% highlight console %}
sudo ./i2c1_get_clkt_tout
{% endhighlight %}


[BCM2835-ARM-Peripherals]: https://www.raspberrypi.org/app/uploads/2012/02/BCM2835-ARM-Peripherals.pdf
[i2c-clkst-setter]: https://github.com/raspihats/raspihats/blob/master/clk_stretch/i2c1_set_clkt_tout.c
[i2c-clkst-getter]: https://github.com/raspihats/raspihats/blob/master/clk_stretch/i2c1_get_clkt_tout.c
[startup-script]: http://raspberrywebserver.com/serveradmin/run-a-script-on-start-up.html
[raspihats-package]: https://pypi.python.org/pypi/raspihats