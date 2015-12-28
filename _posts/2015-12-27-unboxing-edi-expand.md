---
title: Unboxing Edi-Expand
layout: post
tags: Edison
---
Some days ago, I was very lucky to receive an Edi-Expand board from [Tektyte](tektyte.com) in Australia. The Edi-Expand breaks out a number of GPIO pins from the Intel Edison, adds an ethernet connection and 4 USB ports. 


<img src="/media/images/ediexpand_pcb.png" />

After unboxing, I first had a look at [the Getting Started guides](www.tektyte.com/docs/docpages/edi-expand/gettingstarted.html) for a quick overview.

The Edi-Expand has a number of nice LEDs to indicate the different states of the boards, especially about what parts of the board are activated through the switches. A nice blue LED lights constantly to indicate that the device is on. Then, there are red and green LEDs to indicate communication with the board, and whether or not the board is programming mode.

In order to work with breadboard setups, the Raspberry Pi compatible 14-pin header is interesting. There is an overview about the pins in the Edi-Expand schematic as below.

<img src="/media/images/ediexpand_breakout_headers.png" />

# Mapping of GPIOs to SYSFS

On the Edison, the mapping of pins from MRAA to pins in the filesystem (SYSFS and schematic) is a bit confusing. One source to better learn about the mapping is [this](http://www.i-programmer.info/programming/hardware/8744-exploring-edison-mraa-gpio.html) website.  From the website, there is a mapping of Arduino/MRAA pins to SYSFS pins is roughly as follows:

<img src="/media/images/edison_gpio_mapping.png" />

