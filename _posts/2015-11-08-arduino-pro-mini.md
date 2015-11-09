---
layout: post
title: Towards Tiny Arduino boards
tags: arduino, hardware, programmer
---

Last weekend started with a message on the mailing list:

  "Need Arduino Pro Mini 3.3V - because I broke mine [in this controller project](https://github.com/5shekel/wiperMotorPlatform)"

Since I had bought a bunch of Arduino Pro Mini's on Ebay a while back, I thought that I could help. The parts I bought are like the left one below. At its core, it is only an ATmega with a minimum components:

<img src="/media/images/pro_mini_1.png" />

On the right, there is an USB-to-FTDI converter for serial communication which is needed to program an Arduino Pro Mini. So, to do something useful with the board, the converter can act as a nice programmer as shown below:

<img src="/media/images/pro_mini_2.png" />

While the basic idea of combining two boards felt nice, I somehow preferered working with Arduino Nano's until this weekend.  On Ebay, the Arduino Pro Mini's are just incredibly cheap.

<img src="/media/images/ebay_pro_mini.png" />

As with other boards from China, you have to solder header pins to use them on a breadboard. Only, I also realized this weekend that there is a 3.3V and 5V version of the Arduino Mini. The 3.3V variant can be nice if you want to combine the board with a Raspberry Pi for example or other 3.3V components.

You can use the Arduino IDE to program the board. The following settings worked for me:

<img src="/media/images/arduino_mini_settings.png" />

But it is even possible to find cheaper boards with an MCU, such as the [ATtami board](http://telavivmakers.org/ATtami) and a schematic can be found [here](https://github.com/telavivmakers/at-tami).

<img src="/media/images/attami.png" />

This board reminds a bit on the [Wattuino Nanite](http://www.watterott.com/en/Wattuino-Nanite85) which is based on the [Nanite](https://github.com/cpldcpu/Nanite) design by Tim Böscke. However, that controller is so small, that it does run a special bootloader: [The Micronucleus](https://github.com/micronucleus/micronucleus) which is a bit larger than 1kByte.
