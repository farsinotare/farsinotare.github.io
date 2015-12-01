---
layout: post
title: The Riotboard
tags: riotboard
---
Working with embedded graphics and multimedia requires a powerful process.

This was the main reason I got the [Riotboard](http://riotboard.org/) a while ago. The board has a powerful ARM Cortex A9 core delivered by an i.MX6Solo.

The board boots by default Android from the embedded flash.  It also has two SD Card (micro and normal) slots, so you can customize what to boot.
Once an SD-Card is prepared, you can select the OS to boot with jumpers.

Here are the jumper settings taken from [here](http://www.element14.com/community/servlet/JiveServlet/download/2525-37206-123703-151737/RIoTboard+Boot+Switches.pdf)

<img src="/media/images/riot_switches.png" />

To work with the board, you'll need an FTDI serial-to-USB converter.

So far, I did not yet manage to install Linux. Also, I am not sure where/how to start with Android developing.

<img src="/media/images/riotboard_sw_download.png" />


From [MCU on Eclipse](http://mcuoneclipse.com/2014/07/21/terminal-connection-to-the-riot-board/), the following debug setup is helpful:

<img src="/media/images/riot_debug.png" />

Starting up the board with debug code shows something like:

      Hit any key to stop autoboot:  0
      kernel   @ 10808000 (4739640)
      ramdisk  @ 11800000 (233777)
      kernel cmdline:
              use uboot command line:
      	        console=ttymxc1,115200 init=/init nosmp video=mxcfb0:dev=hdmi,1280x720M@60,bpp=32 video=mxcfb1:off fbmem=10M vmalloc=400M androidboot.console=ttymxc1 androidboot.hardware=freescale
      
      		Starting kernel ...
      
      		Initializing cgroup subsys cpu
      		Linux version 3.0.35-06430-gd4e9d43-dirty (android@embest-tech) (gcc version 4.6.x-google 20120106 (prerelease) (GCC) ) #4 SMP PREEMPT Fri Mar 7 17:32:26 CST 2014
      		CPU: ARMv7 Processor [412fc09a] revision 10 (ARMv7), cr=10c53c7d
      		CPU: VIPT nonaliasing data cache, VIPT aliasing instruction cache
      		Machine: Freescale i.MX 6Solo RIoTboard
      		Ignoring unrecognised tag 0x54410008
      		Memory policy: ECC disabled, Data cache writealloc
      		CPU identified as i.MX6DL/SOLO, silicon rev 1.1
      		PERCPU: Embedded 7 pages/cpu @c1309000 s6592 r8192 d13888 u32768
      		Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 208128
      		Kernel command line: console=ttymxc1,115200 init=/init nosmp video=mxcfb0:dev=hdmi,1280x720M@60,bpp=32 video=mxcfb1:off fbmem=10M vmalloc=400M androidboot.console=ttymxc1 androidboot.hardware=freescale
