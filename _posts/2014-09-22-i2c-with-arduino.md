---
title: Speaking I2C with Wii Nunchuk
tags: i2c, wire
layout: post
---
Reading data from remote sensors and devices is often done with [I2C prototcol](http://en.wikipedia.org/wiki/I%C2%B2C). An important property of this protocol is that it uses only a single wire for data (in contrast to SPI that uses 4 or UART that uses separate lines for RX and TX).

# Soldercore I2C Nunchuk break-out board

As first contact with I2C, you can look at the [Soldercore breakout board](http://soldercore.com/wordpres/wp-content/uploads/2012/04/coreWii.pdf) for the Wii Nunchuk.

It basically says:

    SDA I2C Data 
    SCL I2C Clock

SDA stands for "serial data line", and "SCL" for "serial clock line", which are below on the left (J1), SDA at Pin 2, and SCL at Pin 3.

<img src="/media/images/breakout_board.png"></img>

# Arduino

Arduino supports the I2C protocol with the [wire](http://arduino.cc/en/reference/wire) library. Reading the description of the wire library, we see:

    Board I2C / TWI pins
    Uno A4 (SDA), A5 (SCL)

 Both,  SDA and SCL are places on the the analog input pins on the left, but it newer Arduino boards also support I2C with their own pins (on the top right, see the [board schematic](http://www.adafruit.com/blog/wp-content/uploads/2013/04/mega2.png)

As the Nunchuk is a I2C device, there are two different libraries that can be used to speak I2C with the Nunchuk.



# Tessel

I2C plays an important role at Tessel too. There, the following pins are supported on each module:


    Pin Name Notes
    1 GND Ground. Pins are marked with a circle.
    2 3V3 3.3 V power rail. The onboard regulator is rated to 3A.
    3 SCL I2C clock line. Ports A and B and the GPIO bank share a common I2C bus, as do ports C and D.
    4 SDA I2C data line. Ports A and B and the GPIO bank share a common I2C bus, as do ports C and D.

So, on the Tessel wiring a I2C device is even easier.



