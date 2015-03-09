

The main properties of the LIN bus are:
* single master with multiple slaves concept


Raspberry PI (master) - Arduino (Slave) - communication via I2C

* http://forum.arduino.cc/index.php?topic=231764.0


* https://forum.sparkfun.com/viewtopic.php?f=14&t=38056&p=170349&hilit=master+slave#p170349

According to the I2C bus protocol the bus Master (in this case the application processor) sends a packet across the bus starting with the address of the slave, followed by each byte of the message. The Slave (that would be the display controller processor in this case) acknowledges being addressed and then acknowledges having received each subsequent byte of the message.

On the Arduino the I2C bus protocol is easily handled for you by a library called Wire. The Wire library was used in coding up the BubbleDisplay library and will be used again here in the display controller firmware.


* https://forum.sparkfun.com/viewtopic.php?f=42&t=37866&hilit=master+slave

 think the problem the OP is running into is that when the master requests data from the slaves, both respond at the same time. Everything gets jumbled and things freeze up. Frankly just have a single reply is farther than I ever got. To solve the simultaneous responses I think the slaves need to be addressed 1 and 2. The master needs to call each individually. IIRC this is how multiple ICs communicate using I2C. I'd love to see basic code for both the master and slave. 
https://news.ycombinator.com/item?id=7634314

* An LCD display that shows the local transit times, so I know when to head out to catch a bus/train * An LCD display that shows my weekly mileage (running) and other relevant stats, maybe for other people I follow, too * An LCD display that alerts me if it I missed a phone call or text.
I guess the first step is figuring out how to hook up an LCD to my Raspberry Pi... :)

A temperature sensor for BBQ smokers.
Simple thermocouple with an Adafruit breakout board (MAX31855), and an existing Python driver.
Also serves up a Nodejs static page that polls for a new temperature every 5 seconds.
I'm struggling to find the time to get this going, but it's working okay right now. https://github.com/CanadaJ/heat-of-my-meat-node
reply
	
ckvamme 2 hours ago | link

I built a media console.
Great source of inspiration here-
http://www.raspberrypi.org/forums/viewforum.php?f=15




https://freeboard.io/
This is cool, but I think your description is a misnomer. This is a dashboard for Internet-connected devices that provide various readings and status updates.
In my world (enterprise security) -- "Internet of Things" generally means the connectedness of many things at scale. So when I saw the description I got really excited that it'd be a dashboard to help monitor a million devices, or help surface intelligence from the temperature readings of 100,000 sensors across a farmland. Or 500,000 energy meters. Etc. That's what will be cool when people figure out how to do. How do you surface intelligence insights and the data that matters from an avalanche of data coming out of 100's of 1000's or even millions of devices. :-)
That's a free business idea, because not many folks are doing this yet, and none are doing it well.



In my case it's for a CRM / marketing dashboard, so the data is more stuff like "pageviews over time" or "sales today vs last week".
I'm fairly sure that the actual data is unimportant if the widgets and data format are sufficiently generalised.
The important parts for me are how style-able the widgets are... seems like everyone is going for these carbon-black dashboards which isn't ideal for most of where we want to show it (ie, not a statusboard on a TV)
reply




http://www.byteparadigm.com/applications/introduction-to-i2c-and-spi-protocols/



http://en.wikipedia.org/wiki/Serial_Peripheral_Interface_Bus



http://arduino.cc/en/Reference/SPI



https://github.com/breakfastny/node-serialbuster

