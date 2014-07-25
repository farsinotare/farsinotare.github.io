---
title: Lighting Design Overview
layout: post
tags: light design art
---
Light influences our experiences like no other media. With the advances of LED technology, we can expect to experience many different lighting solutions in the near future. And, with IoT ideas, you can start talking directly to your lamps with IP addresses, maybe this year already, maybe next year.

# The Need for Light

That people are looking for new ways to control light can be impressively seen from [this kickstarter](https://www.kickstarter.com/projects/metamanda/clyde-an-expressive-lamp-for-creative-homes) project. There were almost 1000 backers, and $150,000 pledges. Apart from a special design of the lamp, the project's main features were light controls with an [Arduino](http://arduino.cc/) and special software.

The technical specifcations on the light are rather "simple" and described with "High-intensity, energy-efficient LED task lighting. At about 6W, the LEDs output more light than a 40W incandescent."

# Advanced Light Design

While this lamp is a consumer product targetted mostly towards tinkerers, light design plays a very important role in architecture for a number of years already.  One widely used system is the [Philips ColorKinetics](http://www.colorkinetics.de/showcase).

The ColorKinetics interface is done with [DMX power and data supplies](http://www.colorkinetics.de/support/datasheets/PDS-60ca_24V_DMX_SpecSheet.pdf).  The [pinout](http://en.wikipedia.org/wiki/DMX512#Connectors) of the coonectors applies differential signalling with one or two data lines. On the data lines, serial data is transmitted at 250 kBaud.

DMX512 is not only used in high-end lighting products, but also in [Arduino projects](http://playground.arduino.cc/Learning/DMX). These might result in fun projects, since there are plenty of devices at Ebay that support DMX512.

Yet, if you want to follow the road of advanced lighting design, you probably will leave the Arduino behind sooner or later, and start with software and prototyping tools like [VVVV](http://vvvv.org/) or [OpenFrameworks](http://openframeworks.cc/about/). With these kind of tools, you can think of hacking projectors or build your own lighting components.

# Light Networks

So, controlloing a single light source is often just a start. Especially, with cheaper networks access and cheaper lighting components, light networks will get more and more important.

Enter the [LIN bus](http://blog.farsinotare.com/2014/04/15/2-the-lin-bus/) again. LIN is a single-wire protocol that is used to connect a number of slaves to a single master. One advantage of LIN is that you could get diagnostic information on your light, and easily program light sequences with PWM signals.

A number of semiconductor companies produce LIN RGB drivers, such as [this one from ONSemiconductors](http://www.onsemi.com/pub_link/Collateral/NCV7430-D.PDF). Infineon offers an [Low Side current source](http://www.infineon.com/dgdl/TLD7305EK-Data-Sheet-10-Infineon.pdf) that could act as LIN slave in a lighting network. Melexis has the following [driver chip](http://www.melexis.com/IO-Control-ICs/IO-Control-ICs/LIN-RGB-slave-for-ambient-light-applicationsLIN-slave-for-IO-extension-796.aspx). Andrew Stone published some very interesting light sketch for LIN and Arduino [here](https://github.com/gandrewstone/LIN)

