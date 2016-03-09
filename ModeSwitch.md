## Mode Control Switch ##

**Instructions**: This test shows the recorded state of your mode control toggle switch on your RC transmitter. Most people use a three-position switch, but it's possible to mix two toggle switches with your RC transmitter's programming to create six possible states.

Remember, the mode channel (typically channel 5) should be connected to APM's last RC input pins, which are marked IN7. Also, the position is reversed from that of the original ArduPilot: manual is furthest away from you in most RC transmitter defaults.

The meaning of those states is set in the config file tab, in this section:

```
#define POSITION_1 FLY_BY_WIRE_A
#define POSITION_2 FLY_BY_WIRE_A
#define POSITION_3 AUTO
#define POSITION_4 AUTO
#define POSITION_5 MANUAL		// Software Manual - recommended
#define POSITION_6 MANUAL		// Hardware Manual - you can put something else here, but the hardware multiplexer will force manual control
```

In the above case, the user only has a three position switch, so the functions are duplicated for each pair.



**Typical data:**

![http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/controltest.png](http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/controltest.png)

**Troubleshooting:** If this isn't working, check these things:

  * Are the cables plugged in the right way aroud? Black should be closest to the board
  * Are you using buggy firmware from the first APM batch. If so, you can update your firmware by following the instructions [here](http://code.google.com/p/ardupilot-mega/wiki/Encoder).
  * Are you sure your toggle switch is outputting on Channel 5? RC transmitters can assign that switch to any channel you want, so double check that the switch is bound to the right channel.