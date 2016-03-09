## 遙測指南 ##

硬件安裝指南在[這裡](Wireless.md)。

### 1) 速度選擇 ###

```
//                      *EXPLAINED*  
//                           Telemetry is information that is sent over a wireless link between the UAV and your laptop, this is used when a GCS(Ground Control Station) like HK*GCS or QGCS is 
//                           used and it sends that information through "Telemport" on your APM through a Xbee module(wireless module see link above)
//                           
//                      *INSTRUCTIONS*
//                          Because telemetry is a additional add on you need to tell APM that you are using one, 
//                          if you followed the instructions in the link above exactly then you need to do the following.
//                          The Xbee modules has different speed settings (Baudrates) the default baud rate for telemetry is 57600, if you do not have enough knowledge yet we 
//                          Suggest you use the default baud. simply change the statement "#define SERIAL3_BAUD   57600"to whatever speed you would like if you chose to change it.
//                          
//                      *AVAILABLE SPEED OPTIONS*                                             NOTE: WHEN CHOSING A BUAD SPEED FOR YOUR TELEMETRY YOU NEED TO SET UP YOUR 
//                          #define SERIAL3_BAUD   9600                                              XBEE TO THE SAME SPEED AS WELL AS YOUR GCS(gound control station)
//                          #define SERIAL3_BAUD   19200                                             INSTRUCTIONS CAN BE FOUND IN LINK ABOVE
//                          #define SERIAL3_BAUD   38400
//                          #define SERIAL3_BAUD   57600
//                          #define SERIAL3_BAUD   115200
//            ******************
//            *SELECTED OPPTION*
                #define SERIAL3_BAUD   57600            
//            ******************              
```

### 2) 端口選擇 ###

```
//                         *EXPLAINED*
//                             The telemetry can be set up to exit the APM board through 2 ports "0" and "3"
//                             "0" being your USB and "3" being your TelemPort because of this you need to tell APM through wich port
//                             you want the Telemetry(information) to go.
//                             
//                         *INSTRUCTIONS*
//                             Simple change the following statement from"#define GCS_PORT    0" to "#define GCS_PORT	3"
//                         
//                         *AVAILABLE OPPTIONS*
//                             #  define GCS_PORT	     0      (APM will send information through the mini usb port) 
//                             #  define GCS_PORT	     3      (APM will send information through the Telemport to be sent wirelessly by Xbee module)
//             ******************
//             *SELECTED OPPTION*
               #define GCS_PORT      3 
//             ******************   
```

### 3) 地面站協議選擇 ###

```
//                           *EXPLAINED*
//                                Now that you have your telemetry speed selected and you have chosen the port you want the information to exit you must now select
//                                what GCS Protocol you want to use. The Protocol is the different Information formats used by different GCS software and you need to select the one you want.
//                           
//                           *INSTRUCTIONS*
//                                Look at the list provided below and simply change the statement from 
//                                "#define GCS_PROTOCOL GCS_PROTOCOL_NONE" to "#define GCS_PROTOCOL GCS_PROTOCOL_(your choice)"
//                                
//                           *AVAILABLE OPPTIONS*     
//                                 GCS_PROTOCOL_NONE        No GCS output
//                                 GCS_PROTOCOL_STANDARD    standard APM protocol
//                                 GCS_PROTOCOL_SPECIAL     special test protocol (?)
//                                 GCS_PROTOCOL_LEGACY      legacy ArduPilot protocol
//                                 GCS_PROTOCOL_XPLANE      HIL simulation ground station
//                                 GCS_PROTOCOL_IMU         ArdiPilot IMU output
//                                 GCS_PROTOCOL_JASON       Jason's special secret GCS protocol
//                 ******************
//                  SELECTED OPPTION 
                  #define GCS_PROTOCOL GCS_PROTOCOL_LEGACY
//                 ******************
```