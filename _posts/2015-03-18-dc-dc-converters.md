---
title: DC-DC converters
tags: converters, analog, mixed
layout: post
---
If you power mobile solutions, you most likely need to convert a battery voltage into something "usable". Most likely into 5V or 3.3V. 
An additional difficulty comes with a battery voltage that changes over time.

So, what to do? Feedback systems to the rescue. DC DC converters provide a rather constant current at different output voltage from its input. Here is a collection of links that might clarify some concepts:

* The [EEVvblo](https://www.youtube.com/watch?v=-V_p1GBH4pk) has some great overview about building power supplies with DC DC converters. [An Arduino Proto platform](https://www.youtube.com/watch?v=kfBREaP93Xc): A general overview for supplying an Arduino and sensors from the same power source.

* [A datasheet of a an advanced DC DC converter](http://www.ti.com/lit/ds/symlink/lm8850.pdf): Interesting here is the amount of digital logic that goes into a DC DC converter. The logic is controlled with I2C. A simpler but widely popular DC DC converter is [the MC34063](https://www.sparkfun.com/datasheets/IC/MC34063A.pdf).

* [An intro to BOOST converters](http://reibot.org/2011/08/07/intro-to-boost-converter/): DC DC converters can be from type step-up or step-down. This tutorial shows some ideas for building your own Boost converter.

* [Linear regulators](http://en.wikipedia.org/wiki/Linear_regulator): These converters provide an accourate scaled voltage (or voltage) based on a resistor. However, resistors dissipate power, so for mobile uses they are not the first choice. In some cases, it is simpler to use this type of DC Dc converter.

* [Discussion about building a Buck converter](http://www.eevblog.com/forum/beginners/%28how-to%29-arduino-digitally-controlled-step-down-buck-dc-converter/): Buck or step-down converters provide a scaled version of the input. There is a nice discussion about using those in the forum of the EEVblog.

* [Role of a DAC in a DC DC converter](http://www.microchip.com/forums/m688260.aspx): This link provides some information about using feedback in a Buck converter.

* [Energy in an LC circuit](http://www.tpub.com/neets/book9/34d.htm): In some DC DC converters power is stored and provided from an LC circuit. Here is some information about energy in that.

