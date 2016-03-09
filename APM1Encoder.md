## Programming the Atmega328p (PPM encoder/failsafe) ##

**Note**: ArduPilot Mega 1.0 comes with the PPM encoder/failsafe pre-programmed, and most users will never need or want to modify it. (Indeed, the point of black-boxing the chip like this is people don't mess with the code and introduce bugs that could stop the failsafe from working properly).

However, some users may want to get into the code to change the way ArduPilot Mega interprets RC signals or may want to update to the latest version.
Some rare users did report receiver compatility problems with the old version (before ArduPPM). For most cases, ArduPPM did solve them.

ArduPPM is the official name for the newer generation firmwares that fit APM v1.0, APM 1.4, Phonedrone and futur boards. It has been designed from scratch with reliability as a top priority.
The official release of the encoder firmware is in the Downloads section as ArduPPM\_vx.x.xx\_ATMega328p.hex.
The official source code is in the Git repository :
http://code.google.com/p/ardupilot-mega/source/browse/#git/Tools/ArduPPM/ATMega328p. APM 1.0 and 1.4 boards need the ATMega328p version.

[Using the Atmel AVRStudio tools and AVR ISP MKII programmer](http://code.google.com/p/ardupilot-mega/wiki/AVRStudio)

[Using the low-cost BusPirate and free AVRDude tool](http://code.google.com/p/ardupilot-mega/wiki/BusPirate)

## Note on the correct LED operation of the ArduPPM firmware ##

For those looking at these instructions in order to upgrade their PPM firmware to gain PPM pass-through and other features offered:

The ArduPPM firmware, controls a blue LED right under the word PPM in the top left of the ArduPilotMega board.

Blue status LED is used for status reports :

**slow to fast blinking according to throttle channel position** very fast blinking if missing receiver servo signals, or if the servo signals are wrong (invalid pulse widths)

## Radio Passthrough mode (mux) (only for planes !) ##

This mode is described as hardware failsafe in Arduplane terminology.

Radio Passthrough mode is trigged by channel 8 > 1800 us.

Blue status LED has different behavior in passthrough mode :

**If throttle position < 1200 us, status LED is off** If throttle position > 1200 us, status LED is on

## Failsafe mode ##

If a receiver servo channel is lost, the last known channel position is used.
If all contact with the receiver is lost, an internal failsafe is trigged after 250ms.

Default failsafe values are:

Throttle channel low (channel 3 = 900 us)

Mode Channel set to flight mode 4 (channel 5 = 1555 us)

All other channels set to midstick (1500 us)


## PPM passthrough mode (single cable from RX! ) ##

If your receiver has a PPM sum signal output, it is now possible to pass on the PPM signal from servo channel 1 to the PPM pin (APM atmega1280/2560 PPM decoder).

To enable PPM passthrough, short the servo input channel 2 & 3 signal pins together using a jumper cable. Channel 1 signal pin is then assumed to be 8Ch PPM.

Please note that the PPM sum signal must be standard 8 channel PPM to work with the APM PPM decoder.

In this mode, the blue LED will blink like this  : Long - Short - short