Find explanations of some of those messages and numbers in the serial output.

### Introduction ###

There is a wealth of information in the data stream that comes back to the PC. Even if you are seeing snapshots explained via a groundstation device or in a live PC graphic display the 'serial printout' can be very useful for debugging purposes. The following is an explanation of both the short text messages, as well as some of the standard strings of values.

### Example 1 ###

Each line appears with a letter in front. The rest is like you would see in the serial stream - here from APM alpha 1 code.

```
A:Init ArduPilotMega 1.0.1 Alpha
B:min / max from eeprom	 1190		 1932
C:Offsets   -1.00   37.00   24.00   30.50   4.88   19.46
D:##STABILIZE
E:XXX Startup: AIR
F:!!0|0|0|0|0.0000000000|-32700|0|0|45|-200
F:!!-319940058|1159932525|22805|20|0.0000000000|-9895|0|3561451|45|-23005
F:!!-319940063|1159932552|37647|10|0.0000000000|4947|0|3561451|45|27689
G:init home
F:!!-319940067|1159932564|35375|19|0.0000000000|-2335|0|3561451|45|29961
F:!!-319940065|1159932570|35467|17|0.0000000000|-2243|0|3561451|45|29869
```

### Example 1 explained ... ###

```
A:The program has begun. Version number given.

B:?

C:?

D:The control mode. (Set by the radio control channel switch position with interpretation by code)

E: Startup type : Ground versus AIR are the alternates. AIR start? - If you intended a ground start you need to start the APM in MANUAL (Switch position 6) control mode.

F: Information from the processor and sensors. Intended for groundstation really.
In short form: (useful to paste into your logs to match value lengths)
current.lat;current.lng;current.alt;grnd_speed;airspeed;alt_above_home;climb_rate;wp_distance;throttle_cruise;alt_err
int(* 10**7) int(* 10**7)     cm       cm/s      cm/s     cm(m*100)       cm/s       cm          %(target)    cm
These lines come from serial.print(ln) statements in print_position() procedure (which is in GCS-xxx.pde file). This is called EVERY time
 there is a new data packet from the GPS - so its fast - about 3Hz
Longer format...
!! current.latitude;current.longitude;current.altitude;grnd_speed;airspeed(zero if airspeed sensor not installed);current_altitude_now_above_home
(current.alt-home.alt);climb_rate;wp_distance(distance to next wapoint);throttle_cruise(target%);alt_err(target-actual)

G: Home point save successful - the altitude and coordinates of your current location have been captured and stored.
```

### Example 2 ###

```
A:Init ArduPilotMega 1.0.1 Alpha
B:min / max from eeprom	 1190		 1932
C:Offsets   0.05   29.99   25.00   -15.20   41.67   6.21
D:##AUTO
E:XXX Startup: Ground
F:Commands in memory
G:commands total: 4
I:Home: 
J:command #: 0 id: 0 p1: 0 p2: 19700 p3: -319938514 p4: 1159930268
K:Commands:
L:command #: 0 id: 64 p1: 5 p2: 19700 p3: -319938514 p4: 1159930268
M:command #: 1 id: 16 p1: 0 p2: 5000 p3: -31 p4: 115
M:command #: 2 id: 16 p1: 0 p2: 5000 p3: -31 p4: 115
M:command #: 3 id: 16 p1: 0 p2: 5000 p3: -31 p4: 115
N:Demo Servos!
N:Demo Servos!
N:Demo Servos!
O:Offsets   0.93   27.31   25.37   -15.82   38.15   6.67
P:NO airspeed
N:Demo Servos!
N:Demo Servos!
N:Demo Servos!

Q:Waiting for GPS. 
Y:!!0|0|0|0|0.0000000000|-19700|0|0|45|-32636
R:load WP
S:PWP:	-319931761,	1159943725,	166608
T:CUR:	-319931761,	1159943725,	166608
U:NWP:1,	-31,	115,	24700
V:wp_distance 3561464
W:??1|-319931761|1159943725|166608|-31|115|24700|3561464|1547|1509

X:command #: 1 id: 16 p1: 0 p2: 5000 p3: -31 p4: 115
Y:!!-319931761|1159943725|166608|104|0.0000000000|15836|0|3561464|45|-10836
Y:!!-319939156|1159930300|6686|62|0.0000000000|-13014|0|3561464|45|18014
```

### Example 2 explained ###
```
A:The program has begun. Software Version number given. 
B:?  
C:?  
D:The control mode. (Set by the radio control channel switch position with interpretation by code) 
E: Startup type : Ground versus AIR are the alternates. GROUND means a normal startup.
F and G: Commands retrieved from memory - loaded previously into EEPROM i.e. using wapoint_writer.pde or similar.
I and J: Home point inserted as command #0 (?)
K: saying the commands now loaded and active are...
L and M: the commands.
L: is home position as a command. Also the RTL target location.

M: the commands you loaded previously.
Format - same as the waypoint file. Namely,
command # num id   param1 2: alt    3: lat  4: long         
Note: all values in decimal int, so command is converted from hex to decimal e.g. 0x10 = 16 (?)
N:Wiggle one servo a little. Indicates program started OR calibration taking place.
O: (?)
P: NO airspeed sensor (hence we will use approximate info from GPS?)
Q: Waiting for start of GPS message stream (?). 
R: (?)
S: previous waypoint (lat, lng, alt)
T: current waypoint (lat, lng, alt)
U: next waypoint (lat, lng, alt)
V: distance from plane to next waypoint from current position (cm(m*100))
W: new waypoint (?? line prefix)
wp_index,prev_WP.lat,prev_WP.lng,prev_WP.alt,next_WP.lat,next_WP.lng,next_WP.alt,
wp_totalDistance,radio_trim[CH_ROLL],radio_trim[CH_PITCH]
X:command #: 1 id: 16 p1: 0 p2: 5000 p3: -31 p4: 115

Y: print statements coming from print_position()procedure (in GCSxxx.pde file)
In short form: (useful to paste into your logs to match value lengths) 
current.lat;current.lng;current.alt;grnd_speed;airspeed;alt_above_home;climb_rate;wp_distance;throttle_cruise;alt_err 
int(* 10**7) int(* 10**7)     cm       cm/s      cm/s     cm(m*100)       cm/s       cm            %          cm
These lines come from serial.print(ln) statements in print_position() procedure (which is in GCS-xxx.pde file). This is called EVERY time
 there is a new data packet from the GPS - so its fast - about 3Hz 
Longer format... 
!! current.latitude;current.longitude;current.altitude;grnd_speed;airspeed(zero if airspeed sensor not installed);current_altitude_now_above_home
(current.alt-home.alt);climb_rate;wp_distance(distance to next wapoint);throttle_cruise(target%);alt_err(target-actual) 
```

May your debugging be quick and your flying long.