---
title: Blinking LEDs with Edison mini breakout board
tags: edison
layout: post
---
The [Intel Edison Hardware guide](https://communities.intel.com/servlet/JiveServlet/downloadBody/23158-102-4-27348/edison-module_HG_331189-002.pdf) gives a good overview about the board.

The main module comes with components on both sides. On top, there is:
* eMMC (embedded memory)
* USB transceiver
* Bluetooth transceiver
* A Wifi transceiver with antenna

<img src="/media/images/edison_top.png" />


On the bottom, there is:

* PMIC (power management IC)
* Processor and DDR memory

<img src="/media/images/edison_bottom.png" />

There are two processors:

* Core IA-32(R) 500 MHz
* 32-bit Intel(R) Atom(TM) Processor Z34xx Series @ 100 MHz

Note that the logical levels of these processors are 1.8V (which is nice for low-consumption).

# Breakout boards

Now, to use this hardware, there are several breakout boards (a bit like motherboards) to mount an Edison on top:

* Intel Mini Breakout board
* Intel Arduino Breakout board
* EdiExpand breakout board ( [DOCs](http://www.tektyte.com/docs/docpages/edi-expand/usage.html) )

An important function of breakout boards is to manage power on the Edison. The Edison can be powewered with 3.15 to 4.5V, but USB has 5V or a DC jack can even have higher voltages.

Another function of the boards are communication with the Edison over USB. The Edison uses mainly 2 USB ports: One port firmware updates, and another port for console inputs.

The rest of this post is about exploring the Mini Breakout board.


# Update firmware

Firmware changes and it is a good idea to get the latest version. You can check what version you have with:

   # configure_edison --version

If you don't get a reply back, you should upgrade. Have a look at:

* [Firmware update](https://software.intel.com/en-us/flashing-firmware-on-your-intel-edison-board-mac-os-x)
* http://www.helios.de/heliosapp/edison/

# Board schematics

The mini breakaut board breaks out xx GPIO pins, some power pins and pins for communication.

<img src="/media/images/mini_bb_blocks.png" />

Some basic documentation about the [jumpers on the board](https://www.arduino.cc/en/ArduinoCertified/IntelEdison) can be found on the Arduino site.

The mini breakout board does not have header pins. So, you need to solder some. One possible approach is this approach by Guido Burger:

<img src="http://fab-lab.eu/wp-content/uploads/2014/10/Edison_IO_LED.jpg" />


As next step, you'll see that the logical levels are too small to light an LED. Without level shifting, the edison has 1.8V voltage levels.

How do you blink an LED with it?

One approach is by using a transistor.

A transistor acts as a small current amplifier. if the GPIO is high, there goes a current from base to emitter. That current is "amplified" in the collector-base current which is high enough to drive the LED.


Now, it's possible to apply MQTT to remotely switch the LED.

https://github.com/mqttjs/MQTT.js#subscribe
