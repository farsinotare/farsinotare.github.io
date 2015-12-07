---
layout: post
title: My favorite prototyping tool
tags: prototyping
---
Small boards, like [Arduino Pro Mini, Nano's or Micro's](http://blog.farsinotare.com/2015/11/08/arduino-pro-mini/) are great. They are cheap, small and just need a mini USB cable.

They also fit well with breadboards. One thing makes these boards even better: [An adapter board for Grove Kit components](https://www.tindie.com/products/imrehg/grovehat-for-arduino-nano/). The [Grove headers and connectors](http://www.seeedstudio.com/depot/Grove-Universal-4-pin-connector-p-789.html) make plugging circuits very simple for software handed people. This can be nice to simple simulate *sensors* or *events*.

<img src="/media/images/grove_hat_nano.png" />

If you want to quickly learn about embedded devices, it's great too. An Arduino Nano costs only between 3-6 Eur on Ebay. Grove Kit components are very robust. And, there are many components already. Grove components can be used with normal Arduino, LinkIt One, Intel Edison, Beagleboard Green. Grove will be pretty good for hardware interoperability. It's not perfect, but seems to be better than anything else out there at the moment.

Now, with a Grove potentiometer that you connect to an analog input, you can nicely "simulate" sensor data. By tuning the knob, you can sweep through the whole range of an analog-to-digital converter (ADC). Then, you can easily exchange a button input for a LED output. Or you can build a quick display for I2C


And all this, in a blink of an eye. Without using soldering iron, or a magnificent glasses to check the right pins locations.

The pinout of the Grove header Nano provides plugs for 5 devices. If you get bored with LEDs, pots or buttons, you can easily attach other devices from [the Grove system](http://www.seeedstudio.com/wiki/Grove_System).

<img src="/media/images/grove_hat_pinout_wip.png" />

There is no clear marker for direction. So, you have to experiment a bit where a pin is located. One way to do this using the StandardFirmata firmware for Arduino and a GUI to check pin functions.

