---
layout: post
title: SSH to RedPitaya
tags: redpitaya, measurements
images:
  - /media/images/redpitaya_shell.PNG
---
In my [previous post on RedPitaya](http://blog.farsinotare.com/2014/07/04/my-new-lab-with-red-pitaya/), I showed the web interface of Red Pitaya. While the web interface is nice for ad-hoc experiments, the Red Pitaya command line interface (CLI) gives new ways to generate custom signals and measurements.

To use the Unix shell on RedPitaya, you can use ssh.

# Finding Red Pitaya

Before you can execute commands from the command-line, you must know the RedPitaya IP address.

If you have setup RedPitaya with a dynamic IP address, you can use the following [nmap](http://en.wikipedia.org/wiki/Nmap) command to lookup its IP address:

    $ nmap -p 80 --open -sV 192.168.2.0/24

This port scan will take some seconds, but if everything works, you will see something along these lines:

    Starting Nmap 6.46 ( http://nmap.org ) at 2014-07-13 14:10 CEST
    Strange error from connect (65):No route to host
    Nmap scan report for speedport.ip (192.168.2.1)
    Host is up (0.0024s latency).
    PORT   STATE SERVICE VERSION
    80/tcp open  http    Router HAD23V WAP http config
    Service Info: Device: WAP
    
    Nmap scan report for HAD23V_02 (192.168.2.103)
    Host is up (0.024s latency).
    PORT   STATE SERVICE VERSION
    80/tcp open  http    nginx 1.5.3
    
    Service detection performed. Please report any incorrect results at http://nmap.org/submit/ .
    Nmap done: 256 IP addresses (3 hosts up) scanned in 8.67 seconds
    

Now, we can use the IP of 192.168.2.103

# SSH command

Now, let call ssh as follows:


      $ ssh root@192.168.2.103


Both, the username and password are "root".


From here, you can run the commands:

    $ generate

and

    $ acquire


You can even write your own commands and cross-compile e.g. a square wave generator.

<img src="{{page.images[0]}}" />
