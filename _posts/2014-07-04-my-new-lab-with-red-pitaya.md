---
title: Red Pitaya for the lab
layout: post
tags: measurements
images:
  - /media/images/redpitaya1.jpg
  - /media/images/redpitaya2.jpg
  - /media/images/redpitaya3.jpg
---
The [Red Pitaya](http://redpitaya.com/) is an open instruments platform. With the 4 SMA connectors, you can capture and generate high-frequency signals. With an open-source approach, this device might be interesting for enabling new kinds of electronics laboratories.

I was lucky to receive a box with the Red Pitaya today.

## Before You Get Started

Getting started with the Red Pitaya is easy. You need a number of things though:

* A network cable to connect your Red Pitaya to the network.
* A USB micro cable and/or power supply. The Red Pitaya manual advises a USB power supply that handles 2A, but my 1A power supply seems to handle the power just fine
* A micro SD card where you can install the RedPitaya OS, and if you are on a 11inch MacBook Air, as I am, you need to have a USB micro SD card reader/writer 

## The first run

Once you have the equipment, you can follow the getting started instructions as on the website. What I did was:

1. Download the RedPitaya OS, unzip the archive and write the files to the SD card
2. Next, you can boot the RedPitaya, i.e. plug the SD card, plug the power and network cable. some LEDs should start blinking (the yellow one mainly, and some LEDs from the ethernet interface)
3. Next, you need to find the IP address of the RedPitaya. The device normally gets the IP address with DHCP. You can also [customize the network setup](http://wiki.redpitaya.com/index.php?title=User_Manual#Manual_network_interface_configuration) as I will probably do later too. Right now, I found the IP by looking into the logs of my router. In my case, the IP was: http://192.168.2.108/
4. From here on, you can access the RedPitaya webserver, and run the applications such as the oscilloscope and signal generators. In the future, we might share and discuss our own applications via the [RedPitaya bazar](http://wiki.redpitaya.com/index.php?title=User_Manual#Installing_applications).

There is also an option to log in to the Red Pitaya with an SSH console over USB. This might be interesting to explore further.

## An open-source measurement community

The Red Pitaya comes with 3 applications out of the box: An oscilloscope, a signal generator and a spectrum analyzer. But thanks to the open-source approach, you can build and run your own applications. A first community of developers has formed already, and  there are already 9 community applications available for download in the [Bazaar](http://bazaar.redpitaya.com) section and we should expect many more to come. 

## A first Hello World measurement

If you want to see the Red Pitaya in action, have a look at the pictures below:

<ul>
<li><img src="{{ page.images[0] }}" /></img></li>
<li><img src="{{ page.images[1] }}" /></img></li>
<li><img src="{{ page.images[2] }}" /></img></li>
</ul>

# Power on 

<object type="application/x-shockwave-flash" width="400" height="225" data="https://www.flickr.com/apps/video/stewart.swf" classid="clsid:D27CDB6E-AE6D-11cf-96B8-444553540000"><param name="flashvars" value="intl_lang=en-US&photo_secret=1dddb28274&photo_id=14385189560"></param><param name="movie" value="https://www.flickr.com/apps/video/stewart.swf"></param><param name="bgcolor" value="#000000"></param><param name="allowFullScreen" value="true"></param><embed type="application/x-shockwave-flash" src="https://www.flickr.com/apps/video/stewart.swf" bgcolor="#000000" allowfullscreen="true" flashvars="intl_lang=en-US&photo_secret=1dddb28274&photo_id=14385189560" width="400" height="225"></embed></object>


<object type="application/x-shockwave-flash" width="400" height="225" data="https://www.flickr.com/apps/video/stewart.swf" classid="clsid:D27CDB6E-AE6D-11cf-96B8-444553540000"><param name="flashvars" value="intl_lang=en-US&photo_secret=abf3dd997c&photo_id=14385255869&hd_default=false"></param><param name="movie" value="https://www.flickr.com/apps/video/stewart.swf"></param><param name="bgcolor" value="#000000"></param><param name="allowFullScreen" value="true"></param><embed type="application/x-shockwave-flash" src="https://www.flickr.com/apps/video/stewart.swf" bgcolor="#000000" allowfullscreen="true" flashvars="intl_lang=en-US&photo_secret=abf3dd997c&photo_id=14385255869&hd_default=false" width="400" height="225"></embed></object>

