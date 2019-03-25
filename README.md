# Project Rover
Project Rover, the newest product from Bot-In-a-Box Educational Robotics!

<p align="center"><img src="https://botinabox.ca/wp-content/uploads/2019/03/project-rover-logo.png" alt="Project Rover's Logo"></p>

From [https://www.thingiverse.com/thing:3334545](https://www.thingiverse.com/thing:3334545)

Powered by an Orange Pi Zero, Project Rover is a [DietPi](https://dietpi.com/)-compatible educational robotics kit that is modular, Wifi-enabled, works with Node-RED, and includes a lid with holes for M3 screws that can be used to mount any manner of sensors, servos, and electronics. 

# BOM/Tools:

You'll need the following to get the most out of the kit:

A Raspberry Pi Zero WH (available in Canada and the US from [https://buyapi.ca](http://bit.ly/buyapi-botinabox)

A USB Power Bank with 2 18650 batteries

A Micro USB Cord

An MPU6050 Accelerometer/Gyro Breakout Board (with soldered headers)

4 DC Toy Motors with a 120:1 gear ratio

2 L9110 Dual-Motor H-Bridge Controllers

Some 30cm Female-to-Female Dupont Cables

Some 8 Male-to-Male Dupont Cables

A soldering iron and some solder

A bevy of 10mm M3 screws (

An M3 Allen Key

An M2.5 Allen Key

A little flathead screwdriver

A wire stripper

A MicroSD card - at least 8GB is recommended

# Printing:

In the STLs file, you'll find seven 3D models in the Stereolithography format. Most 3D Printers don't accept STLs directly, so you'll most likely need to use a slicer program like (Cura)[https://ultimaker.com/en/products/ultimaker-cura-software] to export them to a GCODE file for the specific printer you're using. 

The files were designed to be printed without supports at a low-ish resolution, and their dimensions are in MM. By low-ish I mean about .2mm/layer. I printed these with a Wanhao Duplicator i3 using PLA at 193°C, if that means anything to you.

First of all, print the Body, which is the main component of the Rover. It has mounts for four motors, two motor controllers, and a Raspberry Pi Zero WH. 

Secondly, the Top Mount screws on to the posts in the middle of the Rover, held on by four M3 screws. On top of this mount are screw holes for placing the Battery Box, as well as the Accelerometer. At this time, that's all that goes up there, though I'm working on thinking of what else I could put up there.

Third, the Battery Box and its corresponding Lid screw on top of the Top Mount. The Lid slides onto the box after it's screwed in place. A word of caution: it might be tight. The first time I printed the lid I had to tap it in with a small hammer, and I needed to grab it with a pair of vice grips and gently tap those with the hammer to get it off. At some point, I should probably fix it, but it works for now since it fits and won't come off easily.

The Accelerometer Mount fits in the middle of the Top Mount, and is attached by two screws. An Accelerometer is of course optional, but can come in handy.

There are two places on the Body that support a Front Mount: one above each motor controller mount. Right now, I don't have anything that goes on top of them, but feel free to experiment.

Finally, any good rover needs Wheels, and these should fit snugly onto the motors' shafts. Yes, I know, you can buy these motors with wheels, but I'm telling you now that they won't fit properly, since the motor mounts get in the way. Maybe this is a design flaw, maybe it's just something we're going to need to work around, I don't know. But, for now at least, the printed Wheels should do the trick.

# Post-print Setup

Screw in the Motors and the Motor Controllers (Motors take three M3s, Motor Controllers take two M3s and two M2.5s) after soldering stripped Male Dupont Cables onto each of the Motors' contacts, then plug the cables into the Motor Controllers (you'll need the flathead screwdriver to tighten the screw terminals to keep the wires in place).

Flash the Raspberry Pi Zero WH's SD Card with some kind of Linux, preferably Diet-Pi ([https://dietpi.com/](https://dietpi.com/)) using an imaging program like Etcher ([https://etcher.io](https://etcher.io)) or dd if you're on Linux and know what you're doing.

Alternatively, you could use something like PiNN Lite from (https://sourceforge.net/projects/pinn/)[https://sourceforge.net/projects/pinn/] to install Diet-Pi (or a number of other Linux distros). This way might be easier, but it requires a working Internet connection, a Micro HDMI adapter and an HDMI cable, a TV or monitor with HDMI input, a USB keyboard, a USB mouse, and a Micro USB OTG hub. One of these days I'll get around to making up a decent tutorial for the installation process, but for now you should be able to figure it out if you've ever used NooBS on a Raspberry Pi.

Screw in the Raspberry Pi Zero WH with four M2.5 screws, and plug it in (preferably with an AC adapter, since you don't want the battery bank to run out during setup).

Find a way to SSH into the Raspberry Pi Zero WH. This can prove difficult, especially if you don't have a screen, keyboard, and mouse handy. One way to bypass this limitation is by connecting your Pi via a USB Ethernet plug to your router, then using a program like (Angry IP Scanner)[https://angryip.org/download/](https://angryip.org/download/ ]to find its IP address when it boots up. Alternatively, use some kind of UART-to-USB adapter with Putty ([https://www.putty.org/](https://www.putty.org/)) to initiate a Serial connection - check Device Manager in Windows 10 to find the COM port to which you'll need to connect. Either way, you'll have to login as 'root' with the password 'dietpi.' 

One really nice thing about DietPi is that it does a lot of the setup busyork for you, updates, upgrades, and all that. Once you have the option to install software, go to the Optimized for DietPi section in DietPi-Software, select Node-RED and the packages for GPIO and I2C support. Again, I'll get to making a decent tutorial one of these days...

At any rate, once the setup has fully completed, you can open up a browser window on another computer on the same network as the Pi, go to http://'the-ip-address-of-your-pi':1880 and you should be met with the Node-RED interface.

Click the three-bar button in the top-right of the window, and go to manage pallete. I recommend installing the Dashboard nodes then the UI builder nodes.

You can then fiddle around with the Raspberry Pi GPIO interface, turning pins on/off using Javascript (connect the pins from the L9110s to the proper pins on the Pi - GND to a GND pin, VCC to a 5V, and the other four pins from each controller to a GPIO pin (not GPIO 2 or 3 though; I'm pretty sure they're reserved for something).

After you've bulit a decent program, you can have some fun watching the Rover roll around on the floor based on your specifications.


# Coming Soon

You're probably looking at the Top Mount and thinking that there's space to mount sensors, servos, an LED matrix, or really anything. Sometime in the near future I hope to release a semi-major update with mounts for an Arduino Nano, LED Matrix, LCD screen, continuous-rotation servo, and a CMOS camera, so be on the look-out for those. 

Also, I'm still working on support for the MPU6050. I know there are a lot of libraries out there, some compatible with NodeJS, that support the board, but I haven't gotten around to testing them yet. When I do, I'll make sure to update this README.

At any rate, I hope you get some enjoyment out of this crazy kit, and that it maybe helps you learn something about building 3D-printed cars.

Sincerely, Matthew Piercey


**Disclaimer: This Readme includes Affilate Links**
