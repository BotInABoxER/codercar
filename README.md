# Project Rover
Project Rover, the newest product from Bot-In-a-Box Educational Robotics!

<a href="https://botinabox.ca/wp-content/uploads/2019/03/project-rover-logo.png" align="center"></a>


From [https://www.thingiverse.com/thing:3334545](https://www.thingiverse.com/thing:3334545)

Powered by an Orange Pi Zero, Project Rover is an [Armbian](https://github.com/armbian)-compatible educational robotics kit that is modular, Wifi-enabled, works with Node-RED, and includes a lid with holes for M3 screws that can be used to mount any manner of sensors, servos, and electronics. 

# Materials/Tools:

You'll need the following to get the most out of the kit:

An Orange Pi Zero with 2x13 headers (like from [https://ebay.to/2Qp88bp and https://ebay.to/2F9WcZc](https://ebay.to/2Qp88bp and https://ebay.to/2F9WcZc))

A USB Power Bank (At least 5V) ([https://ebay.to/2RB6c4g](https://ebay.to/2RB6c4g) with 2 of these: [https://ebay.to/2BYSM8w](https://ebay.to/2BYSM8w) should do the trick)

A Micro USB Cord (a little one like [https://ebay.to/2LSCoeq](https://ebay.to/2LSCoeq) maybe)

4 DC Toy Motors with wheels (like from [https://ebay.to/2SE9np6](https://ebay.to/2SE9np6))

2 L9110 Dual-Motor H-Bridge Controllers (like from [https://ebay.to/2GT3G5d](https://ebay.to/2GT3G5d))

12 30cm Female-to-Female Dupont Cables (like from [https://ebay.to/2R6mRxn](https://ebay.to/2R6mRxn))

8 Male-to-Male Dupont Cables

A Soldering Iron and some Solder

28 10mm M3 screws ([https://amzn.to/2Rcb5BC](https://amzn.to/2Rcb5BC))

An M3 Allen Key

A little Philips Screwdriver

A Wire Stripper

A Micro SD Card - at least 4GB ([https://amzn.to/2s7EA8E](https://amzn.to/2s7EA8E))

# Printing:

The body prints in two pieces without supports, but the wheel mounts to extend the axles will probably print short-side-down sideways with supports.

# How to Put Together

Screw in the Motors and the L9110s (the two screws on each controller nearest to the big green plugs go in upside-down) after soldering stripped Male Dupont Cables onto each of the motors' contacts, then plug the cables into the Motor Controllers (you'll need the screwdriver to keep them in place).

Flash the Orange Pi Zero's SD Card with some kind of Linux, preferably Armbian Stretch ([https://www.armbian.com/orange-pi-zero/](https://www.armbian.com/orange-pi-zero/)) using Etcher ([https://etcher.io](https://etcher.io)).

Screw in the Orange Pi Zero and plug it in.

Find a way to SSH into the Orange Pi Zero by connecting it via Ethernet to your router, then using a program like Angry IP Scanner to find its address when it boots up (you'll see a blinking green LED on a successful boot) - [https://angryip.org/download/](https://angryip.org/download/). Alternatively, use some kind of UART-to-USB adapter with Putty ([https://www.putty.org/](https://www.putty.org/)) to initiate a Serial connection - check Device Manager in Windows 10 to find the COM port to which you'll need to connect. Either way, you'll have to login as 'root' with the password '1234' then create a password and user account to use.

Afterwards, do a 'sudo apt update' and 'sudo apt upgrade' from the command line to get the latest updates and fixes for Armbian. Use nmtui or something like that to connect to a Wifi network. install Node.js 8.x ([https://www.arduinoslovakia.eu/blog/2017/9/orange-pi-zero-a-nodejs?lang=en](https://www.arduinoslovakia.eu/blog/2017/9/orange-pi-zero-a-nodejs?lang=en)) then install Node-RED ([https://nodered.org/docs/getting-started/installation](https://nodered.org/docs/getting-started/installation)) and then install the specialized Orange Pi library from the ~/.node-red folder ([https://flows.nodered.org/node/node-red-contrib-opi-gpio](https://flows.nodered.org/node/node-red-contrib-opi-gpio)).

Open up a browser window on another computer on the same network as the Orange Pi Zero, go to http://'the-ip-address-of-your-opizero':1880 and you should be met with the Node RED interface.

You can then fiddle around with the Orange Pi GPIO interface, turning pins on/off using Javascript (connect the pins from the L9110s to the proper pins on the Orange Pi Zero, select Orange Pi Zero+ in the Orange Pi GPIO menu, and use the lookup table at the Sunxi Linux Wiki for reference: [http://linux-sunxi.org/Xunlong_Orange_Pi_Zero](http://linux-sunxi.org/Xunlong_Orange_Pi_Zero)).

You can use the lid to hold the battery bank, screwing the lid in with 3 screws,
and there's space to mount sensors, servos, an LED matrix, or really anything. At some point I'll probably release an update with some mounts.

At any rate, I hope you get some enjoyment out of this crazy kit, and that it maybe helps you learn something about building 3D-printed cars.

Sincerely, Matthew Piercey
