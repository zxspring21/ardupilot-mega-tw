# Table of Contents #


# Vehicles #


## ArduPlane Parameters ##


### Telemetry Baud Rate (ArduPlane:SERIAL3\_BAUD) ###

_The baud rate used on the telemetry port_
  * Values
| **Value** | **Meaning** |
|:----------|:------------|
| 1         | 1200        |
| 2         | 2400        |
| 4         | 4800        |
| 9         | 9600        |
| 19        | 19200       |
| 38        | 38400       |
| 57        | 57600       |
| 111       | 111100      |
| 115       | 115200      |


### Telemetry startup delay  (ArduPlane:TELEM\_DELAY) ###

_The amount of time (in seconds) to delay radio telemetry to prevent an Xbee bricking on power up_
  * Range: 0 10
  * Increment: 1
  * Units: seconds


### Pitch Compensation (ArduPlane:KFF\_PTCHCOMP) ###

_Adds pitch input to compensate for the loss of lift due to roll control. 0 `=` 0 %, 1 `=` 100%_
  * Range: 0 1
  * Increment: 0.01


### Rudder Mix (ArduPlane:KFF\_RDDRMIX) ###

_The amount of rudder mix to apply during aileron movement 0 `=` 0 %, 1 `=` 100%_
  * Range: 0 1
  * Increment: 0.01


### Pitch to Throttle Mix (ArduPlane:KFF\_PTCH2THR) ###

_Pitch to throttle feed-forward gain._
  * Range: 0 5
  * Increment: 0.01


### Throttle to Pitch Mix (ArduPlane:KFF\_THR2PTCH) ###

_Throttle to pitch feed-forward gain._
  * Range: 0 5
  * Increment: 0.01


### Manual Level (ArduPlane:MANUAL\_LEVEL) ###

_Setting this to Disabled(0) will enable autolevel on every boot. Setting it to Enabled(1) will do a calibration only when you tell it to_
  * Values
| **Value** | **Meaning** |
|:----------|:------------|
| 0         | Disabled    |
| 1         | Enabled     |


### Stick Mixing (ArduPlane:STICK\_MIXING) ###

_When enabled, this adds user stick input to the control surfaces in auto modes, allowing the user to have some degree of flight control without changing modes_
  * Values
| **Value** | **Meaning** |
|:----------|:------------|
| 0         | Disabled    |
| 1         | Enabled     |


### Rudder steering on takeoff and landing (ArduPlane:RUDDER\_STEER) ###

_When enabled, only rudder will be used for steering during takeoff and landing, with the ailerons used to hold the plane level_
  * Values
| **Value** | **Meaning** |
|:----------|:------------|
| 0         | Disabled    |
| 1         | Enabled     |


### Landing Pitch (ArduPlane:land\_pitch\_cd) ###

_Used in autoland for planes without airspeed sensors in hundredths of a degree_
  * Units: centi-Degrees


### Landing flare altitude (ArduPlane:land\_flare\_alt) ###

_Altitude in autoland at which to lock heading and flare to the LAND`_`PITCH`_`CD pitch_
  * Increment: 0.1
  * Units: meters


### Landing flare time (ArduPlane:land\_flare\_sec) ###

_Time before landing point at which to lock heading and flare to the LAND`_`PITCH`_`CD pitch_
  * Increment: 0.1
  * Units: seconds


### Crosstrack Gain (ArduPlane:XTRK\_GAIN\_SC) ###

_The scale between distance off the line and angle to meet the line (in Degrees `*` 100)_
  * Range: 0 2000
  * Increment: 1


### Crosstrack Entry Angle (ArduPlane:XTRK\_ANGLE\_CD) ###

_Maximum angle used to correct for track following._
  * Range: 0 9000
  * Increment: 1
  * Units: centi-Degrees


### Crosstrack Wind correction (ArduPlane:XTRK\_USE\_WIND) ###

_If enabled, use wind estimation for navigation crosstrack when using a compass for yaw_
  * Values
| **Value** | **Meaning** |
|:----------|:------------|
| 0         | Disabled    |
| 1         | Enabled     |


### Crosstrack mininum distance (ArduPlane:XTRK\_MIN\_DIST) ###

_Minimum distance in meters between waypoints to do crosstrack correction._
  * Range: 0 32767
  * Increment: 1
  * Units: Meters


### Gps to Baro Mix (ArduPlane:ALT\_MIX) ###

_The percent of mixing between gps altitude and baro altitude. 0 `=` 100% gps, 1 `=` 100% baro_
  * Range: 0 1
  * Increment: 0.1
  * Units: Percent


### Altitude control algorithm (ArduPlane:ALT\_CTRL\_ALG) ###

_This sets what algorithm will be used for altitude control. The default is to select the algorithm based on whether airspeed is enabled. If you set it to 1, then the airspeed based algorithm won't be used for altitude control, but airspeed can be used for other flight control functions_
  * Values
| **Value** | **Meaning** |
|:----------|:------------|
| 0         | Default Method |
| 1         | non-airspeed |


### Altitude offset (ArduPlane:ALT\_OFFSET) ###

_This is added to the target altitude in automatic flight. It can be used to add a global altitude offset to a mission, or to adjust for barometric pressure changes_
  * Range: -32767 32767
  * Increment: 1
  * Units: Meters


### Waypoint Radius (ArduPlane:WP\_RADIUS) ###

_Defines the distance from a waypoint, that when crossed indicates the wp has been hit._
  * Range: 1 127
  * Increment: 1
  * Units: Meters


### Waypoint Loiter Radius (ArduPlane:WP\_LOITER\_RAD) ###

_Defines the distance from the waypoint center, the plane will maintain during a loiter_
  * Range: 1 127
  * Increment: 1
  * Units: Meters


### Action on geofence breach (ArduPlane:FENCE\_ACTION) ###

_What to do on fence breach_
  * Values
| **Value** | **Meaning** |
|:----------|:------------|
| 0         | None        |
| 1         | GuidedMode  |
| 2         | ReportOnly  |


### Fence Total (ArduPlane:FENCE\_TOTAL) ###

_Number of geofence points currently loaded_


### Fence Channel (ArduPlane:FENCE\_CHANNEL) ###

_RC Channel to use to enable geofence. PWM input above 1750 enables the geofence_


### Fence Minimum Altitude (ArduPlane:FENCE\_MINALT) ###

_Minimum altitude allowed before geofence triggers_
  * Range: 0 32767
  * Increment: 1
  * Units: meters


### Fence Maximum Altitude (ArduPlane:FENCE\_MAXALT) ###

_Maximum altitude allowed before geofence triggers_
  * Range: 0 32767
  * Increment: 1
  * Units: meters


### Fly By Wire Minimum Airspeed (ArduPlane:ARSPD\_FBW\_MIN) ###

_Airspeed corresponding to minimum throttle in Fly By Wire B mode._
  * Range: 5 50
  * Increment: 1
  * Units: m`/`s


### Fly By Wire Maximum Airspeed (ArduPlane:ARSPD\_FBW\_MAX) ###

_Airspeed corresponding to maximum throttle in Fly By Wire B mode._
  * Range: 5 50
  * Increment: 1
  * Units: m`/`s


### Fly By Wire elevator reverse (ArduPlane:FBWB\_ELEV\_REV) ###

_Reverse sense of elevator in FBWB. When set to 0 up elevator (pulling back on the stick) means to lower altitude. When set to 1, up elevator means to raise altitude._
  * Values
| **Value** | **Meaning** |
|:----------|:------------|
| 0         | Disabled    |
| 1         | Enabled     |


### Minimum Throttle (ArduPlane:THR\_MIN) ###

_The minimum throttle setting to which the autopilot will apply._
  * Range: 0 100
  * Increment: 1
  * Units: Percent


### Maximum Throttle (ArduPlane:THR\_MAX) ###

_The maximum throttle setting to which the autopilot will apply._
  * Range: 0 100
  * Increment: 1
  * Units: Percent


### Throttlw slew rate (ArduPlane:THR\_SLEWRATE) ###

_maximum percentage change in throttle per second_
  * Range: 0 100
  * Increment: 1
  * Units: Percent


### Throttle suppress manual passthru (ArduPlane:THR\_SUPP\_MAN) ###

_When throttle is supressed in auto mode it is normally forced to zero. If you enable this option, then while suppressed it will be manual throttle. This is useful on petrol engines to hold the idle throttle manually while waiting for takeoff_
  * Values
| **Value** | **Meaning** |
|:----------|:------------|
| 0         | Disabled    |
| 1         | Enabled     |


### Throttle Failsafe Enable (ArduPlane:THR\_FAILSAFE) ###

_The throttle failsafe allows you to configure a software failsafe activated by a setting on the throttle input channel_
  * Values
| **Value** | **Meaning** |
|:----------|:------------|
| 0         | Disabled    |
| 1         | Enabled     |


### Throttle Failsafe Value (ArduPlane:THR\_FS\_VALUE) ###

_The PWM level on channel 3 below which throttle sailsafe triggers_


### Throttle cruise percentage (ArduPlane:TRIM\_THROTTLE) ###

_The target percentage of throttle to apply for normal flight_
  * Range: 0 100
  * Increment: 1
  * Units: Percent


### Throttle nudge enable (ArduPlane:THROTTLE\_NUDGE) ###

_When enabled, this uses the throttle input in auto-throttle modes to 'nudge' the throttle to higher or lower values_
  * Values
| **Value** | **Meaning** |
|:----------|:------------|
| 0         | Disabled    |
| 1         | Enabled     |


### Short failsafe action (ArduPlane:FS\_SHORT\_ACTN) ###

_The action to take on a short (1 second) failsafe event_
  * Values
| **Value** | **Meaning** |
|:----------|:------------|
| 0         | None        |
| 1         | ReturnToLaunch |


### Long failsafe action (ArduPlane:FS\_LONG\_ACTN) ###

_The action to take on a long (20 second) failsafe event_
  * Values
| **Value** | **Meaning** |
|:----------|:------------|
| 0         | None        |
| 1         | ReturnToLaunch |


### GCS failsafe enable (ArduPlane:FS\_GCS\_ENABL) ###

_Enable ground control station telemetry failsafe. Failsafe will trigger after 20 seconds of no MAVLink heartbeat messages_
  * Values
| **Value** | **Meaning** |
|:----------|:------------|
| 0         | Disabled    |
| 1         | Enabled     |


### Flightmode channel (ArduPlane:FLTMODE\_CH) ###

_RC Channel to use for flight mode control_


### FlightMode1 (ArduPlane:FLTMODE1) ###

_Flight mode for switch position 1 (910 to 1230 and above 2049)_
  * Values
| **Value** | **Meaning** |
|:----------|:------------|
| 0         | Manual      |
| 1         | CIRCLE      |
| 2         | STABILIZE   |
| 5         | FBWA        |
| 6         | FBWB        |
| 10        | Auto        |
| 11        | RTL         |
| 12        | Loiter      |
| 15        | Guided      |


### FlightMode2 (ArduPlane:FLTMODE2) ###

_Flight mode for switch position 2 (1231 to 1360)_
  * Values
| **Value** | **Meaning** |
|:----------|:------------|
| 0         | Manual      |
| 1         | CIRCLE      |
| 2         | STABILIZE   |
| 5         | FBWA        |
| 6         | FBWB        |
| 10        | Auto        |
| 11        | RTL         |
| 12        | Loiter      |
| 15        | Guided      |


### FlightMode3 (ArduPlane:FLTMODE3) ###

_Flight mode for switch position 3 (1361 to 1490)_
  * Values
| **Value** | **Meaning** |
|:----------|:------------|
| 0         | Manual      |
| 1         | CIRCLE      |
| 2         | STABILIZE   |
| 5         | FBWA        |
| 6         | FBWB        |
| 10        | Auto        |
| 11        | RTL         |
| 12        | Loiter      |
| 15        | Guided      |


### FlightMode4 (ArduPlane:FLTMODE4) ###

_Flight mode for switch position 4 (1491 to 1620)_
  * Values
| **Value** | **Meaning** |
|:----------|:------------|
| 0         | Manual      |
| 1         | CIRCLE      |
| 2         | STABILIZE   |
| 5         | FBWA        |
| 6         | FBWB        |
| 10        | Auto        |
| 11        | RTL         |
| 12        | Loiter      |
| 15        | Guided      |


### FlightMode5 (ArduPlane:FLTMODE5) ###

_Flight mode for switch position 5 (1621 to 1749)_
  * Values
| **Value** | **Meaning** |
|:----------|:------------|
| 0         | Manual      |
| 1         | CIRCLE      |
| 2         | STABILIZE   |
| 5         | FBWA        |
| 6         | FBWB        |
| 10        | Auto        |
| 11        | RTL         |
| 12        | Loiter      |
| 15        | Guided      |


### FlightMode6 (ArduPlane:FLTMODE6) ###

_Flight mode for switch position 6 (1750 to 2049)_
  * Values
| **Value** | **Meaning** |
|:----------|:------------|
| 0         | Manual      |
| 1         | CIRCLE      |
| 2         | STABILIZE   |
| 5         | FBWA        |
| 6         | FBWB        |
| 10        | Auto        |
| 11        | RTL         |
| 12        | Loiter      |
| 15        | Guided      |


### Maximum Bank Angle (ArduPlane:LIM\_ROLL\_CD) ###

_The maximum commanded bank angle in either direction_
  * Range: 0 9000
  * Increment: 1
  * Units: centi-Degrees


### Maximum Pitch Angle (ArduPlane:LIM\_PITCH\_MAX) ###

_The maximum commanded pitch up angle_
  * Range: 0 9000
  * Increment: 1
  * Units: centi-Degrees


### Minimum Pitch Angle (ArduPlane:LIM\_PITCH\_MIN) ###

_The minimum commanded pitch down angle_
  * Range: -9000 0
  * Increment: 1
  * Units: centi-Degrees


### Auto trim (ArduPlane:AUTO\_TRIM) ###

_Set RC trim PWM levels to current levels when switching away from manual mode_
  * Values
| **Value** | **Meaning** |
|:----------|:------------|
| 0         | Disabled    |
| 1         | Enabled     |


### Elevon mixing (ArduPlane:MIX\_MODE) ###

_Enable elevon mixing_
  * Values
| **Value** | **Meaning** |
|:----------|:------------|
| 0         | Disabled    |
| 1         | Enabled     |


### Elevon reverse (ArduPlane:ELEVON\_REVERSE) ###

_Reverse elevon mixing_
  * Values
| **Value** | **Meaning** |
|:----------|:------------|
| 0         | Disabled    |
| 1         | Enabled     |


### Elevon reverse (ArduPlane:ELEVON\_CH1\_REV) ###

_Reverse elevon channel 1_
  * Values: -1:Disabled,1:Enabled


### Elevon reverse (ArduPlane:ELEVON\_CH2\_REV) ###

_Reverse elevon channel 2_
  * Values: -1:Disabled,1:Enabled


### Num Resets (ArduPlane:SYS\_NUM\_RESETS) ###

_Number of APM board resets_


### Log bitmask (ArduPlane:LOG\_BITMASK) ###

_bitmap of log fields to enable_


### Reset Switch Channel (ArduPlane:RST\_SWITCH\_CH) ###

_RC channel to use to reset to last flight mode	after geofence takeover._


### Reset Mission Channel (ArduPlane:RST\_MISSION\_CH) ###

_RC channel to use to reset the mission to the first waypoint. When this channel goes above 1750 the mission is reset. Set RST`_`MISSION`_`CH to 0 to disable._


### Target airspeed (ArduPlane:TRIM\_ARSPD\_CM) ###

_Airspeed in cm`/`s to aim for when airspeed is enabled in auto mode_
  * Units: cm`/`s


### speed used for speed scaling calculations (ArduPlane:SCALING\_SPEED) ###

_Airspeed in m`/`s to use when calculating surface speed scaling. Note that changing this value will affect all PID values_
  * Units: m`/`s


### Minimum ground speed (ArduPlane:MIN\_GNDSPD\_CM) ###

_Minimum ground speed in cm`/`s when under airspeed control_
  * Units: cm`/`s


### Pitch angle offset (ArduPlane:TRIM\_PITCH\_CD) ###

_offset to add to pitch - used for trimming tail draggers_
  * Units: centi-Degrees


### RTL altitude (ArduPlane:ALT\_HOLD\_RTL) ###

_Return to launch target altitude_
  * Units: centimeters


### Enable Compass (ArduPlane:MAG\_ENABLE) ###

_Setting this to Enabled(1) will enable the compass. Setting this to Disabled(0) will disable the compass_
  * Values
| **Value** | **Meaning** |
|:----------|:------------|
| 0         | Disabled    |
| 1         | Enabled     |


### Battery Voltage sensing pin (ArduPlane:BATT\_VOLT\_PIN) ###

_Setting this to 0 `~` 13 will enable battery current sensing on pins A0 `~` A13._
  * Values
| **Value** | **Meaning** |
|:----------|:------------|
| 99        | Disabled    |
|  0        | A0          |
|  1        | A1          |
|  13       | A13         |


### Battery Current sensing pin (ArduPlane:BATT\_CURR\_PIN) ###

_Setting this to 0 `~` 13 will enable battery current sensing on pins A0 `~` A13._
  * Values
| **Value** | **Meaning** |
|:----------|:------------|
| 99        | Disabled    |
|  1        | A1          |
|  2        | A2          |
|  12       | A12         |


## ArduCopter Parameters ##


### Telemetry Baud Rate (ArduCopter:SERIAL3\_BAUD) ###

_The baud rate used on the telemetry port_
  * Values
| **Value** | **Meaning** |
|:----------|:------------|
| 1         | 1200        |
| 2         | 2400        |
| 4         | 4800        |
| 9         | 9600        |
| 19        | 19200       |
| 38        | 38400       |
| 57        | 57600       |
| 111       | 111100      |
| 115       | 115200      |


### Telemetry startup delay  (ArduCopter:TELEM\_DELAY) ###

_The amount of time (in seconds) to delay radio telemetry to prevent an Xbee bricking on power up_
  * Range: 0 10
  * Increment: 1
  * Units: seconds


### RTL Altitude (ArduCopter:ALT\_HOLD\_RTL) ###

_This is the altitude the model will move to before Returning to Launch.  Set to zero to return at current altitude._
  * Range: 0 4000
  * Increment: 1
  * Units: centimeters


### Enable Sonar (ArduCopter:SONAR\_ENABLE) ###

_Setting this to Enabled(1) will enable the sonar. Setting this to Disabled(0) will disable the sonar_
  * Values
| **Value** | **Meaning** |
|:----------|:------------|
| 0         | Disabled    |
| 1         | Enabled     |


### Voltage Divider (ArduCopter:VOLT\_DIVIDER) ###

_TODO_


### Battery Capacity (ArduCopter:BATT\_CAPACITY) ###

_Battery capacity in milliamp-hours (mAh)_
  * Units: mAh


### Enable Compass (ArduCopter:MAG\_ENABLE) ###

_Setting this to Enabled(1) will enable the compass. Setting this to Disabled(0) will disable the compass_
  * Values
| **Value** | **Meaning** |
|:----------|:------------|
| 0         | Disabled    |
| 1         | Enabled     |


### Enable Optical Flow (ArduCopter:FLOW\_ENABLE) ###

_Setting this to Enabled(1) will enable optical flow. Setting this to Disabled(0) will disable optical flow_
  * Values
| **Value** | **Meaning** |
|:----------|:------------|
| 0         | Disabled    |
| 1         | Enabled     |


### Low Voltage (ArduCopter:LOW\_VOLT) ###

_Set this to the voltage you want to represent low voltage_
  * Range: 0 20
  * Increment: .1


### Enable Super Simple Mode (ArduCopter:SUPER\_SIMPLE) ###

_Setting this to Enabled(1) will enable Super Simple Mode. Setting this to Disabled(0) will disable Super Simple Mode_
  * Values
| **Value** | **Meaning** |
|:----------|:------------|
| 0         | Disabled    |
| 1         | Enabled     |


### RTL Approach Altitude (ArduCopter:APPROACH\_ALT) ###

_This is the altitude the vehicle will move to as the final stage of Returning to Launch.  Set to zero to land._
  * Range: 0 1000
  * Increment: 1
  * Units: centimeters


### Auto Tilt Compensation (ArduCopter:TILT) ###

_This is a feed-forward compensation which helps the aircraft achieve target waypoint speed._
  * Range: 0 100
  * Increment: 1


### Battery Voltage sensing pin (ArduCopter:BATT\_VOLT\_PIN) ###

_Setting this to 0 `~` 13 will enable battery current sensing on pins A0 `~` A13._
  * Values
| **Value** | **Meaning** |
|:----------|:------------|
| 99        | Disabled    |
|  0        | A0          |
|  1        | A1          |
|  13       | A13         |


### Battery Current sensing pin (ArduCopter:BATT\_CURR\_PIN) ###

_Setting this to 0 `~` 13 will enable battery current sensing on pins A0 `~` A13._
  * Values
| **Value** | **Meaning** |
|:----------|:------------|
| 99        | Disabled    |
|  1        | A1          |
|  2        | A2          |
|  12       | A12         |


### Waypoint Radius (ArduCopter:WP\_RADIUS) ###

_Defines the distance from a waypoint, that when crossed indicates the wp has been hit._
  * Range: 1 127
  * Increment: 1
  * Units: Meters


### Waypoint Loiter Radius (ArduCopter:WP\_LOITER\_RAD) ###

_Defines the distance from the waypoint center, the vehicle will maintain during a loiter_
  * Range: 1 127
  * Increment: 1
  * Units: Meters


### Waypoint Max Speed Target (ArduCopter:WP\_SPEED\_MAX) ###

_Defines the speed which the aircraft will attempt to maintain during a WP mission._
  * Increment: 100
  * Units: Centimeters`/`Second


### Cross-Track Gain (ArduCopter:XTRK\_GAIN\_SC) ###

_This controls the rate that the Auto Controller will attempt to return original track_
  * Units: Dimensionless


### Minimum Throttle (ArduCopter:THR\_MIN) ###

_The minimum throttle which the autopilot will apply._
  * Range: 0 100
  * Increment: 1
  * Units: Percent


### Maximum Throttle (ArduCopter:THR\_MAX) ###

_The maximum throttle which the autopilot will apply._
  * Range: 0 100
  * Increment: 1
  * Units: Percent


### Throttle Failsafe Enable (ArduCopter:THR\_FAILSAFE) ###

_The throttle failsafe allows you to configure a software failsafe activated by a setting on the throttle input channel_
  * Values
| **Value** | **Meaning** |
|:----------|:------------|
| 0         | Disabled    |
| 1         | Enabled     |


### Throttle Failsafe Value (ArduCopter:THR\_FS\_VALUE) ###

_The PWM level on channel 3 below which throttle sailsafe triggers_


### Log bitmask (ArduCopter:LOG\_BITMASK) ###

_bitmap of log fields to enable_


### Auto Slew Rate (ArduCopter:AUTO\_SLEW) ###

_This restricts the rate of change of the attitude allowed by the Auto Controller_
  * Range: 1 45
  * Increment: 1
  * Units: Degrees`/`Second


### ESC Update Speed (ArduCopter:RC\_SPEED) ###

_This is the speed in Hertz that your ESCs will receive updates_
  * Values: 125,400,490
  * Units: Hertz (Hz)


### Stabilize D Schedule (ArduCopter:STAB\_D\_S) ###

_This value is a percentage of scheduling applied to the Stabilize D term._
  * Range: 0 1
  * Increment: .01


## APMrover2 Parameters ##


### Enable Sonar (APMrover2:SONAR\_ENABLE) ###

_Setting this to Enabled(1) will enable the sonar. Setting this to Disabled(0) will disable the sonar_
  * Values
| **Value** | **Meaning** |
|:----------|:------------|
| 0         | Disabled    |
| 1         | Enabled     |


# Libraries #



## CAM_Parameters ##_


### Camera shutter (trigger) type (CAM\_TRIGG\_TYPE) ###

_how to trigger the camera to take a picture_
  * Values
| **Value** | **Meaning** |
|:----------|:------------|
| 0         | Servo       |
| 1         | relay       |
| 2         | throttle\_off\_time |
| 3         | throttle\_off\_waypoint |
| 4         | transistor  |


## RC1_Parameters ##_


### RC min PWM (RC1\_MIN) ###

_RC minimum PWM pulse width. Typically 1000 is lower limit, 1500 is neutral and 2000 is upper limit._
  * Range: 800 2200
  * Increment: 1
  * Units: ms


### RC trim PWM (RC1\_TRIM) ###

_RC trim (neutral) PWM pulse width. Typically 1000 is lower limit, 1500 is neutral and 2000 is upper limit._
  * Range: 800 2200
  * Increment: 1
  * Units: ms


### RC max PWM (RC1\_MAX) ###

_RC maximum PWM pulse width. Typically 1000 is lower limit, 1500 is neutral and 2000 is upper limit._
  * Range: 800 2200
  * Increment: 1
  * Units: ms


### RC reverse (RC1\_REV) ###

_Reverse servo operation. Ignored on APM1 unless dip-switches are disabled._
  * Values: -1:Reversed,1:Normal


### RC dead-zone (RC1\_DZ) ###

_dead zone around trim._


## RC2_Parameters ##_


### RC min PWM (RC2\_MIN) ###

_RC minimum PWM pulse width. Typically 1000 is lower limit, 1500 is neutral and 2000 is upper limit._
  * Range: 800 2200
  * Increment: 1
  * Units: ms


### RC trim PWM (RC2\_TRIM) ###

_RC trim (neutral) PWM pulse width. Typically 1000 is lower limit, 1500 is neutral and 2000 is upper limit._
  * Range: 800 2200
  * Increment: 1
  * Units: ms


### RC max PWM (RC2\_MAX) ###

_RC maximum PWM pulse width. Typically 1000 is lower limit, 1500 is neutral and 2000 is upper limit._
  * Range: 800 2200
  * Increment: 1
  * Units: ms


### RC reverse (RC2\_REV) ###

_Reverse servo operation. Ignored on APM1 unless dip-switches are disabled._
  * Values: -1:Reversed,1:Normal


### RC dead-zone (RC2\_DZ) ###

_dead zone around trim._


## RC3_Parameters ##_


### RC min PWM (RC3\_MIN) ###

_RC minimum PWM pulse width. Typically 1000 is lower limit, 1500 is neutral and 2000 is upper limit._
  * Range: 800 2200
  * Increment: 1
  * Units: ms


### RC trim PWM (RC3\_TRIM) ###

_RC trim (neutral) PWM pulse width. Typically 1000 is lower limit, 1500 is neutral and 2000 is upper limit._
  * Range: 800 2200
  * Increment: 1
  * Units: ms


### RC max PWM (RC3\_MAX) ###

_RC maximum PWM pulse width. Typically 1000 is lower limit, 1500 is neutral and 2000 is upper limit._
  * Range: 800 2200
  * Increment: 1
  * Units: ms


### RC reverse (RC3\_REV) ###

_Reverse servo operation. Ignored on APM1 unless dip-switches are disabled._
  * Values: -1:Reversed,1:Normal


### RC dead-zone (RC3\_DZ) ###

_dead zone around trim._


## RC4_Parameters ##_


### RC min PWM (RC4\_MIN) ###

_RC minimum PWM pulse width. Typically 1000 is lower limit, 1500 is neutral and 2000 is upper limit._
  * Range: 800 2200
  * Increment: 1
  * Units: ms


### RC trim PWM (RC4\_TRIM) ###

_RC trim (neutral) PWM pulse width. Typically 1000 is lower limit, 1500 is neutral and 2000 is upper limit._
  * Range: 800 2200
  * Increment: 1
  * Units: ms


### RC max PWM (RC4\_MAX) ###

_RC maximum PWM pulse width. Typically 1000 is lower limit, 1500 is neutral and 2000 is upper limit._
  * Range: 800 2200
  * Increment: 1
  * Units: ms


### RC reverse (RC4\_REV) ###

_Reverse servo operation. Ignored on APM1 unless dip-switches are disabled._
  * Values: -1:Reversed,1:Normal


### RC dead-zone (RC4\_DZ) ###

_dead zone around trim._


## RC5_Parameters ##_


### Servo out function (RC5\_FUNCTION) ###

_Setting this to Disabled(0) will disable this output, any other value will enable the corresponding function_
  * Values
| **Value** | **Meaning** |
|:----------|:------------|
| 0         | Disabled    |
| 1         | Manual      |
| 2         | Flap        |
| 3         | Flap\_auto  |
| 4         | Aileron     |
| 5         | flaperon    |
| 6         | mount\_pan  |
| 7         | mount\_tilt |
| 8         | mount\_roll |
| 9         | mount\_open |
| 10        | camera\_trigger |
| 11        | release     |


### RC min PWM (RC5\_MIN) ###

_RC minimum PWM pulse width. Typically 1000 is lower limit, 1500 is neutral and 2000 is upper limit._
  * Range: 800 2200
  * Increment: 1
  * Units: ms


### RC trim PWM (RC5\_TRIM) ###

_RC trim (neutral) PWM pulse width. Typically 1000 is lower limit, 1500 is neutral and 2000 is upper limit._
  * Range: 800 2200
  * Increment: 1
  * Units: ms


### RC max PWM (RC5\_MAX) ###

_RC maximum PWM pulse width. Typically 1000 is lower limit, 1500 is neutral and 2000 is upper limit._
  * Range: 800 2200
  * Increment: 1
  * Units: ms


### RC reverse (RC5\_REV) ###

_Reverse servo operation. Ignored on APM1 unless dip-switches are disabled._
  * Values: -1:Reversed,1:Normal


### RC dead-zone (RC5\_DZ) ###

_dead zone around trim._


## RC6_Parameters ##_


### Servo out function (RC6\_FUNCTION) ###

_Setting this to Disabled(0) will disable this output, any other value will enable the corresponding function_
  * Values
| **Value** | **Meaning** |
|:----------|:------------|
| 0         | Disabled    |
| 1         | Manual      |
| 2         | Flap        |
| 3         | Flap\_auto  |
| 4         | Aileron     |
| 5         | flaperon    |
| 6         | mount\_pan  |
| 7         | mount\_tilt |
| 8         | mount\_roll |
| 9         | mount\_open |
| 10        | camera\_trigger |
| 11        | release     |


### RC min PWM (RC6\_MIN) ###

_RC minimum PWM pulse width. Typically 1000 is lower limit, 1500 is neutral and 2000 is upper limit._
  * Range: 800 2200
  * Increment: 1
  * Units: ms


### RC trim PWM (RC6\_TRIM) ###

_RC trim (neutral) PWM pulse width. Typically 1000 is lower limit, 1500 is neutral and 2000 is upper limit._
  * Range: 800 2200
  * Increment: 1
  * Units: ms


### RC max PWM (RC6\_MAX) ###

_RC maximum PWM pulse width. Typically 1000 is lower limit, 1500 is neutral and 2000 is upper limit._
  * Range: 800 2200
  * Increment: 1
  * Units: ms


### RC reverse (RC6\_REV) ###

_Reverse servo operation. Ignored on APM1 unless dip-switches are disabled._
  * Values: -1:Reversed,1:Normal


### RC dead-zone (RC6\_DZ) ###

_dead zone around trim._


## RC7_Parameters ##_


### Servo out function (RC7\_FUNCTION) ###

_Setting this to Disabled(0) will disable this output, any other value will enable the corresponding function_
  * Values
| **Value** | **Meaning** |
|:----------|:------------|
| 0         | Disabled    |
| 1         | Manual      |
| 2         | Flap        |
| 3         | Flap\_auto  |
| 4         | Aileron     |
| 5         | flaperon    |
| 6         | mount\_pan  |
| 7         | mount\_tilt |
| 8         | mount\_roll |
| 9         | mount\_open |
| 10        | camera\_trigger |
| 11        | release     |


### RC min PWM (RC7\_MIN) ###

_RC minimum PWM pulse width. Typically 1000 is lower limit, 1500 is neutral and 2000 is upper limit._
  * Range: 800 2200
  * Increment: 1
  * Units: ms


### RC trim PWM (RC7\_TRIM) ###

_RC trim (neutral) PWM pulse width. Typically 1000 is lower limit, 1500 is neutral and 2000 is upper limit._
  * Range: 800 2200
  * Increment: 1
  * Units: ms


### RC max PWM (RC7\_MAX) ###

_RC maximum PWM pulse width. Typically 1000 is lower limit, 1500 is neutral and 2000 is upper limit._
  * Range: 800 2200
  * Increment: 1
  * Units: ms


### RC reverse (RC7\_REV) ###

_Reverse servo operation. Ignored on APM1 unless dip-switches are disabled._
  * Values: -1:Reversed,1:Normal


### RC dead-zone (RC7\_DZ) ###

_dead zone around trim._


## RC8_Parameters ##_


### Servo out function (RC8\_FUNCTION) ###

_Setting this to Disabled(0) will disable this output, any other value will enable the corresponding function_
  * Values
| **Value** | **Meaning** |
|:----------|:------------|
| 0         | Disabled    |
| 1         | Manual      |
| 2         | Flap        |
| 3         | Flap\_auto  |
| 4         | Aileron     |
| 5         | flaperon    |
| 6         | mount\_pan  |
| 7         | mount\_tilt |
| 8         | mount\_roll |
| 9         | mount\_open |
| 10        | camera\_trigger |
| 11        | release     |


### RC min PWM (RC8\_MIN) ###

_RC minimum PWM pulse width. Typically 1000 is lower limit, 1500 is neutral and 2000 is upper limit._
  * Range: 800 2200
  * Increment: 1
  * Units: ms


### RC trim PWM (RC8\_TRIM) ###

_RC trim (neutral) PWM pulse width. Typically 1000 is lower limit, 1500 is neutral and 2000 is upper limit._
  * Range: 800 2200
  * Increment: 1
  * Units: ms


### RC max PWM (RC8\_MAX) ###

_RC maximum PWM pulse width. Typically 1000 is lower limit, 1500 is neutral and 2000 is upper limit._
  * Range: 800 2200
  * Increment: 1
  * Units: ms


### RC reverse (RC8\_REV) ###

_Reverse servo operation. Ignored on APM1 unless dip-switches are disabled._
  * Values: -1:Reversed,1:Normal


### RC dead-zone (RC8\_DZ) ###

_dead zone around trim._


## RC9_Parameters ##_


### Servo out function (RC9\_FUNCTION) ###

_Setting this to Disabled(0) will disable this output, any other value will enable the corresponding function_
  * Values
| **Value** | **Meaning** |
|:----------|:------------|
| 0         | Disabled    |
| 1         | Manual      |
| 2         | Flap        |
| 3         | Flap\_auto  |
| 4         | Aileron     |
| 5         | flaperon    |
| 6         | mount\_pan  |
| 7         | mount\_tilt |
| 8         | mount\_roll |
| 9         | mount\_open |
| 10        | camera\_trigger |
| 11        | release     |


### RC min PWM (RC9\_MIN) ###

_RC minimum PWM pulse width. Typically 1000 is lower limit, 1500 is neutral and 2000 is upper limit._
  * Range: 800 2200
  * Increment: 1
  * Units: ms


### RC trim PWM (RC9\_TRIM) ###

_RC trim (neutral) PWM pulse width. Typically 1000 is lower limit, 1500 is neutral and 2000 is upper limit._
  * Range: 800 2200
  * Increment: 1
  * Units: ms


### RC max PWM (RC9\_MAX) ###

_RC maximum PWM pulse width. Typically 1000 is lower limit, 1500 is neutral and 2000 is upper limit._
  * Range: 800 2200
  * Increment: 1
  * Units: ms


### RC reverse (RC9\_REV) ###

_Reverse servo operation. Ignored on APM1 unless dip-switches are disabled._
  * Values: -1:Reversed,1:Normal


### RC dead-zone (RC9\_DZ) ###

_dead zone around trim._


## RC10_Parameters ##_


### Servo out function (RC10\_FUNCTION) ###

_Setting this to Disabled(0) will disable this output, any other value will enable the corresponding function_
  * Values
| **Value** | **Meaning** |
|:----------|:------------|
| 0         | Disabled    |
| 1         | Manual      |
| 2         | Flap        |
| 3         | Flap\_auto  |
| 4         | Aileron     |
| 5         | flaperon    |
| 6         | mount\_pan  |
| 7         | mount\_tilt |
| 8         | mount\_roll |
| 9         | mount\_open |
| 10        | camera\_trigger |
| 11        | release     |


### RC min PWM (RC10\_MIN) ###

_RC minimum PWM pulse width. Typically 1000 is lower limit, 1500 is neutral and 2000 is upper limit._
  * Range: 800 2200
  * Increment: 1
  * Units: ms


### RC trim PWM (RC10\_TRIM) ###

_RC trim (neutral) PWM pulse width. Typically 1000 is lower limit, 1500 is neutral and 2000 is upper limit._
  * Range: 800 2200
  * Increment: 1
  * Units: ms


### RC max PWM (RC10\_MAX) ###

_RC maximum PWM pulse width. Typically 1000 is lower limit, 1500 is neutral and 2000 is upper limit._
  * Range: 800 2200
  * Increment: 1
  * Units: ms


### RC reverse (RC10\_REV) ###

_Reverse servo operation. Ignored on APM1 unless dip-switches are disabled._
  * Values: -1:Reversed,1:Normal


### RC dead-zone (RC10\_DZ) ###

_dead zone around trim._


## RC11_Parameters ##_


### Servo out function (RC11\_FUNCTION) ###

_Setting this to Disabled(0) will disable this output, any other value will enable the corresponding function_
  * Values
| **Value** | **Meaning** |
|:----------|:------------|
| 0         | Disabled    |
| 1         | Manual      |
| 2         | Flap        |
| 3         | Flap\_auto  |
| 4         | Aileron     |
| 5         | flaperon    |
| 6         | mount\_pan  |
| 7         | mount\_tilt |
| 8         | mount\_roll |
| 9         | mount\_open |
| 10        | camera\_trigger |
| 11        | release     |


### RC min PWM (RC11\_MIN) ###

_RC minimum PWM pulse width. Typically 1000 is lower limit, 1500 is neutral and 2000 is upper limit._
  * Range: 800 2200
  * Increment: 1
  * Units: ms


### RC trim PWM (RC11\_TRIM) ###

_RC trim (neutral) PWM pulse width. Typically 1000 is lower limit, 1500 is neutral and 2000 is upper limit._
  * Range: 800 2200
  * Increment: 1
  * Units: ms


### RC max PWM (RC11\_MAX) ###

_RC maximum PWM pulse width. Typically 1000 is lower limit, 1500 is neutral and 2000 is upper limit._
  * Range: 800 2200
  * Increment: 1
  * Units: ms


### RC reverse (RC11\_REV) ###

_Reverse servo operation. Ignored on APM1 unless dip-switches are disabled._
  * Values: -1:Reversed,1:Normal


### RC dead-zone (RC11\_DZ) ###

_dead zone around trim._


## AHRS_Parameters ##_


### AHRS GPS gain (AHRS\_GPS\_GAIN) ###

_This controls how how much to use the GPS to correct the attitude_
  * Range: 0.0 1.0
  * Increment: .01


### AHRS use GPS (AHRS\_GPS\_USE) ###

_This controls how how much to use the GPS to correct the attitude. This is for testing the dead-reckoning code_


### Yaw P (AHRS\_YAW\_P) ###

_This controls the weight the compass has on the overall heading_
  * Range: 0 .4
  * Increment: .01


### AHRS RP\_P (AHRS\_RP\_P) ###

_This controls how fast the accelerometers correct the attitude_
  * Range: 0 .4
  * Increment: .01


### AHRS Use Barometer (AHRS\_BARO\_USE) ###

_This controls the use of the barometer for vertical acceleration compensation in AHRS_
  * Values
| **Value** | **Meaning** |
|:----------|:------------|
| 0         | Disabled    |
| 1         | Enabled     |


## ARSPD_Parameters ##_


### Airspeed enable (ARSPD\_ENABLE) ###

_enable airspeed sensor_
  * Values
| **Value** | **Meaning** |
|:----------|:------------|
| 0         | Disable     |
| 1         | Enable      |


### Airspeed use (ARSPD\_USE) ###

_use airspeed for flight control_
  * Values
| **Value** | **Meaning** |
|:----------|:------------|
| 1         | Use         |
| 0         | Don't Use   |


### Airspeed offset (ARSPD\_OFFSET) ###

_Airspeed calibration offset_
  * Increment: 0.1


### Airspeed ratio (ARSPD\_RATIO) ###

_Airspeed calibration ratio_
  * Increment: 0.1


## MNT_Parameters ##_


### Mount operation mode (MNT\_MODE) ###

_Camera or antenna mount operation mode_
  * Values
| **Value** | **Meaning** |
|:----------|:------------|
| 0         | retract     |
| 1         | neutral     |
| 2         | MavLink\_targeting |
| 3         | RC\_targeting |
| 4         | GPS\_point  |


### Mount retract angles (MNT\_RETRACT) ###

_Mount angles when in retract operation mode_
  * Range: -18000 17999
  * Increment: 1
  * Units: centi-Degrees


### Mount neutral angles (MNT\_NEUTRAL) ###

_Mount angles when in neutral operation mode_
  * Range: -18000 17999
  * Increment: 1
  * Units: centi-Degrees


### Mount control angles (MNT\_CONTROL) ###

_Mount angles when in MavLink or RC control operation mode_
  * Range: -18000 17999
  * Increment: 1
  * Units: centi-Degrees


### Stabilize mount tilt (MNT\_STAB\_TILT) ###

_enable tilt (pitch) stabilisation relative to Earth_
  * Values
| **Value** | **Meaning** |
|:----------|:------------|
| 0         | Disabled    |
| 1         | Enabled     |


### Stabilize mount pan (MNT\_STAB\_PAN) ###

_enable pan (yaw) stabilisation relative to Earth_
  * Values
| **Value** | **Meaning** |
|:----------|:------------|
| 0         | Disabled    |
| 1         | Enabled     |


### roll RC input channel (MNT\_RC\_IN\_ROLL) ###

_0 for none, any other for the RC channel to be used to control roll movements_
  * Values
| **Value** | **Meaning** |
|:----------|:------------|
| 0         | Disabled    |
| 5         | RC5         |
| 6         | RC6         |
| 7         | RC7         |
| 8         | RC8         |


### Minimum roll angle (MNT\_ANGMIN\_ROL) ###

_Minimum physical roll angular position of mount._
  * Range: -18000 17999
  * Increment: 1
  * Units: centi-Degrees


### Maximum roll angle (MNT\_ANGMAX\_ROL) ###

_Maximum physical roll angular position of the mount_
  * Range: -18000 17999
  * Increment: 1
  * Units: centi-Degrees


### tilt (pitch) RC input channel (MNT\_RC\_IN\_TILT) ###

_0 for none, any other for the RC channel to be used to control tilt (pitch) movements_
  * Values
| **Value** | **Meaning** |
|:----------|:------------|
| 0         | Disabled    |
| 5         | RC5         |
| 6         | RC6         |
| 7         | RC7         |
| 8         | RC8         |


### Minimum tilt angle (MNT\_ANGMIN\_TIL) ###

_Minimum physical tilt (pitch) angular position of mount._
  * Range: -18000 17999
  * Increment: 1
  * Units: centi-Degrees


### Maximum tilt angle (MNT\_ANGMAX\_TIL) ###

_Maximum physical tilt (pitch) angular position of the mount_
  * Range: -18000 17999
  * Increment: 1
  * Units: centi-Degrees


### pan (yaw) RC input channel (MNT\_RC\_IN\_PAN) ###

_0 for none, any other for the RC channel to be used to control pan (yaw) movements_
  * Values
| **Value** | **Meaning** |
|:----------|:------------|
| 0         | Disabled    |
| 5         | RC5         |
| 6         | RC6         |
| 7         | RC7         |
| 8         | RC8         |


### Minimum pan angle (MNT\_ANGMIN\_PAN) ###

_Minimum physical pan (yaw) angular position of mount._
  * Range: -18000 17999
  * Increment: 1
  * Units: centi-Degrees


### Maximum pan angle (MNT\_ANGMAX\_PAN) ###

_Maximum physical pan (yaw) angular position of the mount_
  * Range: -18000 17999
  * Increment: 1
  * Units: centi-Degrees


### mount joystick speed (MNT\_JSTICK\_SPD) ###

_0 for position control, small for low speeds, 10 for max speed_
  * Range: 0 10
  * Increment: 1


## MNT2_Parameters ##_


### Mount operation mode (MNT2\_MODE) ###

_Camera or antenna mount operation mode_
  * Values
| **Value** | **Meaning** |
|:----------|:------------|
| 0         | retract     |
| 1         | neutral     |
| 2         | MavLink\_targeting |
| 3         | RC\_targeting |
| 4         | GPS\_point  |


### Mount retract angles (MNT2\_RETRACT) ###

_Mount angles when in retract operation mode_
  * Range: -18000 17999
  * Increment: 1
  * Units: centi-Degrees


### Mount neutral angles (MNT2\_NEUTRAL) ###

_Mount angles when in neutral operation mode_
  * Range: -18000 17999
  * Increment: 1
  * Units: centi-Degrees


### Mount control angles (MNT2\_CONTROL) ###

_Mount angles when in MavLink or RC control operation mode_
  * Range: -18000 17999
  * Increment: 1
  * Units: centi-Degrees


### Stabilize mount tilt (MNT2\_STAB\_TILT) ###

_enable tilt (pitch) stabilisation relative to Earth_
  * Values
| **Value** | **Meaning** |
|:----------|:------------|
| 0         | Disabled    |
| 1         | Enabled     |


### Stabilize mount pan (MNT2\_STAB\_PAN) ###

_enable pan (yaw) stabilisation relative to Earth_
  * Values
| **Value** | **Meaning** |
|:----------|:------------|
| 0         | Disabled    |
| 1         | Enabled     |


### roll RC input channel (MNT2\_RC\_IN\_ROLL) ###

_0 for none, any other for the RC channel to be used to control roll movements_
  * Values
| **Value** | **Meaning** |
|:----------|:------------|
| 0         | Disabled    |
| 5         | RC5         |
| 6         | RC6         |
| 7         | RC7         |
| 8         | RC8         |


### Minimum roll angle (MNT2\_ANGMIN\_ROL) ###

_Minimum physical roll angular position of mount._
  * Range: -18000 17999
  * Increment: 1
  * Units: centi-Degrees


### Maximum roll angle (MNT2\_ANGMAX\_ROL) ###

_Maximum physical roll angular position of the mount_
  * Range: -18000 17999
  * Increment: 1
  * Units: centi-Degrees


### tilt (pitch) RC input channel (MNT2\_RC\_IN\_TILT) ###

_0 for none, any other for the RC channel to be used to control tilt (pitch) movements_
  * Values
| **Value** | **Meaning** |
|:----------|:------------|
| 0         | Disabled    |
| 5         | RC5         |
| 6         | RC6         |
| 7         | RC7         |
| 8         | RC8         |


### Minimum tilt angle (MNT2\_ANGMIN\_TIL) ###

_Minimum physical tilt (pitch) angular position of mount._
  * Range: -18000 17999
  * Increment: 1
  * Units: centi-Degrees


### Maximum tilt angle (MNT2\_ANGMAX\_TIL) ###

_Maximum physical tilt (pitch) angular position of the mount_
  * Range: -18000 17999
  * Increment: 1
  * Units: centi-Degrees


### pan (yaw) RC input channel (MNT2\_RC\_IN\_PAN) ###

_0 for none, any other for the RC channel to be used to control pan (yaw) movements_
  * Values
| **Value** | **Meaning** |
|:----------|:------------|
| 0         | Disabled    |
| 5         | RC5         |
| 6         | RC6         |
| 7         | RC7         |
| 8         | RC8         |


### Minimum pan angle (MNT2\_ANGMIN\_PAN) ###

_Minimum physical pan (yaw) angular position of mount._
  * Range: -18000 17999
  * Increment: 1
  * Units: centi-Degrees


### Maximum pan angle (MNT2\_ANGMAX\_PAN) ###

_Maximum physical pan (yaw) angular position of the mount_
  * Range: -18000 17999
  * Increment: 1
  * Units: centi-Degrees


### mount joystick speed (MNT2\_JSTICK\_SPD) ###

_0 for position control, small for low speeds, 10 for max speed_
  * Range: 0 10
  * Increment: 1


## CAM_Parameters ##_


### Camera shutter (trigger) type (CAM\_TRIGG\_TYPE) ###

_how to trigger the camera to take a picture_
  * Values
| **Value** | **Meaning** |
|:----------|:------------|
| 0         | Servo       |
| 1         | relay       |
| 2         | throttle\_off\_time |
| 3         | throttle\_off\_waypoint |
| 4         | transistor  |


## RC1_Parameters ##_


### RC min PWM (RC1\_MIN) ###

_RC minimum PWM pulse width. Typically 1000 is lower limit, 1500 is neutral and 2000 is upper limit._
  * Range: 800 2200
  * Increment: 1
  * Units: ms


### RC trim PWM (RC1\_TRIM) ###

_RC trim (neutral) PWM pulse width. Typically 1000 is lower limit, 1500 is neutral and 2000 is upper limit._
  * Range: 800 2200
  * Increment: 1
  * Units: ms


### RC max PWM (RC1\_MAX) ###

_RC maximum PWM pulse width. Typically 1000 is lower limit, 1500 is neutral and 2000 is upper limit._
  * Range: 800 2200
  * Increment: 1
  * Units: ms


### RC reverse (RC1\_REV) ###

_Reverse servo operation. Ignored on APM1 unless dip-switches are disabled._
  * Values: -1:Reversed,1:Normal


### RC dead-zone (RC1\_DZ) ###

_dead zone around trim._


## RC2_Parameters ##_


### RC min PWM (RC2\_MIN) ###

_RC minimum PWM pulse width. Typically 1000 is lower limit, 1500 is neutral and 2000 is upper limit._
  * Range: 800 2200
  * Increment: 1
  * Units: ms


### RC trim PWM (RC2\_TRIM) ###

_RC trim (neutral) PWM pulse width. Typically 1000 is lower limit, 1500 is neutral and 2000 is upper limit._
  * Range: 800 2200
  * Increment: 1
  * Units: ms


### RC max PWM (RC2\_MAX) ###

_RC maximum PWM pulse width. Typically 1000 is lower limit, 1500 is neutral and 2000 is upper limit._
  * Range: 800 2200
  * Increment: 1
  * Units: ms


### RC reverse (RC2\_REV) ###

_Reverse servo operation. Ignored on APM1 unless dip-switches are disabled._
  * Values: -1:Reversed,1:Normal


### RC dead-zone (RC2\_DZ) ###

_dead zone around trim._


## RC3_Parameters ##_


### RC min PWM (RC3\_MIN) ###

_RC minimum PWM pulse width. Typically 1000 is lower limit, 1500 is neutral and 2000 is upper limit._
  * Range: 800 2200
  * Increment: 1
  * Units: ms


### RC trim PWM (RC3\_TRIM) ###

_RC trim (neutral) PWM pulse width. Typically 1000 is lower limit, 1500 is neutral and 2000 is upper limit._
  * Range: 800 2200
  * Increment: 1
  * Units: ms


### RC max PWM (RC3\_MAX) ###

_RC maximum PWM pulse width. Typically 1000 is lower limit, 1500 is neutral and 2000 is upper limit._
  * Range: 800 2200
  * Increment: 1
  * Units: ms


### RC reverse (RC3\_REV) ###

_Reverse servo operation. Ignored on APM1 unless dip-switches are disabled._
  * Values: -1:Reversed,1:Normal


### RC dead-zone (RC3\_DZ) ###

_dead zone around trim._


## RC4_Parameters ##_


### RC min PWM (RC4\_MIN) ###

_RC minimum PWM pulse width. Typically 1000 is lower limit, 1500 is neutral and 2000 is upper limit._
  * Range: 800 2200
  * Increment: 1
  * Units: ms


### RC trim PWM (RC4\_TRIM) ###

_RC trim (neutral) PWM pulse width. Typically 1000 is lower limit, 1500 is neutral and 2000 is upper limit._
  * Range: 800 2200
  * Increment: 1
  * Units: ms


### RC max PWM (RC4\_MAX) ###

_RC maximum PWM pulse width. Typically 1000 is lower limit, 1500 is neutral and 2000 is upper limit._
  * Range: 800 2200
  * Increment: 1
  * Units: ms


### RC reverse (RC4\_REV) ###

_Reverse servo operation. Ignored on APM1 unless dip-switches are disabled._
  * Values: -1:Reversed,1:Normal


### RC dead-zone (RC4\_DZ) ###

_dead zone around trim._


## RC5_Parameters ##_


### Servo out function (RC5\_FUNCTION) ###

_Setting this to Disabled(0) will disable this output, any other value will enable the corresponding function_
  * Values
| **Value** | **Meaning** |
|:----------|:------------|
| 0         | Disabled    |
| 1         | Manual      |
| 2         | Flap        |
| 3         | Flap\_auto  |
| 4         | Aileron     |
| 5         | flaperon    |
| 6         | mount\_pan  |
| 7         | mount\_tilt |
| 8         | mount\_roll |
| 9         | mount\_open |
| 10        | camera\_trigger |
| 11        | release     |


## RC6_Parameters ##_


### Servo out function (RC6\_FUNCTION) ###

_Setting this to Disabled(0) will disable this output, any other value will enable the corresponding function_
  * Values
| **Value** | **Meaning** |
|:----------|:------------|
| 0         | Disabled    |
| 1         | Manual      |
| 2         | Flap        |
| 3         | Flap\_auto  |
| 4         | Aileron     |
| 5         | flaperon    |
| 6         | mount\_pan  |
| 7         | mount\_tilt |
| 8         | mount\_roll |
| 9         | mount\_open |
| 10        | camera\_trigger |
| 11        | release     |


## RC7_Parameters ##_


### Servo out function (RC7\_FUNCTION) ###

_Setting this to Disabled(0) will disable this output, any other value will enable the corresponding function_
  * Values
| **Value** | **Meaning** |
|:----------|:------------|
| 0         | Disabled    |
| 1         | Manual      |
| 2         | Flap        |
| 3         | Flap\_auto  |
| 4         | Aileron     |
| 5         | flaperon    |
| 6         | mount\_pan  |
| 7         | mount\_tilt |
| 8         | mount\_roll |
| 9         | mount\_open |
| 10        | camera\_trigger |
| 11        | release     |


## RC8_Parameters ##_


### Servo out function (RC8\_FUNCTION) ###

_Setting this to Disabled(0) will disable this output, any other value will enable the corresponding function_
  * Values
| **Value** | **Meaning** |
|:----------|:------------|
| 0         | Disabled    |
| 1         | Manual      |
| 2         | Flap        |
| 3         | Flap\_auto  |
| 4         | Aileron     |
| 5         | flaperon    |
| 6         | mount\_pan  |
| 7         | mount\_tilt |
| 8         | mount\_roll |
| 9         | mount\_open |
| 10        | camera\_trigger |
| 11        | release     |


## RC10_Parameters ##_


### Servo out function (RC10\_FUNCTION) ###

_Setting this to Disabled(0) will disable this output, any other value will enable the corresponding function_
  * Values
| **Value** | **Meaning** |
|:----------|:------------|
| 0         | Disabled    |
| 1         | Manual      |
| 2         | Flap        |
| 3         | Flap\_auto  |
| 4         | Aileron     |
| 5         | flaperon    |
| 6         | mount\_pan  |
| 7         | mount\_tilt |
| 8         | mount\_roll |
| 9         | mount\_open |
| 10        | camera\_trigger |
| 11        | release     |


## RC11_Parameters ##_


### Servo out function (RC11\_FUNCTION) ###

_Setting this to Disabled(0) will disable this output, any other value will enable the corresponding function_
  * Values
| **Value** | **Meaning** |
|:----------|:------------|
| 0         | Disabled    |
| 1         | Manual      |
| 2         | Flap        |
| 3         | Flap\_auto  |
| 4         | Aileron     |
| 5         | flaperon    |
| 6         | mount\_pan  |
| 7         | mount\_tilt |
| 8         | mount\_roll |
| 9         | mount\_open |
| 10        | camera\_trigger |
| 11        | release     |


## AHRS_Parameters ##_


### AHRS GPS gain (AHRS\_GPS\_GAIN) ###

_This controls how how much to use the GPS to correct the attitude_
  * Range: 0.0 1.0
  * Increment: .01


### AHRS use GPS (AHRS\_GPS\_USE) ###

_This controls how how much to use the GPS to correct the attitude. This is for testing the dead-reckoning code_


### Yaw P (AHRS\_YAW\_P) ###

_This controls the weight the compass has on the overall heading_
  * Range: 0 .4
  * Increment: .01


### AHRS RP\_P (AHRS\_RP\_P) ###

_This controls how fast the accelerometers correct the attitude_
  * Range: 0 .4
  * Increment: .01


### AHRS Use Barometer (AHRS\_BARO\_USE) ###

_This controls the use of the barometer for vertical acceleration compensation in AHRS_
  * Values
| **Value** | **Meaning** |
|:----------|:------------|
| 0         | Disabled    |
| 1         | Enabled     |


## MNT_Parameters ##_


### Mount operation mode (MNT\_MODE) ###

_Camera or antenna mount operation mode_
  * Values
| **Value** | **Meaning** |
|:----------|:------------|
| 0         | retract     |
| 1         | neutral     |
| 2         | MavLink\_targeting |
| 3         | RC\_targeting |
| 4         | GPS\_point  |


### Mount retract angles (MNT\_RETRACT) ###

_Mount angles when in retract operation mode_
  * Range: -18000 17999
  * Increment: 1
  * Units: centi-Degrees


### Mount neutral angles (MNT\_NEUTRAL) ###

_Mount angles when in neutral operation mode_
  * Range: -18000 17999
  * Increment: 1
  * Units: centi-Degrees


### Mount control angles (MNT\_CONTROL) ###

_Mount angles when in MavLink or RC control operation mode_
  * Range: -18000 17999
  * Increment: 1
  * Units: centi-Degrees


### Stabilize mount tilt (MNT\_STAB\_TILT) ###

_enable tilt (pitch) stabilisation relative to Earth_
  * Values
| **Value** | **Meaning** |
|:----------|:------------|
| 0         | Disabled    |
| 1         | Enabled     |


### Stabilize mount pan (MNT\_STAB\_PAN) ###

_enable pan (yaw) stabilisation relative to Earth_
  * Values
| **Value** | **Meaning** |
|:----------|:------------|
| 0         | Disabled    |
| 1         | Enabled     |


### roll RC input channel (MNT\_RC\_IN\_ROLL) ###

_0 for none, any other for the RC channel to be used to control roll movements_
  * Values
| **Value** | **Meaning** |
|:----------|:------------|
| 0         | Disabled    |
| 5         | RC5         |
| 6         | RC6         |
| 7         | RC7         |
| 8         | RC8         |


### Minimum roll angle (MNT\_ANGMIN\_ROL) ###

_Minimum physical roll angular position of mount._
  * Range: -18000 17999
  * Increment: 1
  * Units: centi-Degrees


### Maximum roll angle (MNT\_ANGMAX\_ROL) ###

_Maximum physical roll angular position of the mount_
  * Range: -18000 17999
  * Increment: 1
  * Units: centi-Degrees


### tilt (pitch) RC input channel (MNT\_RC\_IN\_TILT) ###

_0 for none, any other for the RC channel to be used to control tilt (pitch) movements_
  * Values
| **Value** | **Meaning** |
|:----------|:------------|
| 0         | Disabled    |
| 5         | RC5         |
| 6         | RC6         |
| 7         | RC7         |
| 8         | RC8         |


### Minimum tilt angle (MNT\_ANGMIN\_TIL) ###

_Minimum physical tilt (pitch) angular position of mount._
  * Range: -18000 17999
  * Increment: 1
  * Units: centi-Degrees


### Maximum tilt angle (MNT\_ANGMAX\_TIL) ###

_Maximum physical tilt (pitch) angular position of the mount_
  * Range: -18000 17999
  * Increment: 1
  * Units: centi-Degrees


### pan (yaw) RC input channel (MNT\_RC\_IN\_PAN) ###

_0 for none, any other for the RC channel to be used to control pan (yaw) movements_
  * Values
| **Value** | **Meaning** |
|:----------|:------------|
| 0         | Disabled    |
| 5         | RC5         |
| 6         | RC6         |
| 7         | RC7         |
| 8         | RC8         |


### Minimum pan angle (MNT\_ANGMIN\_PAN) ###

_Minimum physical pan (yaw) angular position of mount._
  * Range: -18000 17999
  * Increment: 1
  * Units: centi-Degrees


### Maximum pan angle (MNT\_ANGMAX\_PAN) ###

_Maximum physical pan (yaw) angular position of the mount_
  * Range: -18000 17999
  * Increment: 1
  * Units: centi-Degrees


### mount joystick speed (MNT\_JSTICK\_SPD) ###

_0 for position control, small for low speeds, 10 for max speed_
  * Range: 0 10
  * Increment: 1


## MNT2_Parameters ##_


### Mount operation mode (MNT2\_MODE) ###

_Camera or antenna mount operation mode_
  * Values
| **Value** | **Meaning** |
|:----------|:------------|
| 0         | retract     |
| 1         | neutral     |
| 2         | MavLink\_targeting |
| 3         | RC\_targeting |
| 4         | GPS\_point  |


### Mount retract angles (MNT2\_RETRACT) ###

_Mount angles when in retract operation mode_
  * Range: -18000 17999
  * Increment: 1
  * Units: centi-Degrees


### Mount neutral angles (MNT2\_NEUTRAL) ###

_Mount angles when in neutral operation mode_
  * Range: -18000 17999
  * Increment: 1
  * Units: centi-Degrees


### Mount control angles (MNT2\_CONTROL) ###

_Mount angles when in MavLink or RC control operation mode_
  * Range: -18000 17999
  * Increment: 1
  * Units: centi-Degrees


### Stabilize mount tilt (MNT2\_STAB\_TILT) ###

_enable tilt (pitch) stabilisation relative to Earth_
  * Values
| **Value** | **Meaning** |
|:----------|:------------|
| 0         | Disabled    |
| 1         | Enabled     |


### Stabilize mount pan (MNT2\_STAB\_PAN) ###

_enable pan (yaw) stabilisation relative to Earth_
  * Values
| **Value** | **Meaning** |
|:----------|:------------|
| 0         | Disabled    |
| 1         | Enabled     |


### roll RC input channel (MNT2\_RC\_IN\_ROLL) ###

_0 for none, any other for the RC channel to be used to control roll movements_
  * Values
| **Value** | **Meaning** |
|:----------|:------------|
| 0         | Disabled    |
| 5         | RC5         |
| 6         | RC6         |
| 7         | RC7         |
| 8         | RC8         |


### Minimum roll angle (MNT2\_ANGMIN\_ROL) ###

_Minimum physical roll angular position of mount._
  * Range: -18000 17999
  * Increment: 1
  * Units: centi-Degrees


### Maximum roll angle (MNT2\_ANGMAX\_ROL) ###

_Maximum physical roll angular position of the mount_
  * Range: -18000 17999
  * Increment: 1
  * Units: centi-Degrees


### tilt (pitch) RC input channel (MNT2\_RC\_IN\_TILT) ###

_0 for none, any other for the RC channel to be used to control tilt (pitch) movements_
  * Values
| **Value** | **Meaning** |
|:----------|:------------|
| 0         | Disabled    |
| 5         | RC5         |
| 6         | RC6         |
| 7         | RC7         |
| 8         | RC8         |


### Minimum tilt angle (MNT2\_ANGMIN\_TIL) ###

_Minimum physical tilt (pitch) angular position of mount._
  * Range: -18000 17999
  * Increment: 1
  * Units: centi-Degrees


### Maximum tilt angle (MNT2\_ANGMAX\_TIL) ###

_Maximum physical tilt (pitch) angular position of the mount_
  * Range: -18000 17999
  * Increment: 1
  * Units: centi-Degrees


### pan (yaw) RC input channel (MNT2\_RC\_IN\_PAN) ###

_0 for none, any other for the RC channel to be used to control pan (yaw) movements_
  * Values
| **Value** | **Meaning** |
|:----------|:------------|
| 0         | Disabled    |
| 5         | RC5         |
| 6         | RC6         |
| 7         | RC7         |
| 8         | RC8         |


### Minimum pan angle (MNT2\_ANGMIN\_PAN) ###

_Minimum physical pan (yaw) angular position of mount._
  * Range: -18000 17999
  * Increment: 1
  * Units: centi-Degrees


### Maximum pan angle (MNT2\_ANGMAX\_PAN) ###

_Maximum physical pan (yaw) angular position of the mount_
  * Range: -18000 17999
  * Increment: 1
  * Units: centi-Degrees


### mount joystick speed (MNT2\_JSTICK\_SPD) ###

_0 for position control, small for low speeds, 10 for max speed_
  * Range: 0 10
  * Increment: 1


## LIM_Parameters ##_


### Enable Limits Library (LIM\_ENABLED) ###

_Setting this to Enabled(1) will enable the limits system_
  * Values
| **Value** | **Meaning** |
|:----------|:------------|
| 0         | Disabled    |
| 1         | Enabled     |


### Limits Library Required (LIM\_REQUIRED) ###

_Setting this to 1 will enable the limits pre-arm checklist_
  * Values
| **Value** | **Meaning** |
|:----------|:------------|
| 0         | Disabled    |
| 1         | Enabled     |


### Enable Limits Debug (LIM\_DEBUG) ###

_Setting this to 1 will turn on debugging messages on the console and via MAVLink STATUSTEXT messages_
  * Values
| **Value** | **Meaning** |
|:----------|:------------|
| 0         | Disabled    |
| 1         | Enabled     |


### Limits Safetime (LIM\_SAFETIME) ###

_Automatic return of controls to pilot. Set to 0 to disable (full RTL) or a number of seconds after complete recovery to return the controls to the pilot in STABILIZE_
  * Values
| **Value** | **Meaning** |
|:----------|:------------|
| 0         | Disabled    |
| 1-255     | Seconds before returning control |


### Limits Channel (LIM\_CHANNEL) ###

_Channel for Limits on`/`off control. If channel exceeds LIMITS`_`ENABLE`_`PWM, it turns limits on, and vice-versa._
  * Range: 1-8


### Limits Recovery Mode (LIM\_RECMODE) ###

_Select how Limits should "recover". Set to 0 for RTL-like mode, where the vehicle navigates back to home until it is "safe". Set to 1, for bounce-mode, where the vehicle will hold position when it hits a limit. RTL mode is better for large fenced areas, Bounce mode for smaller spaces. Note: RTL mode will cause the vehicle to yaw 180 degrees  (turn around) to navigate towards home when it hits a limit._
  * Values
| **Value** | **Meaning** |
|:----------|:------------|
| 0         | RTL mode    |
|  1        |  Bounce mode |


### Enable gpslock (LIM\_GPSLCK\_ON) ###

_Setting this to Enabled(1) will enable the gpslock. Setting this to Disabled(0) will disable the gpslock_
  * Values
| **Value** | **Meaning** |
|:----------|:------------|
| 0         | Disabled    |
| 1         | Enabled     |


### Require gpslock (LIM\_GPSLCK\_REQ) ###

_Setting this to Enabled(1) will make being inside the gpslock a required check before arming the vehicle._
  * Values
| **Value** | **Meaning** |
|:----------|:------------|
| 0         | Disabled    |
| 1         | Enabled     |


### Enable Geofence (LIM\_FNC\_ON) ###

_Setting this to Enabled(1) will enable the geofence. Setting this to Disabled(0) will disable the geofence_
  * Values
| **Value** | **Meaning** |
|:----------|:------------|
| 0         | Disabled    |
| 1         | Enabled     |


### Require Geofence (LIM\_FNC\_REQ) ###

_Setting this to Enabled(1) will make being inside the geofence a required check before arming the vehicle._
  * Values
| **Value** | **Meaning** |
|:----------|:------------|
| 0         | Disabled    |
| 1         | Enabled     |


### Require Geofence (LIM\_FNC\_SMPL) ###

_"Simple" geofence (enabled - 1) is based on a radius from the home position, "Complex" (disabled - 0) define a complex fence by lat`/`long positions_
  * Values
| **Value** | **Meaning** |
|:----------|:------------|
| 0         | Disabled    |
| 1         | Enabled     |


### Require Geofence (LIM\_FNC\_RAD) ###

_Radius of fenced area in meters. A value of 20 creates a 20-meter radius circle (40-meter diameter) from the home point._
  * Range: 0 32767
  * Increment: 1
  * Units: Meters


### Enable altitude (LIM\_ALT\_ON) ###

_Setting this to Enabled(1) will enable the altitude. Setting this to Disabled(0) will disable the altitude_
  * Values
| **Value** | **Meaning** |
|:----------|:------------|
| 0         | Disabled    |
| 1         | Enabled     |


### Require altitude (LIM\_ALT\_REQD) ###

_Setting this to Enabled(1) will make being inside the altitude a required check before arming the vehicle._
  * Values
| **Value** | **Meaning** |
|:----------|:------------|
| 0         | Disabled    |
| 1         | Enabled     |


### Minimum Altitude (LIM\_ALT\_MIN) ###

_Minimum Altitude. Zero to disable. Sets a "floor" that your vehicle will try to stay above. IF the vehicle is crossing the threshold at speed, it will take a while to recover, so give yourself enough room. Caution: minimum altitude limits can cause unexpected behaviour, such as inability to land, or sudden takeoff. Read the wiki instructions before setting._
  * Range: 0 250000
  * Increment: 1
  * Units: Meters


### Maximum Altitude (LIM\_ALT\_MAX) ###

_Maximum Altitude. Zero to disable. Sets a "ceiling" that your vehicle will try to stay below. IF the vehicle is crossing the threshold at speed, it will take a while to recover._
  * Range: 0 250000
  * Increment: 1
  * Units: Meters


## H_Parameters ##_


### Servo 1 Position (H\_SV1\_POS) ###

_This is the angular location of swash servo `#`1._
  * Range: -180 180
  * Increment: 1
  * Units: Degrees


### Servo 2 Position (H\_SV2\_POS) ###

_This is the angular location of swash servo `#`2._
  * Range: -180 180
  * Increment: 1
  * Units: Degrees


### Servo 3 Position (H\_SV3\_POS) ###

_This is the angular location of swash servo `#`3._
  * Range: -180 180
  * Increment: 1
  * Units: Degrees


### Maximum Roll Angle (H\_ROL\_MAX) ###

_This is the maximum allowable roll of the swash plate._
  * Range: 0 18000
  * Increment: 1
  * Units: Degrees


### Maximum Pitch Angle (H\_PIT\_MAX) ###

_This is the maximum allowable pitch of the swash plate._
  * Range: 0 18000
  * Increment: 1
  * Units: Degrees


### Collective Pitch Minimum (H\_COL\_MIN) ###

_This controls the lowest possible servo position for the swashplate._
  * Range: 1000 2000
  * Increment: 1
  * Units: PWM


### Collective Pitch Maximum (H\_COL\_MAX) ###

_This controls the highest possible servo position for the swashplate._
  * Range: 1000 2000
  * Increment: 1
  * Units: PWM


### Collective Pitch Mid-Point (H\_COL\_MID) ###

_This is the swash servo position corresponding to zero collective pitch (or zero lift for Assymetrical blades)._
  * Range: 1000 2000
  * Increment: 1
  * Units: PWM


### External Gyro Enabled (H\_GYR\_ENABLE) ###

_Setting this to Enabled(1) will enable an external rudder gyro control which means outputting a gain on channel 7 and using a simpler heading control algorithm. Setting this to Disabled(0) will disable the external gyro gain on channel 7 and revert to a more complex yaw control algorithm._
  * Values
| **Value** | **Meaning** |
|:----------|:------------|
| 0         | Disabled    |
| 1         | Enabled     |


### Swash Plate Type (H\_SWASH\_TYPE) ###

_Setting this to 0 will configure for a 3-servo CCPM. Setting this to 1 will configure for mechanically mixed "H1"._


### External Gyro Gain (H\_GYR\_GAIN) ###

_This is the PWM which is passed to the external gyro when external gyro is enabled._
  * Range: 1000 2000
  * Increment: 1
  * Units: PWM


### Manual Servo Mode (H\_SV\_MAN) ###

_Setting this to Enabled(1) will pass radio inputs directly to servos. Setting this to Disabled(0) will enable Arducopter control of servos.  This is only meant to be used by the Mission Planner using swash plate set-up._
  * Values
| **Value** | **Meaning** |
|:----------|:------------|
| 0         | Disabled    |
| 1         | Enabled     |


### Swashplate Phase Angle Compensation (H\_PHANG) ###

_This corrects for phase angle errors of the helicopter main rotor head.  For example if pitching the swash forward also induces a roll, that effect can be offset with this parameter._
  * Range: -90 90
  * Increment: 1
  * Units: Degrees


### Collective-Yaw Mixing (H\_COLYAW) ###

_This is a feed-forward compensation to automatically add rudder input when collective pitch is increased._
  * Range: 0 5


### External Motor Governor Setpoint (H\_GOV\_SETPOINT) ###

_This is the PWM which is passed to the external motor governor when external governor is enabled._
  * Range: 1000 2000
  * Increment: 10
  * Units: PWM


### Rotor Speed Control Mode (H\_RSC\_MODE) ###

_This sets which ESC control mode is active._
  * Range: 1 3


### RSC Ramp Rate (H\_RSC\_RATE) ###

_This sets the time the RSC takes to ramp up to full speed (Soft Start)._
  * Range: 0 6000
  * Units: Seconds


### Flybar Mode Selector (H\_FLYBAR\_MODE) ###

_This sets which acro mode is active. (0) is Flybarless (1) is Mechanical Flybar_
  * Range: 0 1