---
layout: post
title: The Arduino Schematic
tags: Arduino
---
Arduino is open-hardware. This means you can freely inspect and explore the board blueprints. To do this, you can find copeis of the schematic [here](https://www.arduino.cc/en/Main/arduinoBoardUno) --> "Schematic and Reference Design".

The board files come in EAGLE format, which you can [freely download](http://www.cadsoft.de/download-eagle/) for non-commercial usage. Once you have EAGLE, you can inspect the Arduino PCB (stands for Printed Circuit Board) which looks as below.

<img src="/media/images/arduino_board.png" />

On this PCB, there are 4 important functions:

1) The MCU: This is the main component of the board. On an Arduino UNO it is an Atmel ATMega328 chip with digital and analog inputs, as well as digital and "PWM" outputs. These pins can be used to switch external state, drive actuators or sense an environment.

2)  Power supplies: The microcontroller needs a stable 5V. But in many embedded systems you'll deal with other devices too, batteries for example, but also displays or sensors. The Arduino power management takes care of converting smoe voltages and making them stable on the board. 

3) To burn softwate onto the microcontroller, the boards needs a way to communicate with an external programmer. This can be done with serial communication that requires a driver chip. Often, you'll find a chip for serial communication, but sometimes it can be a JTAG or ISCP adapter too.

4) Last, the board provides multiple header and a standard form factor that allows others to interface the Arduino.

Ok, so far an overview about the components. How do they actually work? For this, we need to look at [the schematic of an Arduino](https://www.arduino.cc/en/uploads/Main/Arduino_Uno_Rev3-schematic.pdf). The schematic looks like:

<img src="/media/images/arduino_uno_schematic.png" />

Now, the components from above get some more meaning. There are basic discussions about the power management schematic[here](http://electronics.stackexchange.com/questions/65576/arduino-uno-r3-directly-supply-regulated-5v-to-5v-pin) and [here](http://electronics.stackexchange.com/questions/180963/what-happens-in-the-arduino-power-supply-schematic).

A good discussion about the progammer of an Arduino is [here](http://electronics.stackexchange.com/questions/96805/how-to-program-arduino-nano-pro-mini-pro-micro-clone-that-has-no-usb-port). It takes data from an serial port and converts it into board data.

