---
layout: post
title: The bus pirate
tags: i2c spi bus protocols
---
The [bus pirate](http://dangerousprototypes.com/docs/Bus_Pirate) is a bit like a swiss pocket knife: It bundles many specialized functions in a tiny package.

My first contact with the bus pirate with at the [JTAG workshop at Hackaday Munich](http://hackadaymunich.com/). We connected the bus pirate to an old Linksys network router and started hooked into its UART interface. The topic looked a bit similar to this [hack of a WRT54G](http://hackaday.com/2011/07/08/reverse-engineering-vxworks-which-replaces-linux-on-newer-routers/), but all was based on the bus pirate. In principle, you can use the [Open On-Chip debugger](http://openocd.sourceforge.net/) as described [here](http://cybermashup.com/2014/05/01/jtag-debugging-made-easy-with-bus-pirate-and-openocd/).

# What is the bus pirate?

The bus pirate is [a kind of "bridge"](http://dangerousprototypes.com/2009/07/23/bus-pirate-101/). It translates signals from one signal to another, e.g. from UART to SPI. As such you can use the bus pirate as a [programmer for Arduino](http://ilikepepper.wordpress.com/2011/09/15/buspirate-arduino/). And sometimes, the bus pirate is easier to setup than tools that ship from [vendors](http://blog.rareschool.com/2011/11/buspirate-to-rescue.html).

Other examples on the web show the bus pirate as [USB-ttl converter](http://haquesprojects.com/embedded-device-hacking/using-a-bus-pirate-as-a-usb-ttl-serial-converter/). Or, as [FTDI cable](http://blog.zencoffee.org/2011/07/bus-pirate-as-ftdi-cable/). This can be useful if you want to program some Arduino, such as Pro mini, or clone via [UART](http://dangerousprototypes.com/bus-pirate-manual/bus-pirate-uart-guide/). At this moment, I did not get it working but in principle it should be possible. There is a nice schematic on how the bus pirate MOSI/MISO map to a UART device.

Last, the bus pirate supports [SPI](http://dangerousprototypes.com/bus-pirate-manual/bus-pirate-spi-guide/). This makes it an universal programmer since many devices support programming via SPI (like) commands.

# What do you need?

The bus pirate provides 10 pins in form of an IDC conector. As you'll need to work with different protocols, it maybe be helpful to buy crocodile cables or cables like [this](https://solarbotics.com/product/14012/)

Often it is useful to have a quick pinout of the [bus pirate connectors](http://dangerousprototypes.com/docs/images/1/1b/Bp-pin-cable-color.png).

# The bus pirate menu

A nice overview on the bus pirate options is [here](http://dangerousprototypes.com/bus-pirate-manual/bus-pirate-menu-options-guide/). The options I used most were "M" to set a certain protocol, and "W" to turn on/off power.
