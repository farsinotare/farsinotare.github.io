---
layout: post
title: Buidling an Alarm clock
tags: Arduino, starters
---
At the last [Arduino meetup](http://munich-aug.de/), Kresi proposed the idea of an Arduino based alarm clock. 

# Tracking time

A basic approach for tracking time is by using [real time clocks](https://learn.adafruit.com/adafruit-data-logger-shield/using-the-real-time-clock). By using an RTC, you keep your timing unit decoupled from the Arduino internal circuits (and importantly battery power).

If you want to get an RTC, you probably end up with

* [DS1307](http://www.instructables.com/id/Arduino-Real-Time-Clock-DS1307/)
* But there are also shields, such as [from TinyCircuits](https://tiny-circuits.com/tiny-shield-rtc.html)

If you don't have an RTC yet, you can track time with some simple code too:

    void loop() {
      digitalWrite(13, HIGH);   // turn the LED on (HIGH is the voltage level)
      delay(500);               // wait for 1/2 second
      digitalWrite(13, LOW);    // turn the LED off by making the voltage LOW
      delay(500);               // wait for 1/2 second
   }


Now, the code above basically switches the Arduino onboard LED. Each blink cycle takes 1 second. This is assured by internal Arduino timers.

# A pointer for seconds

The simplest way to track seconds might be with the Arduino serial port. Addressing the serial port only takes 2  lines of code:

In the setup part this is:

    Serial.begin(9600);  

In the loop part this is:

    Serial.println(i);


But the serial port is hardly interesting for a fancy pointer. RGB LEDs are much more fun. For this, we need to look at the neopixel library.

neopixel set pixel

https://github.com/adafruit/Adafruit_NeoPixel/blob/master/Adafruit_NeoPixel.cpp

# A display for time


pinout 84x48 Nokia 5110 LCD display. Wiring up can be a bit difficult.

http://www.ebay.de/itm/84X48-Nokia-5110-LCD-Display-Module-blue-backlight-with-PCB-adapter-for-Arduino-/371160226424?pt=Wissenschaftliche_Ger%C3%A4te&hash=item566adf9a78

Next, http://playground.arduino.cc/Code/PCD8544


Dynamically update a string.

http://stackoverflow.com/questions/7383606/converting-an-int-or-string-to-a-char-array-on-arduino



http://playground.arduino.cc/Code/PCD8544
