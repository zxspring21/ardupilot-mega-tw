## Configuring the APM Sofware ##

In order to set up Ardupilot you must first customize the header file with settings specific to your airframe and RC system.

Each option has a value with a comment that describes the possible options. Edit this file carefully in the Arduino IDE (do **not** use a separate text editor, which may put in extraneous characters and lead to "/277" compile errors) and follow this format or APM will not compile and upload properly.

#define OPTION\_NAME value // comment

Whatever is in the value slot will be copied directly into the code by the compiler. If you have a typo, that typo will be copied into the code and will generate errors wherever that define is used. If this happens, realize the error may not be in the code or file that the compiler says, but in the header file.

The Header file lives in the same folder as your code. You can have multiple header files for different airframes; just comment out the ones you aren't using. You can choose any name for it as long as you use that name in APM For example if your file name is **test\_header.h** the include statement in APM should read:

```
//#include "APM_Config.h" //commented out the default config file
#include "test_header.h"
```

APM's configuration options have been split into two files: APM\_Config.h and APM\_PID\_gains.h. The first is all that most users will need, and they may never touch anything but that file. The second is for more experienced users, and includes gains and other settings to tweak APM for specific airframes (see sidebar at left).

You can edit the values using the [MissionPlanner utility](http://code.google.com/p/ardupilot-mega/downloads/detail?name=ArdupilotMegaPlanner.zip). First, click the button at top right to load the defines.h file from your APM software folder. Then, just click the Edit APM Config button at the lower right on the main screen, to get the following screen. When you're done, click the "Modify" button to save the settings:

![http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/megaconfig.png](http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/megaconfig.png)

Alternatively, you can edit the configuration file directly in the Arduino IDE. Note: if you use another text editor it can introduce hidden characters that can cause the compiler to choke.

Many values will be either a 0 or 1 (checkboxes if you're using the config utility).  For example the parameter AIRSPEED\_SENSOR will be 0 if you are not using an airspeed sensor and 1 if you are.  Some parameters, like REVERSE\_ROLL must be a -1 or 1.  If you put a 0 here your system will not work properly.

Pay attention to units and ranges listed in the comments.  For example many angle values are input as degrees x 100.  For example the parameter HEAD\_MAX which is the maximum bank angle that the autopilot will command is input as degrees x 100.  If you want your autopilot to use a maximum bank angle of 45 degrees you will set this parameter to 4500.

Pay close attention to the notes about the units for airspeeds! They are tricky.
Even if you are not using an airspeed sensor you need to have a good value for CRUISE\_AIRSPEED.  This value must be matched to the value of THROTTLE\_CRUISE in accordance with the notes.  If these values are mismatched your navigation will work poorly.


## Editing the APM configuration file ##


General Tips:

  * Flight modes are described [here](http://code.google.com/p/ardupilot/wiki/FlightModes).
  * Debug modes are described [here](http://code.google.com/p/ardupilot/wiki/Test)

Tips for auto takeoff and landing settings:

  * TAKE\_OFF\_ALT - this should only be as high as you feel comfortable with - meaning clear all obstacles.
  * LAND\_PITCH is turned on only at the last second before reaching the WP
  * AIRSPEED\_SLOW only if you use a sensor, your throttle slow should be calibrated to deliver this airspeed.
  * SLOW\_RADIUS closer than this radius slows the engine
  * THROTTLE\_CUT\_RADIUS closer than this radius kills the engine offset\_altitude - don't edit this. it generates a slope for your glide path. Set your landing wp to 0 altitude.

Tips for airspeed sensor calibration:

  * AIRSPEED\_RATIO is used to adjust the sensitivity of the differential pressure sensor. If your airspeed is consistently reading high or low (make sure you account for head/tail winds before deciding this) then probably your pitot/static setup is not optimal. You can compensate by changing this parameter.


---


```
/* ArduPilot Mega Header file : Aug 20, 2010 */
// Ardupilot 1.0.3 Public Alpha
// Please don't forget to set your Range of Throttle !!!!!!!!!!!!IMPORTANT!!!!!!!!!!!
 
/*
These Flight Modes can be changed either here or directly in events.pde
	
	MANUAL			= Full manual control via the mux - cannot be overridden
	CIRCLE			= Fly in a stabilized 'dumb' circle - for planes with no GPS
	STABILIZE		= Try and maintain level flight
	FLY_BY_WIRE_A	= Autopilot style control via user input, manual throttle
	FLY_BY_WIRE_B	= Autopilot style control via user input, aispeed controlled with throttle
	AUTO			= What you bought the thing for
	
	Auto Mode options:
	WAYPOINT		= Default Mode
	RTL				= Come home - Home is set at first good GPS read from ground startup
	LOITER			= Come home
	TAKEOFF			= full throttle with desired pitch, stabilized roll
	LAND				= You must specify the landing waypoints in this header - read the manual

  If you are using channel 8 for mode switching then POSITION_5 and POSITION_6 should be MANUAL
  The hardware failsafe MUX is set to go manual at 1750 milliseconds
  Set your switch(es) to produce 1165, 1295, 1425, 1555, 1685, and 1815 milliseconds

  If you only want 3 modes set 1=2, 3=4, 5=6 and set your switch to produce 1165, 1425, and 1815 (assuming you want hardware failsafe MUX)
*/

#define POSITION_1 AUTO
#define POSITION_2 AUTO
#define POSITION_3 FLY_BY_WIRE_B
#define POSITION_4 FLY_BY_WIRE_B
#define POSITION_5 MANUAL		// Software Manual - recommended
#define POSITION_6 MANUAL		// Hardware Manual - you can put something else here, but the hardware multiplexer will force manual control

// So why isn't AUTO here by default? Well, please try and run Stabilize first, 
// then FLY_BY_WIRE_A to verify you have good gains set up correctly 
// before you try Auto and wreck your plane. I'll sleep better that way...

#define ENABLE_AIR_START 0		// 0 = Air Start Disabled,  1 = Air Start Enabled
// If airstart is disabled then you will get a ground start (including IMU calibration) every time the AP is powered up.
//    This means that if you get a power glitch or reboot for some reason in the air, you will probably crash, but it prevents
//    a lot of problems on the ground like unintentional motor start-ups, etc.
// If airstart is enabled then you will get an air start at power up and a ground start will be performed if the speed is near zero when we get gps lock

// Debug options - set only one of these options to 1 at a time, set the others to 0
#define DEBUG_SUBSYSTEM 0 		// 0 = no debug
								// 1 = Debug the Radio input
								// 2 = Debug the Servo output
								// 3 = Debug the Sensor input
								// 4 = Debug the GPS input
								// 5 = Debug the GPS input - RAW HEX OUTPUT
								// 6 = Debug the IMU
								// 7 = Debug the Control Switch
								// 8 = Debug the Servo DIP switches
								// 9 = Debug the Relay out
								// 10 = Debug the Magnetometer
								// 11 = Debug the ABS pressure sensor
								// 12 = Debug the stored waypoints
								// 13 = Debug the Throttle
								// 14 = Debug the Radio Min Max
								// 15 = Debug the EEPROM - Hex Dump
								

#define DEBUG_LEVEL SEVERITY_LOW
								// SEVERITY_LOW
								// SEVERITY_MEDIUM
								// SEVERITY_HIGH
								// SEVERITY_CRITICAL

#define GROUND_START_DELAY 0	// milliseconds : if you need time to flip the model over to level before the IMU calibration

/***************************************/
//HARDWARE CONFIGURATION
#define AIRSPEED_SENSOR 1 		// (boolean) Do you have an airspeed sensor attached? 1= yes, 0 = no.
#define ALTITUDE_MIX 0.5		//	GPS vs Pressure Altitude.	0 = GPS altitude, 1 = Press alt, 0.5 = half and half, etc.


// can someone get computed includes working???
//#define GPS_PROTOCOL 	2		// 0 = NMEA
								// 1 = SIRF, 
								// 2 = uBlox
								// 3 = ArduIMU / Xplane
								// 4 = MediaTek, 
								// -1 = no GPS

//0-4 Ground Control Station:
#define GCS_PROTOCOL 	2		// 0 = Ardupilot Mega Standard Binary 
								// 1 = special test, 
								// 2 = Ardupilot Legacy 
								// 3 = Xplane
								// 4 = Ardupilot IMU out
								// 5 = Jason's GCS, 
								// -1 = no GCS (no telemtry output)
								
								
/***************************************/
//  Telemetry -  Uncomment the pair for the port you want to use

#define SendSer Serial.print		//  This pair to use the usb port
#define SendSerln Serial.println

//#define SendSer Serial3.print		//  this pair for the xbee port
//#define SendSerln Serial3.println

/***************************************/
// Altitude estimation:
#define AOA 100					// deg * 100 : the angle your plane flies at level - use the IMU to find this value.
#define ALT_EST_GAIN .01		// the gain of the altitude estimation function, lower number = slower error correction and smoother output


/***************************************/
//Battery:
#define BATTERY_EVENT 0 		// (boolean) 0 = don't read battery, 1 = read battery voltage (only if you have it wired up!)
#define INPUT_VOLTAGE 5.2	 	// (Volts) voltage your power regulator is feeding your ArduPilot to have an accurate pressure and battery level readings. (you need a multimeter to measure and set this of course)
#define VOLT_DIV_RATIO 1.0		//  Voltage divider ratio set with thru-hole resistor (see manual)
#define LOW_VOLTAGE	11.4		// Pack voltage at which to trigger alarm



/***************************************/
// RADIO
//3-1
#define MODE_CHANNEL 7			// 4 to 7 (of 0 to 7)	Which channel will you use for mode selection
#define THROTTLE_OUT 1			// For debugging - 0 = no throttle, 1 = normal throttle
#define THROTTLE_FAILSAFE 0 	// Do you want to react to a throttle failsafe condition? Default is no 0, Yes is 1
#define THROTTLE_FS_VALUE 975	// (microseconds) What value to trigger failsafe 
#define REVERSE_THROTTLE 0		// 0 = Normal mode. 1 = Reverse mode - Try and reverse throttle direction on your radio first, most ESC use low values for low throttle.
#define FAILSAFE_ACTION 2		// 1 = come home in AUTO, LOITER,	2 = dont come home
#define AUTO_TRIM 1				// 0 = no, 1 = set the trim of the radio when switching from Manual
#define SET_RADIO_LIMITS 0		// 0 = no, 1 = set the limits of the Channels with the radio at launch each time; see manual for more
#define CH1_MIN 1162 			// (Microseconds) Range of Ailerons/ (Rudder for 3 channel)
#define CH1_MAX 1907 			// (Microseconds)
#define CH2_MIN 1011 			// (Microseconds) Range of Elevator
#define CH2_MAX 1763 			// (Microseconds)
#define CH3_MIN 1110 			// (Microseconds) Range of Throttle !!!!!!!!!!!!IMPORTANT!!!!!!!!!!!
#define CH3_MAX 1939 			// (Microseconds)
#define CH4_MIN 1005 			// (Microseconds) Range of Rudder
#define CH4_MAX 2100 			// (Microseconds)
#define CH5_MIN 1000 			// (Microseconds) 
#define CH5_MAX 2000 			// (Microseconds)
#define CH6_MIN 1000 			// (Microseconds) 
#define CH6_MAX 2000 			// (Microseconds)
#define CH7_MIN 1000 			// (Microseconds) 
#define CH7_MAX 2000 			// (Microseconds)
#define CH8_MIN 1000 			// (Microseconds) 
#define CH8_MAX 2000 			// (Microseconds)


/***************************************/
// Airplane speed control
#define AIRSPEED_CRUISE 10		// meters/s : Speed to try and maintain - this is no longer pressure value!!!
#define AIRSPEED_RATIO 2.0064	// If your airspeed is under-reporting, increase this value (make small changes)

// NOTE - The range for throttle values is 0 to 100
// NOTE - For proper tuning the THROTTLE_CRUISE value should be the correct value to produce AIRSPEED_CRUISE in straight and level flight with your airframe
#define THROTTLE_MIN 0			// (0-100) raise it if your plane falls to quickly when decending.
#define THROTTLE_CRUISE 45    	// (0-100) Default throttle value - Used for central value.
#define THROTTLE_MAX 75    	    // (0-100) example: 70 = 56%throttle (lower this if your plane is overpowered)

// For use in Fly By Wire B mode in meters per second
#define AIRSPEED_FBW_MIN 6		// meters/s : Minimum airspeed for Fly By Wire mode B, throttle stick at bottom
#define AIRSPEED_FBW_MAX 30		// meters/s : Maximum airspeed for Fly By Wire mode B, throttle stick at top



/***************************************/
//NAVIGATION: PARAMETERS
//Note: Some Gains are now variables
//4-1
#define HEAD_MAX 4500			// deg * 100 : The maximum commanded bank angle (left and right) 	degrees*100
#define PITCH_MAX 1500			// deg * 100 : The maximum commanded pitch up angle 	degrees*100
#define PITCH_MIN -2500			// deg * 100 : The maximum commanded pitch down angle 	degrees*100
#define LOITER_RADIUS 40 		// meters : radius in meters of a Loiter
#define WP_RADIUS 30			// meters 
#define RTL_ALT 100				// (meters) altitude to hold over home position


// Serial ports
#define SERIAL0_BAUD 38400		// this is the main USB out 38400 57600 115200
#define SERIAL1_BAUD 115200
#define SERIAL2_BAUD 115200
#define SERIAL3_BAUD 115200
									
/****************************************************/
/*Logging Stuff	- These should be 1 (on) or 0 (off)*/
/****************************************************/	
#define LOG_ATTITUDE 1	// Logs basic attitude info
#define LOG_GPS 1		// Logs GPS info
#define LOG_PM 1		// Logs IMU performance monitoring info
#define LOG_CTUN 0		// Logs control loop tuning info
#define LOG_NTUN 0		// Logs navigation loop tuning info
#define LOG_MODE 1		// Logs mode changes
#define LOG_RAW 0		// Logs raw accel/gyro data
```