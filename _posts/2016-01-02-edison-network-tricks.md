---
title: Edison Network tricks
tags: network
layout: post
---

The Edison supports Wifi and Bluetooth out-of-the-box. And, with the [Edi-Expand](http://www.tektyte.com/#about) you can additionally get Ethernet for Edison.

Enough reasons to quickly gather some thoughts about connectivity setups with the Edison.

# Edison as Access Point

First, it can be interesting to have the Intel Edison working as Wifi Access Point (AP mode) or Hotspot. You will find some ideas in the [thread](https://communities.intel.com/thread/55610?start=0&tstart=0). The main command for the hotspot mode is:

    # systemctl start hostapd
    
This starts the AP mode and you could easily use it to serve pages to your mobile phone.    


# SSH into the Edison

Once you have a network connection, how can you SSH into the Edison via Wifi? One option is by defining an alias, e.g. on your local laptop:

   $ alias ssh_edison="ssh -o StrictHostKeyChecking=no root@edison.local"
   $ ssh_edison

Note: Depending on your Edison configuration, you have to edit the systemd service to allow ssh without a password.
On the Edison:

   # vi /lib/systemd/system/sshd.socket

In this file, you comment out BindToDevice=usb0 depending on your security preferences. 


# Setup routes

Depending on your network configuration, you must check that routes are setup correctly. An important route is the "default" route. More information about it [here](http://www.cyberciti.biz/faq/linux-setup-default-gateway-with-route-command/) and [here](https://communities.intel.com/thread/76067?start=0&tstart=0).

The default gateway can be added with:

   root@edison:~# route add default gw 192.168.2.1

Now, a working routes table can look like:

   root@edison:~# netstat -rn
   Kernel IP routing table
   Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
   0.0.0.0         192.168.1.1     0.0.0.0         UG        0 0          0 wlan0
   192.168.1.0     0.0.0.0         255.255.255.0   U         0 0          0 wlan0
   192.168.2.0     0.0.0.0         255.255.255.0   U         0 0          0 usb0

Or:

   root@edison:~# route
   Kernel IP routing table
   Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
   192.168.2.0     *               255.255.255.0   U     0      0        0 wlan0

By adding default routes, you can also share internet through another machine, e.g. as described [here](http://cylonjs.com/documentation/platforms/edison/).

Last, it might be important to setup a DNS service.

More info in:

   /etc/resolv.conf


# ifconfig

To debug settings, it is always helpful to do a quick ifconfig:

    root@eddie:~# ifconfig
    lo        Link encap:Local Loopback
              inet addr:127.0.0.1  Mask:255.0.0.0
              inet6 addr: ::1/128 Scope:Host
              UP LOOPBACK RUNNING  MTU:65536  Metric:1
              RX packets:3 errors:0 dropped:0 overruns:0 frame:0
              TX packets:3 errors:0 dropped:0 overruns:0 carrier:0
              collisions:0 txqueuelen:0
              RX bytes:120 (120.0 B)  TX bytes:120 (120.0 B)
    
    sit0      Link encap:UNSPEC  HWaddr 00-00-00-00-31-00-66-65-00-00-00-00-00-00-00-00
              inet6 addr: ::127.0.0.1/96 Scope:Unknown
              UP RUNNING NOARP  MTU:1480  Metric:1
              RX packets:0 errors:0 dropped:0 overruns:0 frame:0
              TX packets:0 errors:6 dropped:0 overruns:0 carrier:0
              collisions:0 txqueuelen:0
              RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
    
    usb0      Link encap:Ethernet  HWaddr 4a:08:f5:85:7a:5e
              inet6 addr: fe80::4808:f5ff:fe85:7a5e/64 Scope:Link
              UP BROADCAST MULTICAST  MTU:1500  Metric:1
              RX packets:62 errors:0 dropped:0 overruns:0 frame:0
              TX packets:24 errors:0 dropped:0 overruns:0 carrier:0
              collisions:0 txqueuelen:1000
              RX bytes:14192 (13.8 KiB)  TX bytes:4614 (4.5 KiB)
    
    wlan0     Link encap:Ethernet  HWaddr 78:4b:87:a6:3a:6f
    
              inet addr:192.168.42.1  Bcast:192.168.42.255  Mask:255.255.255.0
              inet6 addr: fe80::7a4b:87ff:fea6:3a6f/64 Scope:Link
              UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
              RX packets:0 errors:0 dropped:0 overruns:0 frame:0
              TX packets:59 errors:0 dropped:0 overruns:0 carrier:0
              collisions:0 txqueuelen:1000
              RX bytes:0 (0.0 B)  TX bytes:11720 (11.4 KiB)
    
    
Note, coming from an Raspberry Pi or Beaglebone you don't have a file to look default mappings of network interfaces. So, you might see:

   ifdown: can't open '/etc/network/interfaces': No such file or directory

However, you have a system service that you can probe:

    
    root@eddie:~# systemctl status wpa_supplicant.service
    
    root@eddie:~# systemctl status -l wpa_supplicant.service

And, a command 

     
     
     root@eddie:~# wpa_cli status
     Selected interface 'wlan0'
     bssid=bc:05:43:6a:24:9e
     ssid=WLAN-xxxx
     id=10
     mode=station
     pairwise_cipher=CCMP
     group_cipher=TKIP
     key_mgmt=WPA2-PSK
     wpa_state=COMPLETED
     ip_address=192.168.2.118
     p2p_device_address=7a:4b:xx:xx:xx:6f
     address=78:4b:87:xx:xx:6f


Note, if you see that the following command does not work:

    # configure_edison --version 
    
You should upgrade your firmware.

# Ethernet with edison

To come:

* http://www.tektyte.com/docs/docpages/edi-expand/gettingstarted.html#gettingstarted
