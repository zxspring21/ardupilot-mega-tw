## ArduPilot Mega 二進制通信協議 ##


**通用消息規則**
  1. 消息可以從 UAV 發送到地面站或從地面站發送到 UAV
  1. UAV以消息 0x00 確認地面站發送給 UAV 的消息
  1. 地面站不確認 UAV 發送的消息，除非是 0x05 狀態字消息，並且嚴重性代碼為200或以上


**二進制消息組成部分**
下文順序說明消息的組成部分:
  1. 報頭。報頭為 "4D", 或者 0x34 0x44。(2 字節)
  1. 載荷長度。 (1 字節)
  1. 消息ID。消息ID區分該協議下消息的不同類型。(1 字節)
  1. 消息版本。該字節為今後可能的重大修改預留。(1 字節）
  1. 消息載荷。載荷長度在上述第 2 項中定義。(1-32 字節)
  1. 校驗碼。校驗碼為 2 字節，用Fletcher-8算法計算載荷長度、消息ID、消息版本和載荷的校驗和。該算法與 uBlox 使用的相同。

載荷長度應該與該類型消息預計的長度一致。

例子:  0x3444, 0x03, 0x00, 0x01, 0x1A2B3C （譯註：這個例子沒有給出校驗碼）

**定義的消息**

| **消息ID** |  **請求方式/速率** | **名稱 (典型速率)** | **載荷長度 (字節數)** | **載荷細節** |
|:---------|:-------------|:--------------|:---------------|:---------|
| **0x0x messages are general use messages**|              | | | |
|0x00      |              |接收消息確認 (在上行消息或狀態字消息後)|3               |MsgReceivedID(byte), ChecksumReceived(2 bytes)|
|0x01      |輪詢或1Hz        |系統狀態 (心跳) (1hz)|7               |FlightMode(byte),Timestamp(uint16) (seconds),batt(uint16) (volts\*100), CommandIndex(uint16)|
|0x02      |Constant/10Hz |姿態數據 (10hz)    |6               |roll(int16) (degrees\*100), pitch(int16) (degrees x 100), yaw(uint16) (degrees x 100)|
|0x03      |              |位置數據 (GPS) (1-4hz)|18              |Lat(int32) (decimal degrees x 10^7), Lon(int32), Alt\_MSL(int32) (meters x 100), ground\_speed(uint16) (M/S x 100), ground\_course(uint16) (degrees x 100), Time of Week (uint32) (milliseconds)|
|0x04      |              |氣壓數據 (10Hz)    |4               |PressureAlt (int32) (meters x 100)(mixed value if pressure/gps mixing in use), Airspeed (int16)(TBD)|
|0x05      |On event      |StatusText (on event occurrence)|variable up to 51|Severity (uint8) (0=info, 255=critical), array(50) (Status text message, with null termination character)|
|0x06      |              |性能報告 (20 sec interval)|16              |report interval(uint32) milliseconds, main loop cycles(uint16), max main loop cycle time(uint8) (milliseconds), gyro saturation count(byte), adc contraint count(byte), renorm sqrt count(byte), renorm blowup count(byte), gps fix count(byte), IMU health(uint16) (0 to 1 x1000), GCS message sent count(uint16)|
|0x07      |              |Request Startup Message|2               |system type (byte), system identifier (byte) |
|0x08      |              |Startup Message|5               |system type (byte), system identifier (byte), firmware version (3 bytes) |
| **0x2x messages are command and mode messages** |
|0x20      |              |Request command list item|                |          |
|0x21      |              |Command upload |17              |Action (byte) (0=insert in list, 1=execute immediately), Item number (uint16), List length (uint16), Command ID (byte), Command P1 (byte), Command P2 (int32), Command P3 (int32), Command P4 (int32). See APM Mission Commands for a list of commands|
|0x22      |              |Command List Item (polled or when next WP command becomes active )|16              |Item number (uint16), List length (uint16), Command ID (byte), Command P1 (byte), Command P2 (int32), Command P3 (int32), Command P4 (int32)|
| **0x3x messages are value and variable messages** |
|0x30      |              |Request Value  |2               |Requested value ID (byte), Broadcast (byte) (0=send once, 1=broadcast)   One value ID may be broadcast at a time.  Requesting a 「send once」 of a value being broadcast discontinues broadcast.|
|0x31      |              |Set Value      |5               |Value ID (byte), Value (4 bytes). See appendix 1 for list of values and scaling/format|
|0x32      |              |Requested Value (polled or broadcast at 10Hz)|5               |Requested Value ID (byte), Requested Value (4 bytes). See appendix 1 for list of values and scaling/format|
| **0x4x messages are PID messages** |
|0x40      |              | Request PID   |1               |Requested PID set (byte)|
|0x41      |              |Set PID        |15              |PID Set (byte), P I D gains (each int32) (gain value x 1000000), Integrator max(int16). See appendix 2 for list of PID sets|
|0x42      |              |Requested PID Gains (polled)|15              |PID Set (byte), PID gains (each int32) (gain value x 1000000), Integrator max(int16). See appendix 2 for list of PID sets|
| **0x5x messages are radio messages** |
|0x50      |              |Radio trims (startup)|16              |ch1\_trim(uint16)(pulse width) - ch8\_trim(uint16)(pulse width);|
|0x51      |              |Radio mins (startup)|16              |ch1\_min(uint16)(pulse width) - ch8\_min(uint16)(pulse width);|
|0x52      |              |Radio maxes (startup)|16              |ch1\_max(uint16)(pulse width) - ch8\_max(uint16)(pulse width);|
|0x53      |              |Current radio outputs|16              |ch1(uint16)(pulse width) - ch8(uint16)(pulse width);|
|0x6x      |              |               |                |messages are raw sensor data messages|
| **0x7x messages are for simulation I/O** |
|0x70      |              |Current normalized servo outputs.|16              | ch1(int16)(-100 to 100 x 100)-ch8(int16)(-100 to 100 x 100) |
|0x8x      |              |               |                |messages are for messages for reading ATmega pins|
|0x9x      |              |               |                |messages are for DataFlash messages|
|0xax      |              |               |                |messages are for EEPROM messages|
| **0xbx messages are for navigation augmentation** |
|0xb0      |              |Position Correction|8               |error Lat(int16) (decimal degrees x 10^7), error Lon(int16), error Alt\_MSL(int16) (meters x 100), error ground\_speed(int16) (M/S x 100)|
|0xb1      |              |Attitude Correction|6               |error roll(int16) (degrees\*100), error pitch(int16) (degrees x 100), error yaw(int16) (degrees x 100)|
|0xb2      |              |Set Position   |16              |Lat(int32) (decimal degrees x 10^7), Lon(int32), Alt\_MSL(int32) (meters x 100), ground\_speed(uint16) (M/S x 100)|
|0xb3      |              |Set Attitude   |6               |roll(int16) (degrees\*100), pitch(int16) (degrees x 100), yaw(uint16) (degrees x 100)|


### 附錄 1 ###

**可查詢/設置的值**

| **值** | **設置** | **類型**|
|:------|:-------|:------|
|0x00   |Roll Mode|Integer|
|0x01   |Pitch Mode|Integer|
|0x02   |Throttle Mode|Integer|
|0x03   |Yaw Mode|Integer|
|0x04   |Elevon 1 trim|Integer|
|0x05   |Elevon 2 trim|Integer|
|       | | |
|0x10   |Integrator(0)|x 1000 |
|0x11   |Integrator(1)|x 1000 |
|0x12   |Integrator(2)|x 1000 |
|0x13   |Integrator(3)|x 1000 |
|0x14   |Integrator(4)|x 1000 |
|0x15   |Integrator(5)|x 1000 |
|0x16   |Integrator(6)|x 1000 |
|0x17   |Integrator(7)|x 1000 |
|       | | |
|0x1a   |Kff(0)  |x 1000 |
|0x1b   |Kff(1)  |x 1000 |
|0x1c   |Kff(2)  |x 1000 |
|       | | |
|0x20   |target\_bearing|degrees x 100|
|0x21   |nav\_bearing|degrees x 100|
|0x22   |bearing\_error|degrees x 100|
|0x23   |crosstrack bearing|degrees x 100|
|0x24   |crosstrack\_error|meters |
|0x25   |altitude\_error|meters x 100|
|0x26   |wp\_radius|meters |
|0x27   |loiter\_radius|meters |
|0x28   |wp\_mode|int    |
|0x29   |loop\_commands|int    |
|0x2a   |nav\_gain\_scaler|x 1000 |

待續


### 附錄 2 - PID Sets ###

|CASE\_SERVO\_ROLL|0|
|:----------------|:|
|CASE\_SERVO\_PITCH|1|
|CASE\_SERVO\_RUDDER|2|
|CASE\_NAV\_ROLL  |3|
|CASE\_NAV\_PITCH\_ASP|4|
|CASE\_NAV\_PITCH\_ALT|5|
|CASE\_TE\_THROTTLE|6|
|CASE\_ALT\_THROTTLE|7|