---
layout: post
title: Disassembling a servo motor
tags: motors arduino
---

Servo motors allow to position somthing, for example a pointer.

<img src="/media/images/pointer.png" />

The basic Arduino code to move that pointer could be something similar to:

    #include <Servo.h>

    void setup() 
    { 
      myservo.attach(9);
      myservo.write(90);  // set servo angle
    } 

See the [Arduino API](http://arduino.cc/en/Reference/ServoWrite) for information about "writing" a position. That position is regulated with help of a [feedback loop](http://en.wikipedia.org/wiki/Feedback#History).


Let's look a bit deeper into the feedback mechanics of a servo motor.

# Position control

Typically, [servomotors](http://en.wikipedia.org/wiki/Servomotor) look as:

<a href="https://www.flickr.com/photos/unavoidablegrain/2815722060" title="R/C Servo by Greg Borenstein, on Flickr"><img src="https://farm4.staticflickr.com/3218/2815722060_9cf6bbfe74_m.jpg" width="375" height="275" alt="R/C Servo"></a>

From this picture, we see two important parts. Some gears on top, and the main DC motor bottom left. Bottom right is some integrated circuit, and a potentionmeter.
I opened a damaged servo to look inside, and the parts are clear here too:

<a href="https://www.flickr.com/photos/pmulder99/16353556499" title="servo motor by Patrick Mulder, on Flickr"><img src="https://farm8.staticflickr.com/7320/16353556499_0cfbc8b696_m.jpg" width="375" height="475" alt="servo motor"></a>

Removing the DC motor, gives some mechanical parts as well as a potentionmeter to get feedback. 

Another nice illustration of the different parts is in this video:

<iframe width="420" height="315" src="https://www.youtube.com/embed/-XSXfqd1N58" frameborder="0" allowfullscreen></iframe>


# Postion feedback

By adding feedback of the position of the motor, the position can be better controlled. This is basic feedback theory, but requires reading an extra signal. This is often not done with a servo motor.


# Continuous rotation

Often, servo motors are limited to a position range only, e.g. 0 to 180 degress. This is done with the gears and the motor feedback if I understand correctly. It is possible to remove the limitation. This is shown in this video:

<iframe width="560" height="315" src="https://www.youtube.com/embed/bpO7XMXGzfw" frameborder="0" allowfullscreen></iframe>

It is also possible to buy continous rotation servo motors directly, e.g. from [Adafruit](http://www.adafruit.com/product/154). The advantage of using such kind of motors is the gearbox.

## Comments
Leave comments at [reddit](http://www.reddit.com/r/arduino/comments/2wj4wz/disassembling_a_servo_motor/)

