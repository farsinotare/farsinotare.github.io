---
layout: post
title: The wiring problem
tags: wires electronics
---
In the beginning, there are breadboard prototypes. An examples looks as below:

<img src="/media/images/ledlogics_working.jpg" />

Breadboard wiring is often done with so called "jumper wires". Jumper wires can be as simple wires. Jumpe wires often come with headers, and for breadboards, wires with male type headers often make sense.

Well, breadboards are just lo-fidelity prototypes. For advancing a product, you want to replace a breadboard with a PCB. This influences the wiring. In contrast to breadboards, connecting a PCB is often done with wires with female headers.

For example, in the case of combining a <a href="http://ledlogics.com">LEDlogics</a> with an [Arduino Micro](http://pinboardjs.divshot.io/arduino_micro), a setup with male headers on the PCBs and female headers on the wires looks like this:

<img src="/media/images/small_arduino_ledlogics.jpg" />

The combination of male header connectors on the board together with female headers on the jumper wires is also a popular option for most breakout boards, for example see the following Nunchuk break out board:

<img src="/media/images/breakout_board.png" />

If you think about advanced wiring of digital systems, things get quickly more complicated. Would you really want to manage 10 or more wires between PCBs? No. When using multiple wires, you can use so called ribbon wires.

An example is here wiring up an old joystick with an RS-232 interface. You can find the RS-232 connectors easily, but how would you connect those to a PCB (or a breadboard)? Well, you most likely need ribbon cables, and probably some kind of breakout board.

Connectors on ribbon cables are another topic. Soldering a ribbon to a breakout board might be an option, but not the best, as you can see below:

<img src="/media/images/thumb_rs232_cable_2.jpg" />

For sure, wiring is an interesting and important part of electronic projects.


