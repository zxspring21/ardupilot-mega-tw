
```
//-------------------------------------
#define GPS_PROTOCOL GPS_PROTOCOL_MTK
//                           *AVAILABLE OPTIONS*
//                             GPS_PROTOCOL_NONE        No GPS attached
//                             GPS_PROTOCOL_IMU         X-Plane interface or ArduPilot IMU.
//                             GPS_PROTOCOL_MTK         MediaTek-based GPS.
//                             GPS_PROTOCOL_MTK16       MediaTek GPS with firmware 1.6
//                             GPS_PROTOCOL_UBLOX       UBLOX GPS
//                             GPS_PROTOCOL_SIRF        SiRF-based GPS in Binary mode.  NOT TESTED
//-------------------------------------
#define AIRSPEED_SENSOR     ENABLED
//                           *AVAILABLE OPTIONS*
//                              #define AIRSPEED_SENSOR     DISABLED
//                              #define AIRSPEED_SENSOR     ENABLED
//-------------------------------------
#define SERIAL3_BAUD   57600            
//                           *AVAILABLE SPEED OPTIONS*   NOTE: When choosing a speed for APM, you need to configure your Xbee modules and GCS for that same speed)
//                              #define SERIAL3_BAUD   9600                                          
//                              #define SERIAL3_BAUD   19200      
//                              #define SERIAL3_BAUD   38400
//                              #define SERIAL3_BAUD   57600
//                              #define SERIAL3_BAUD   115200
//-------------------------------------
#define GCS_PORT      3 
//                         *AVAILABLE OPTIONS*
//                             #  define GCS_PORT	     0      (APM will send information through the mini usb port) 
//                             #  define GCS_PORT	     3      (APM will send information through the Telemport to be sent wirelessly by Xbee module)
//
//--------------------------------------
#define GCS_PROTOCOL GCS_PROTOCOL_LEGACY
//
//                         *AVAILABLE OPTIONS*     
//                                 GCS_PROTOCOL_NONE        No GCS output
//                                 GCS_PROTOCOL_STANDARD    standard APM protocol
//                                 GCS_PROTOCOL_SPECIAL     special test protocol (?)
//                                 GCS_PROTOCOL_LEGACY      legacy ArduPilot protocol
//                                 GCS_PROTOCOL_XPLANE      HIL simulation ground station
//                                 GCS_PROTOCOL_IMU         ArdiPilot IMU output
//                                 GCS_PROTOCOL_JASON       Jason's special secret GCS protocol
```