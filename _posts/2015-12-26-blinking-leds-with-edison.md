---
title: Blinking LEDs with Edison mini breakout board
tags: edison
layout: post
---
The [Intel Edison Hardware guide](https://communities.intel.com/servlet/JiveServlet/downloadBody/23158-102-4-27348/edison-module_HG_331189-002.pdf) provides an interesting combination of connectivity (Wifi, Bluetooth and USB) with "special" pins for signal processing. This makes the board similar to a [Raspberry Pi](https://en.wikipedia.org/wiki/Raspberry_Pi) with Wifi and Bluetooth dongles, and on the other hand similar to an [Arduino](https://en.wikipedia.org/wiki/Arduino) with pins for processing "digital" and "analog" signals.

It is great to look how on both sides of an Edison module are mounted. On top, there are mainly components for connectivity:

* eMMC (embedded memory)
* USB transceiver
* Bluetooth transceiver
* A Wifi transceiver with antenna

<img src="/media/images/edison_top.png" />

On the bottom, there are the main processing blocks and a component for power management:

* Processor and DDR memory
* PMIC (power management IC)
* [a 70-pin Hirose connector](http://www.intel.com/content/www/us/en/support/boards-and-kits/000005798.html?wapkw=353)

<img src="/media/images/edison_bottom.png" />

Note that the system uses two processors:

* Core processor: IA-32(R), runs on 500 MHz
* 32-bit Intel(R) Atom(TM) Processor Z34xx Series, runs on 100 MHz

The logical levels of these processors are on 1.8V, which is nice for low-power consumption but harder to connect "classical" components from an Arduino or Raspberry Pi.

# Breakout boards

To use the Edison hardware for a Maker project, there are several breakout boards that act a bit like motherboards. The Edison is mounted on top. The breakout boards makes it easy to access certain pins of the Edison.

There are several breakout boards:

* Intel Mini Breakout board
* Intel Arduino Breakout board
* EdiExpand breakout board ( [see docs](http://www.tektyte.com/docs/docpages/edi-expand/usage.html) )
* [Sparkfun breakout boards](https://www.sparkfun.com/categories/272)

Besides access to pins, breakout boards help to manage power on the Edison. The Edison can be powewered with 3.15 to 4.5V, but USB has 5V or a DC jack can even have higher voltages. Also, some boards, such as the [Edi-Expand](/http://blog.farsinotare.com/2015/12/27/unboxing-edi-expand/) help with level-shifting signals.

Another function of breakout boards is to manage USB communication with the Edison and a host computer. The Edison uses 2 USB ports: One port for firmware updates, and another port for providing console communication.

Once you have selected a breakout board and mounted the component, you are most likely to run a firmware update and install some extra packages.

# Update firmware

As firmware changes over time, it is a good idea to get the latest version (currently Poky 1.7.2 if you follow the Intel projects). You can check what version you have with:

     # configure_edison --version

If you don't get a reply back, you should upgrade. Recent firmware will show you 159 as reply.

To update the firmware, have a look at:

* [Firmware update](https://software.intel.com/en-us/flashing-firmware-on-your-intel-edison-board-mac-os-x)
* [Another description firmware update](http://www.helios.de/heliosapp/edison/)

After installing the firmware, it is time to configure connectivity.

This is easy with the following command:

    # configure_edison --wifi

The board scans for networks and you can add your network of choice. (An Edison can also be configured as Access Point but this is the topic of another post).

To check that network settings are working, ping google.com for example:

    # ping google.com

Next, I advise to install "git" and some Node libraries.

To install git, you can follow the steps as in [setup.sh](https://github.com/embeddednodejs/ch_3_nodejs_on_embedded_linux/blob/master/edison/setup.sh)

And now, it's time to clone some projects based on the [MRAA](https://github.com/intel-iot-devkit/mraa) library. The basic board software setup should now be ready.

# Board schematics

To check the board setup and to learn about pin functions of the board, it's good to explore blinking LEDs. Blinking LEDs are the "hello world" experience of embedded systems. In the case of the Mini breakout board, we have to build a small circuit to make an external LED blink.

A good start are the schematics of the board. You can find the [Edison mini breakout board schematics](http://www.intel.com/content/dam/support/us/en/documents/edison/sb/mini_edison_breakout_hvm_8_26.pdf) online. It's a great source for learning about electronics, although if you have a software background contact with schematics can be a bit frustrating first.

From the schematics, you can learn how the mini breakaut board breaks out pins for power, pins for communication and for GPIOs. Another nice source learn about board schematics is [this guide](http://www.microcasts.tv/edison/) by [Kevin Sidwar](https://twitter.com/KevinSidwar).

<img src="/media/images/mini_bb_blocks.png" />

The main pin blocks are provided with 4 jumpers (J19, J17, J18, J20) where you can attach wires or probes for measurements (or LEDs). One important pin for Arduino projects is pin 13. However, we don't find "Pin 13" in the schematic, but need to take the detour via [a pin mapping provided by the MRAA library](https://github.com/intel-iot-devkit/mraa/blob/master/docs/edison.md).

Here you'll see that MRAA (or Arduino pin 13) maps to physical pin GP128:

    13  J17-14  GP128   GPIO-128   UART-1-CTS

This pin can also be found in the filesystem of the Poky Linux installation: 

    /sys/class/GPIO/GPIO_128

You can find some more basic documentation about the [jumpers on the board](https://www.arduino.cc/en/ArduinoCertified/IntelEdison) on the Arduino website.

To make the mini breakout board compatible with a breadboard, you must add header pins. So, you have to solder some. One possible approach is this approach by [Guido Burger](https://twitter.com/guido_burger):

<img style="width: 550px" src="http://fab-lab.eu/wp-content/uploads/2014/10/Edison_IO_LED.jpg" />

As next step, you'll see that the 1.8V logical levels from the Edison are too small to light an LED. Without level shifting, the Edison has 1.8V voltage levels.

A nice [approach to solve this problem](http://electronics.stackexchange.com/questions/207363/how-to-blink-led-with-1-8v) is by using a transistor. The schematic looks as below:

<img src="/media/images/bjt_schematic.png" />

The NPN transistor acts as a small current amplifier. If the GPIO is high, there goes a current from base to emitter. That current is "amplified" in the collector-base current which is high enough to drive the LED.

You can solder components to a soldering board as follows:

<img style="width: 400px" src="/media/images/bjt_schematic2.png" />

And, last, you can have the LED blink by connecting to the GPIO and running [the following Node.js code](https://github.com/embeddednodejs/ch_5_nodejs_libs_for_hardware/blob/master/mraa/blink.js).

<img style="width: 500px" src="/media/images/edison_led.jpg" />

The USB ammetter shows the input voltage of 5.1 V. This is a nice feedback that the board has power.

Please leave comments and feedback how to improve at [Reddit](https://www.reddit.com/r/IntelEdison/comments/3yp0hl/notes_on_getting_started_with_the_mini_breakout/).
