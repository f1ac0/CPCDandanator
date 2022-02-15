# CPCDandanator
This project is a personal version of the famous "CPC Dandanator! Mini" by Dandare : http://www.dandare.es/Proyectos_Dandare/CPC_Dandanator%21_Mini.html .

Facts about this project :
- I wanted badly to try out "Sword of Ianna", so I built it on breadboard with the parts I had in stock :
- Flash ROM in DIP format,
- XC9572XL in VQ64 package (although Kicad files with VQ44 are also provided).

It ended on its own PCB with additional changes : 
- It can accommodate a card-edge connector or a pin header.
- I used a crystal-less CH340E to reduce BOM. WARNING: serial/USB communication does not work for me :( 

# Disclaimer
This is a hobbyist project, it comes with no warranty and no support. Also remember that the Amstrad machines are about 30 years old and may fail because of such hardware expansions.

The original "CPC Dandanator! Mini" is "a Public Domain project and all code/hardware/description is free to use with no restriction whatsoever" thanks to its author.

This version is not connected to Dandare, please don't bother him with issues you might have because of it.

If you find it useful and want to reward someone : reward the original author.

# BOM
- 1x XC9572XL CPLD
- 1x DIP SST39SF040, with socket
- 1x CH340E USB-serial converter + 1x micro USB connector
- 1x 3.3v LDO, either SPX3819M5-L-3-3 or XC6206P332MR
- 2x 1uF (or more) 0805 capacitors
- 5x 100nF 0805 capacitors
- 2x 10k 0805 resistor
- 1x 50 pins card-edge connector, or pin headers + cable to match your CPC

# Making it
Components are SMD, and have thin pin pitch. You need to know what you are doing.

Check for shorts at least between 5V, 3.3V, and GND traces before applying power !

The programming port does not need to be soldered since it needs to be programmed just once : you can just hold it in place during the few seconds required for programming.

XC9572XL code is generated and built into xsvf using Xilinx ISE 14.7 IDE then iMPACT. It requires to set "Logic optimization" to "Density". "Macrocell power setting" can be "Low" an "Slew rate" to "Slow". Original xsvf file provided by the author may work but I never tried it.

There are several methods to program the CPLD. I personally use xsvfduino : https://github.com/wschutzer/xsvfduino

CH340E and USB connector are optional if you do not plan to use USB. They dit not work for me anyway.

# Using it
This part is the same as the original device. Enjoy !

If you are a linux user like me, here is a tip to use the java application on modern systems without breaking the latest openjre provided by your distro :
- get oracle jre (for example from http://download.macromedia.com/pub/coldfusion/java/java8/8u271/jre/jre-8u271-linux-x64.tar.gz) and untar it
- start the app with ```~/jre1.8.0_271/bin/java -jar dandanator-cpc-2.3.jar```

