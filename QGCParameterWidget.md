#summary Calibration and OnBoard Parameters Widget

# Introduction #

Using the QGroundControl Calibration and OnBoard Parameters Widget

The contents of this page are current as of 2/5/2011.


# Details #

The QGroundControl Calibration and OnBoard Parameters Widget can be used to:

  * View and change a variety on on-board APM parameters like PID gains, trim settings, throttle or airspeed settings, etc.

  * Change the frequency that various Data Streams are sent from APM to QGroundControl

  * Run certain calibration wizards

Here is an expanded view of the widget:

![http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/param-widget.jpg](http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/param-widget.jpg)


**The OnBoard Parameters** list will initially be empty.  When the "Refresh" button is clicked APM will send down a current list of its changeable parameters and values.  The list will be in an expandable format.  Just click the + and - to the left of each level to show or hide parameters.

Note that the parameter list in the graphic above is NOT from APM.  APM's parameter list will look different.

Parameters are shown with a name and value.  The names cannot be changed.  To change a value double-click on it.  Once you have changed any values you wish click on the "Transmit" button to send the new values to APM.

Functionality for APM associated with the "Read (ROM)" and "Write (ROM)" buttons is still under development.

The "Load File" and "Save File" buttons will allow you to save or load a parameter list to the ground station hard drive (Untested for APM).


**The Data Stream Rates** section allows you to configure APM to send certain telemetry streams to QGroundControl on a periodic basis. APM can send data streams at rates of approximately 50Hz, 10Hz, or 3.3 Hz.  On startup APM has all streams turned off, and only sends a heartbeat message to QGroundControl.

To turn on a particular stream put a frequency value (in Hertz) in the appropriate field.  Recommended frequency values are 3, 10, and 50.  Be careful about turning on too many high frequency streams as APM performance could be affected.

QGroundControl uses the data received in these streams to drive its Main Window and Widgets.  For example if you have the Main Window set to a map and have the button clicked to keep the map centered on the UAV, then the lat/lng info received in the position data stream is used to know the UAV's position and center the map.

General contents of the Data Streams are:
  * Raw Sensor - the raw gyro and accelerometer data
  * Extended - the current mode, battery voltage
  * Position - the UAV's current lat/lng and altitude
  * Controller - the autopilot's current servo outputs
  * RC Values - the current radio input values
  * Extra 1 - the current gps status
  * Extra 2 - the current waypoint
  * Extra 3 - the current roll, pitch and yaw


**Calibration Wizards** - information coming soon.