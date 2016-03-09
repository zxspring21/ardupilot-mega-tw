## Xplane setup instructions (for trunk code) ##

Use a APM\_Config.h file that includes this:

```
#define HIL_PROTOCOL        HIL_PROTOCOL_MAVLINK
#define HIL_MODE            HIL_MODE_ATTITUDE
#define HIL_PORT            0
#define GCS_PROTOCOL        GCS_PROTOCOL_MAVLINK
#define GCS_PORT            3
```

  * Set up the Xplane settings as shown in the [wiki](http://code.google.com/p/ardupilot-mega/wiki/Xplane).  The Net Connections screens are a bit different from APM 1.x so you need to make these changes (you will need to tick 3, 4, 17, 18, 19, 20). You will find the fields you need on the iNet3 tab

![http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/mavlinkhil.png](http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/mavlinkhil.png)

  * I have been using the stock PT-60 in Xplane with good results.    I would recommend a cruise airspeed of 15 m/s
  * One quirk of the PT-60 is that it bounces around a lot on the ground and if you are not careful it has prop-strikes followed by simulated engine failure, which is really annoying. The easiest way around this is to not try taxiing around and take off in FBW mode.  Hold the pitch stick for a modest climb and go to full throttle.

Here is the sequence to get things started properly

  1. Configure APM through the CLI so it is ready to go (including a mission if desired).  Use a terminal program of your choice.  Be sure to close it when you are done so the serial port is free
  1. Start Xplane.  After it is initialized and while the plane is sitting on the ground hit the p key (pause)
  1. Start ArduPilotMega Planner - ArdupilotSim MAVLINK, Configure it for correct serial port and baud rate.
  1. Make sure the slide switch on APM is in the flying position.  Click the button in ArduPilotSim to connect.  In the serial window you should see APM's startup messages, and then you should see values appear in the output fields.  Switch your TX mode switch to the manual position and verify that the outputs are moving with your TX sticks.
  1. Make sure your throttle stick is down.
  1. Switch to Xplane.  You are ready to go.  Click the p key to unpause. Hit the b key to unlock the brakes. Switch to FBW mode if desired.  Take-off!