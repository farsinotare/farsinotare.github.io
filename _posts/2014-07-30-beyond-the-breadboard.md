---
title: Beyond the Breadboard
layout: post
tags: arduino, pcb
---
From breadboard prototypes to electronic products takes some design and concept iterations. Building a sellable products, inolves printing circuits and assembling components, on a PCB or a soldering plate.

# PCB design

To start you need some PCB design tools. Unfortunately, there are no good free, open PCB design tools, not to mention web based approaches.

You will notice that some software packages such as [Viewplot](http://viewplot.com/) come only for Windows, or products such as Altium are very [expensive](http://www.altium.com/en/altium/press-center/press-releases/altium-delivers-new-altium-designer-14). An alternative seems to be [Eagle](http://www.cadsoftusa.com/download-eagle/) from CadsoftUSA, but I still have to explore these directions further.

As I had no experiences with PCB layout, I was lucky to find help [at the Arduino Forums](http://forum.arduino.cc/index.php?topic=255066.msg1804814#msg1804814). After clarifying the idea of the prototype I had on my PCB, I had the "Gerber" files some days later. Gerber seems to be a popular PCB file format that can be used by PCB manufacturers. 

# PCB Manufacturing

Once the PCB design is ready, it is possible to take quotes for PCB production from PCB manufacturers. I wanted my board quickly, so I thought to approach local PCB manufacturers (Munich).

I found two: [Aetzwerk](http://www.aetzwerk.de/) and [Top-Print](http://www.top-print-pcb.de/). Both companies offer the same services for the same price. It is even possible to order just a single board.

I got the PCBs after around 1 week from ordering, and both looked liked very high quality. Yet, their price was a bit high, and I think next time, I just order the PCB from one of the many online suppliers:

* [pcb devboards](https://www.pcb-devboards.de/)
* [pcbpool](http://www.pcb-pool.com/ppde/index.html)
* [eurocircuits](http://www.eurocircuits.com/)
* [printec](http://www.printec-pcb.com.tw/en_product.php)


# Small Series Production

Once, you have your prototype design validated, the next step would be producing a small series of PCBs.

You might want to look at Kickstarter projects, where people ask for funding for electronic projects. A nice current example is this [PIC microcontroller board with integrated USB connector](https://www.kickstarter.com/projects/715586821/the-must-have-development-tool-ping25xx).

It can make sense to collect funds upfront, and go into small series production only with the first product community at hand.

In general: To produce PCBs in batches, the cost calculations are a bit different. First, there is a minimum amount of PCBs in a batch, e.g. 32 parts. Then, there are initial setup costs.


# Open-source Hardware

For really small batches, there is another approach to "pool" PCB production, with e.g. [OSH Park](https://oshpark.com/shared_projects). You can share your design, or simple source a design that is close to your needs. Apparently, it is possible to have several boards for just 10 Eur.
