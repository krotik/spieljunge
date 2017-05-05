Spieljunge
==========
Spieljunge is a hardware design modeling a retro handheld console with a Raspberry Pi in a custom 3D printed case.

<img src="/pics/spieljunge_028.jpg" height="400"> <img src="/pics/spieljunge_030.jpg" height="400">

Utilising the power of a Raspberry Pi 3 with Raspbian & RetroPie as operating system this handheld can emulate many different retro platforms.


Requirements
------------
You need basic soldering skills and should not be afraid of fiddeling with small electronics. Proper tooling is key: a good multimeter with logic testing capabilities, pliers, screwdrivers, some helping hand stand ([example](https://www.amazon.co.uk/gp/product/B000MRFVXM)), solder iron & solder and PATIENCE!

<img src="/pics/spieljunge_001.jpg" height="400">

Features
--------
- No need to destroy existing hardware - all used components can be bought new
- 3.5" Display for a high quality display of graphics
- 15 buttons connected via the GPIO of the Raspberry Pi - simulating keyboard input
- Audio output via an internal speaker which can be switched off
- Using Raspbian with RetroPie as OS
- Powerful hardware which provides smooth emulation
- Raspberry Pi supports headphones, HDMI and Bluetooth


Components
----------

### General

- 1.75mm PLA Filament for the case and buttons (<a href="https://www.amazon.co.uk/gp/product/B00QIPVRN0">Example</a>)

- Fast Universal Charger Micro USB 5V 2000mA / 2A to provide power and charge the battery (<a href="https://www.amazon.co.uk/gp/product/B01CPIECRQ">Example</a>)

- Lithium Ion Battery Pack - 3.7V 4400mAh (<a href="https://www.amazon.co.uk/gp/product/B00PKFJQ0U">Example</a>)

- Solder Finished Prototype PCB for DIY 5x7cm Circuit Board Breadboard to place the buttons on (<a href="https://www.amazon.co.uk/gp/product/B00FXHXT80">Example</a>)

### Buttons

- Rugged Metal On/Off Switch with Red LED Ring the on/off switch for the handheld (<a href="https://www.amazon.co.uk/gp/product/B017MT6AHI">Example</a>)

- Tactile Switch Buttons 6mm slim (<a href="https://www.amazon.co.uk/gp/product/B011OB6M3M">Example</a>)

- SS22F25-G7 2 Position DPDT 2P2T Panel Mount Mini Slide Switch the on/off switch for the internal speaker (<a href="https://www.amazon.co.uk/gp/product/B008DFYLU4">Example</a>)

### Electronic components

- Raspberry Pi 3 Model B Quad Core CPU 1.2 GHz 1 GB RAM (<a href="https://www.amazon.co.uk/gp/product/B01CCOXV34">Example</a>)

- NTSC/PAL (Television) TFT Display - 3.5" Diagonal (<a href="http://www.exp-tech.de/ntsc-pal-television-tft-display-3-5-diagonal">Example</a>)

- LM2577 Boost Step Up Module Voltage Regulator 3.5-30V To 4-30V DC Converter to supply the display with 6V power (<a href="https://www.amazon.co.uk/gp/product/B00HLZNS0Q">Example</a>)

- Adafruit PowerBoost 1000 Charger - Rechargeable 5V Lipo USB Boost @ 1A - 1000C to provide 5v power (<a href="https://www.amazon.co.uk/gp/product/B010M8UVYY">Example</a>)

- Mono 2.5W Class D Audio Amplifier - PAM8302 for the internal speaker (<a href="https://www.amazon.co.uk/gp/product/B00PY2YSI4">Example</a>)

- Adafruit Mini Metal Speaker w/ Wires - 8 ohm 0.5W  (<a href="https://www.amazon.co.uk/gp/product/B00N41FXC2">Example</a>)

### Screws

- 4 x M3x25mm screws to connect top and bottom of the case (<a href="https://www.amazon.co.uk/gp/product/B00OBFRJ04">Example</a>)

- 8 x #6-32 UNC standard PC screws to connect the button boards (<a href="https://www.amazon.co.uk/dp/B01N3Z17GK">Example</a>)

- 4 x M2x3mm screws to connect the Raspberry Pi (<a href="https://www.amazon.co.uk/gp/product/B06XJJB37W">Example</a>)

- 2 x M2x8mm screws to connect the power supply board (<a href="https://www.amazon.co.uk/gp/product/B06XJJB37W">Example</a>)


Construction
------------
The actual construction was a lot of trial and error. You might need to print the case several times to see what is the best fit.

<img src="/pics/spieljunge_012.jpg" height="300"> <img src="/pics/spieljunge_014.jpg" height="300">

### 3D Printing the Case and Buttons
The case for Spieljunge was printed using a Prusa3D MK2 printer with PLA filament. The modeling was done in Blender3D - 
the source file of the model can be found here: <a href="src/sj_model.blend">Model</a> and <a href="src/sj_buttons.blend">Buttons</a>.

<img src="/pics/spieljunge_018.jpg" height="300"> <img src="/pics/spieljunge_019.jpg" height="300">

The STL file containing the 3D model for the case can be found <a href="/stl">here</a>. The printable gcode which was 
used to print the case can be found <a href="/gcode">here</a> (note: these are specific to the used 3D printer). 

### Building the buttons

Use the Breadboard to fit the Tactile Switch Buttons under the printed buttons.

<img src="/pics/spieljunge_017.jpg" height="300"> <img src="/pics/spieljunge_016.jpg" height="300">

Again this is a lot of trial and error until it fits. The Tactile Switch Buttons are then connected to the GPIO ports on the PI (I soldered the wires on the Breadboard and used normal PC jumpers for the Pi's GPIO). Each Switch is connected to a GPIO port and ground.

<img src="/pics/spieljunge_023.jpg" height="300"> <img src="/pics/spieljunge_024.jpg" height="300">

### Internal wiring

The complete wiring should look like this (click to expand):

<a href="/pics/wiring.svg"><img src="/pics/wiring_thumbnail.jpg" height="300"></a>

1. Start off by soldering the composite out and the audio to the Raspberry Pi.
```
PP6  = Ground
PP24 = Video
PP25 = Left audio
PP26 = Right audio
```
<a href="/pics/wiring.svg"><img src="/pics/pi_back_solder_points.jpg" height="300"></a>

2. Connect now the Power to the Pi using GPIO pins 4 (for +5V) and 6 (for ground) to the PowerBoost module. Plugging a suitable 5V power supply into the PowerBoost charger should now power the Raspberry Pi.

4. Connect now the On/Off switch - you should now be able to switch power.

5. Add now the wiring for the PAM8302 Audio Amplifier. You should now be able to output sound from the Raspberry Pi. Note: The audio/video socket is switched off by default if you use the HDMI output.

<img src="/pics/spieljunge_000.jpg" height="300">

6. It is now time to connect the display. Be sure to have the correct output on the Boost Step Up Module (between 6V and 7V). You should now be able to see the Pi's output.

<img src="/pics/spieljunge_004.jpg" height="300">

7. Finally, connect the Lithium Ion Battery Pack to the PowerBoost Charger.

<img src="/pics/spieljunge_026.jpg" height="300">


Software Installation
---------------------
For the software of Spieljunge I started with a vanilla Raspbian "Lite" ([link](https://www.raspberrypi.org/downloads/raspbian/)). Use your favourite flash tool (for example [rufus](https://rufus.akeo.ie/)) to create a bootable SD card for your Pi.

### Converting a GPIO button press into a keyboard stroke

One of the most daunting things on the software side of this project is to convert GPIO input into actual keystrokes which are understood by RetroPie and its emulators. A bit of background: The Linux kernel has a "subsystems" called evdev which makes raw input available in /dev/input/... Most games and emulators will include libraries which read directly from there when they parse input. In order for the GPIO buttons to work we want them to "emulate" a keyboard. There are several libraries available which do exactly that - for example: [pikeyd](https://github.com/mmoller2k/pikeyd), [WiringPi](https://projects.drogon.net/raspberry-pi/wiringpi/) or [Adafruit-Retrogame](https://github.com/adafruit/Adafruit-Retrogame). Unfortunately, most of these libraries require quite a bit of setup. For Spieljunge I decided for a more simple solution: a python library and a script. 

The python script should use a special linux kernel module called uinput which allows to "emulate" input devices from the user space. Since it is a standard Linux module it is well supported. There is a python library called [Python-uinput](https://github.com/tuomasjjrasanen/python-uinput) which provides python bindings for uinput. Although it is available via "pip install", I decided to compile it from source since I want to apply a little patch. So here we go:

- Make sure uinput is loaded on startup. Add the line "uinput" to your /etc/modules and reboot. You can check if uinput is loaded by running:
```
lsmod
```

- Download the latest source code for [Python-uinput](https://github.com/tuomasjjrasanen/python-uinput) from its Github page (Clone or download -> Download ZIP) and extract it.

- Optional: To emulate a keyboard more accurately you may want to activate key repeat for uinput. See this [forum thread](https://www.raspberrypi.org/forums/viewtopic.php?t=45041&p=357808) for more information on this. To do this we need to patch Python-uinput. Either apply the following patch:
```
diff --git a/libsuinput/src/suinput.c b/libsuinput/src/suinput.c
index 8d5fb71..4fa643a 100644
--- a/libsuinput/src/suinput.c
+++ b/libsuinput/src/suinput.c
@@ -179,6 +179,10 @@ int suinput_enable_event(int uinput_fd, uint16_t ev_type, uint16_t ev_code)
                 return -1;
         }

+        if (ev_type == EV_KEY) {
+                ioctl(uinput_fd, UI_SET_EVBIT, EV_REP);
+        }
+
         switch (ev_type) {
         case EV_KEY:
                 io = UI_SET_KEYBIT;
```
or directly edit the file python-uinput/libsuinput/src/suinput.c and add the plus marked lines from above.

- You can now run the usual setup.py build/install to install Python-uinput:
```
python setup.py build
python setup.py install
```
Verify that Python-uinput is installed by running "python" and in the interpreter run "import uinput" - if you don't get an exception back things should be ok.

- In the moment many emulators won't be able to see python-uinput generated events as keyboard events. The solution to this is to add a udev rule. Create the file: /etc/udev/rules.d/10-spieljunge.rules with the following content:
```
SUBSYSTEM=="input", ENV{ID_INPUT_KEYBOARD}="1"
```
This basically says that all things from the INPUT subsystem should be treated as keyboard input.

- It is now time to write the python script which maps GPIO input to keyboard events. Create the file /home/pi/gkeybrd.py with the following content:
```
# Keyboard for GPIO

import RPi.GPIO as GPIO
import time
import uinput

# Key bindings

keys = {

    # Cursor keys

    2 : uinput.KEY_UP,
    17 : uinput.KEY_DOWN,
    3 : uinput.KEY_LEFT,
    4 : uinput.KEY_RIGHT,

    # Select button

    22 : uinput.KEY_ENTER,

    # Trigger buttons

    5 : uinput.KEY_B,
    6 : uinput.KEY_C,
    11 : uinput.KEY_D,
    9 : uinput.KEY_E,

    # Select / Start button

    13 : uinput.KEY_F,
    10 : uinput.KEY_G,

    # Back buttons

    18 : uinput.KEY_H,
    15 : uinput.KEY_I,
    23 : uinput.KEY_J,
    14 : uinput.KEY_K,
}

state = {}

GPIO.setmode(GPIO.BCM)

device = uinput.Device(keys.values())

for i, _ in keys.iteritems():
  GPIO.setup(i, GPIO.IN, pull_up_down = GPIO.PUD_UP)

while True:

    for i, k in keys.iteritems():
        res = GPIO.input(i)

        # Uncomment this to find out which button is which GPIO.input
        # print "press %s - %s" % (i, res)

        if state.get(i) != res:

            if res == 1:
                device.emit(k, 0)
                print "emit %s 0" % i
            else:
                device.emit(k, 1)
                print "emit %s 1" % i

            state[i] = res

        time.sleep(0.004)

GPIO.cleanup()
```
You will need to modify the script for your device. Uncomment the print line and run the script to see which button is associated with a particular GPIO number. Modify the "keys" dictionary accordingly.

- After creating the script make sure it is run from the start. Add the following line to /etc/rc.local before the "exit 0" line:
```
nohup python /home/pi/gkeybrd.py &
```

- After a reboot your button presses should be visible on the normal console.

### Installing RetroPie

To install RetroPie I followed the "Manual Installation" [guide](https://github.com/retropie/retropie-setup/wiki/Manual-Installation) with "Boot to emulationstation" [link](https://github.com/RetroPie/RetroPie-Setup/wiki/FAQ#how-do-i-boot-to-the-desktop-or-kodi) in combination with the "First Installation" [guide](https://retropie.org.uk/docs/First-Installation/). Since the setup of the input controller is part of the installation I recommend to sort out the "GPIO as keyboard" before installing RetroPie.
