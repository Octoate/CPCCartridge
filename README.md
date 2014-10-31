CPCCartridge
============

This repository contains two projects to create a Amstrad Plus / Amstrad GX4000 cartridge, which
I started in 2010. Anyway, I had no time to finish or produce them, so maybe there is somebody
else interested in them and wants to take over :-)!?


Simple Cartridge
================

In the "simple-cartridge" folder, you will find the schematics and board layout for a simple flash
cartridge for the Amstrad Plus / Amstrad GX4000 cartridge. You can equip it either with an CPLD
(XC9536) with ACID protection emulation (see http://www.octoate.de/wp/articles/acid-verilog-code/
for more information) or a real ACID protection chip.


Flash Cartridge
===============

Also designed in 2010, the folder "flash-cartridge" contains an idea for a USB programmable flash
cartridge. The idea was to connect the cartridge to a PC and program it and - after that -, you can
connect it to the Amstrad Plus or the Amstrad GX4000 and run your program / game.
I decided to use an Atmel ATMega8 for the USB connection and to program the flash EPROM (e.g. an
AT29C040). Because the ATMega8 does not support USB out of the box, I intended to use the software 
V-USB stack for Atmel microcontrollers by Obdev (http://www.obdev.at/products/vusb/index.html). To
save pins on the microcontroller, I decided to use some shift-registers, which can be accessed by
the hardware SPI of the ATMega microcontroller.
In the schematics you can find the CARTGND signal, which is connected to GND1 in the schematic and to
PD7 of the ATMega microcontroller. The idea about this is to detect if the cartridge is connected
to the Amstrad Plus / Amstrad GX4000. The internal pull-up of PD7 normally will return "high" if
you read PD7, but if it is connected to the CPC, you will get a "low" value on this pin, which you
can use to disconnect the microcontroller from the bus.
A Xilinx XC9536 VQFP is used for ACID protection emulation.