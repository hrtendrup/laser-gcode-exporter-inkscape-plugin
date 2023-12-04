About This Project
------------------
This project was intended to build an all in one exporting plugin for laser cutters and Inkscape 1.3.1. The code has been updated (or will be) to support python3. 

The plugin builds gcode that is compatible with a fork of Marlin designed to run on laser cutters found at https://github.com/TurnkeyTyranny/buildlog-lasercutter-marlin .

This is forked off of https://github.com/TurnkeyTyranny/laser-gcode-exporter-inkscape-plugin
The work is fantastic and I'm happy to build upon in (in whatever feeble way I may)


Installation
------------


Usage and Setup
---------------
I recommend starting with this cutting surface and doing your designs in it. Its setup to match the size of the K40 Laser cutter bed : https://github.com/TurnkeyTyranny/laser-gcode-exporter-inkscape-plugin/blob/master/designs/cutting_surface.svg


Alternatively if you're setting up your own new inkscape job first press CTRL+Shift+d, choose the tab called 'page' and set your project units in the 'custom size' area to be 'px'. You can set the 'Default Units' option to be mm, inch or px. The 'Default Units' are the ones displayed on your rulers.

Name your layer in Inkscape like: 10 [feed=600,ppm=40]

This will set the power level to 10%, the feedrate to 600mm per minute and will fire at 40 pulse per millimetre in 60us duration pulses. PPM is ignored for rasters.
The ppm option is optional, if you do not specify it then the laser will default to continuous wave mode.
If you do not name your layer in this way then the script will use the default settings specified in the dialog box.


When you're ready to export your objects, images or paths just select the items you would like to be exported by dragging over them or holding shift to select multiple and then run the plugin under under Extensions Menu -> Export -> Turnkey Laser Exporter. 
![alt tag](https://raw.githubusercontent.com/TurnkeyTyranny/laser-gcode-exporter-inkscape-plugin/master/instructions.png)


Sending the file to your laser
------------------------------
You can send the file to your laser by serial (USB cable) or SD memory card. 

1) Via USB cable
* Download repetier host and install it on your PC - http://www.repetier.com/download/
* Open the software and set the port of your laser in the options. It will typically be COM7 - otherwise it's the same as what your programmed your Arduino on originally. The port speed should be set to 115200
* Press the connect button, it will turn green.
* Open your gcode file you created earlier and press the print button. Your laser will now burn your instruction set.


Alternatively you can use pronterface http://www.pronterface.com/index.html#download . You must ensure you check the box for Pronterface under 'Advanced' tab in the exporter plugin. It is checked by default.

2) Via SD Memory card
* Place the file onto your SD card
* Insert it into your ramps SD card reader.
* Select the file from the ramps LCD menu and print.

Keyboard Shortcut
-----------------

You may find it handy to assign the extension to a keyboard shortcut. 
Include something like the following line to your inkscape keys 
preferences file (this will bind the plugin to Ctrl+\):

<bind key="backslash" modifiers="Ctrl" action="org.thinkhaus.filter.thlaser"
display="true"/>

You can find your keyboard preferences file:

* On Linux: ~/.config/inkscape/keys/default.xml
* Windows:  %UserProfile%\Application Data\Inkscape\keys\default.xml

If that file doesn't exist, create it and include the following:

<?xml version="1.0"?>
<keys name="My Keys">
<bind key="backslash" modifiers="Ctrl" action="org.thinkhaus.filter.thlaser"
display="true"/>
</keys>


Attribution
--------------------
The project is built on work by other people, thanks go out to the effort they put in before me.
Thanks to work by https://github.com/ajfoul , Thinkhaus and Lansing Makers Network
This script is released under the license GPL v2.

Change log
--------------------
03-Dec-2023 - initial fork and updated fhis file. much more work to be done


