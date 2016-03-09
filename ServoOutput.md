## Servo output ##

**Instructions**: This test is similar to the RC input test, but instead it records what APM is sending to the output. This reflects any modifications you may have made to the RC signal, such as servo reversing or scaling. With transmitter on, move your sticks. The data should reflect the channel that you're moving.

**Typical data:**

![http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/servo_out.png](http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/servo_out.png)

**Troubleshooting:** If the outputs don't all respond to your RC inputs, you may have an early production run board with buggy firmware. You can update your firmware by following the instructions [here](http://code.google.com/p/ardupilot-mega/wiki/Encoder).