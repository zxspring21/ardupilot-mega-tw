## ArduPilotMega 2.0 命令 ##

APM 2.0 已採用 MAVLink 協議指令集的其中一個子集。

APM 的命令共有 14 字節，安排如下：

|Byte #|地址|數據類型|功能|
|:-----|:-|:---|:-|
|0     |0x00|byte|命令 ID|
|1     |0x01|byte|選項|
|2     |0x02|byte|參數 1|
|3     |0x03|long|參數 2|
|4     |0x04|..  |  |
|5     |0x05|..  |  |
|6     |0x06|..  |  |
|7     |0x07|long|參數 3|
|8     |0x08|..  |  |
|9     |0x09|..  |  |
|10    |0x0A|..  |  |
|11    |0x0B|long|參數 4|
|12    |0x0C|..  |  |
|13    |0x0D|..  |  |
|14    |0x0E|..  |  |



---


**導航命令 -- 這些命令都有經緯度部分**

導航命令具有最高優先級。 對比導航命令 ID 更大的命令來說，當下條導航命令準備執行時，未執行的命令都將丟棄。據此規劃/排列命令！

例如，如果你要發出 CMD\_MAV\_CONDITION 的命令格式如下當航點到達時還未執行完 ||0x10 命令，就不會再去執行 CMD\_MAV\_CONDITION 和 CMD\_MAV\_DO 它們將會被跳過，然後再載入下一個 NAV 命令。



---

|命令ID 十六進制/十進制|名稱|參數 1|高度|維度|經度|備註|
|:------------|:-|:---|:-|:-|:-|:-|
|0x10 / 16    |MAV\_CMD\_NAV\_WAYPOINT|-   |altitude|lat|lon|  |
|0x11 / 17    |MAV\_CMD\_NAV\_LOITER\_UNLIM |(indefinitely)|altitude|lat|lon|  |
|0x12 / 18    |MAV\_CMD\_NAV\_LOITER\_TURNS|turns|altitude|lat|lon|  |
|0x13 / 19    |MAV\_CMD\_NAV\_LOITER\_TIME|time (seconds\*10)|altitude|lat|lon|  |
|0x14 / 20    |MAV\_CMD\_NAV\_RETURN\_TO\_LAUNCH|-   |altitude|lat|lon|  |
|0x15 / 21    |MAV\_CMD\_NAV\_LAND|-   |altitude|lat|lon|  |
|0x16 / 22    |MAV\_CMD\_NAV\_TAKEOFF|takeoff pitch|altitude|- |- |注:對於 0x16 的命令而言，這是起飛仰角的最小值，這個範例使用空速計而如果是目標仰角則沒有。|
|0x17 / 23    |MAV\_CMD\_NAV\_TARGET|-   |altitude|lat|lon|  |



---

**可能命令 - 這些命令有一個終止條件，可能會終止。終止條件例如"到達航點"或者"到達高度"**

|命令ID|名稱|參數 1|參數 2|參數 3|參數 4|備註|
|:---|:-|:---|:---|:---|:---|:-|
|0x70 / 112|MAV\_CMD\_CONDITION\_DELAY|-   |-   |時間 (秒)| -  |  |
|0x71 / 113|MAV\_CMD\_CONDITION\_CHANGE\_ALT |速率 (厘米/秒)|高度 (終止)|-   |-   |注: 速率必須大於 10 厘米/秒，原因為整數運算精度問題|
|0x72 / 114|MAV\_CMD\_CONDITION\_DISTANCE|-   |-   |距離 (米)|-   |  |



---

**立即命令 - 如果沒有新的命令傳入，這些命令只執行一次**

(**Note: DO\_xxx 命令目前需要一個假航點放置之後的命令**<br>
eg:<br>
<br>
WAYPOINT_1<br>
DO_SET_HOME<br>
WAYPOINT_2<br>

家位置會被設為 WAYPOINT_1 但如果沒有 WAYPOINT_2 則沒有作用。)<br>
<br>
<table><thead><th>命令ID</th><th>Name</th><th>參數 1</th><th>參數 2</th><th>參數 3</th><th>參數 4</th><th>備註</th></thead><tbody>
<tr><td>0xB1 / 177</td><td>MAV_CMD_DO_JUMP</td><td>index</td><td>-   </td><td>repeat count</td><td>-   </td><td>註: 要執行的命令重複次數必須大於1。如果你打算使用一次請輸入 1。 </td></tr>
<tr><td>0xB2 / 178</td><td>MAV_CMD_DO_CHANGE_SPEED </td><td>Speed type</td><td>Speed (m/s)</td><td>Throttle (Percent)</td><td>-   </td><td>(0=空中速度, 1=地面速度)(-1 indicates no change)(-1 indicates no change)</td></tr>
<tr><td>0xB3 / 179</td><td>MAV_CMD_DO_SET_HOME</td><td>Use current </td><td>altitude</td><td>lat </td><td>lon </td><td>(1= 使用當前位置，0= 使用指定位置)</td></tr>
<tr><td>0xB4 / 180</td><td>MAV_CMD_DO_SET_PARAMETER</td><td>Param number</td><td>Param value</td><td>    </td><td>    </td><td>(當前未實現)</td></tr>
<tr><td>0xB5 / 181</td><td>MAV_CMD_DO_SET_RELAY</td><td>Relay number</td><td>On/off  (1/0)</td><td>-   </td><td>-   </td><td>  </td></tr>
<tr><td>0xB6 / 182</td><td>MAV_CMD_DO_REPEAT_RELAY</td><td>Relay number</td><td>Cycle count</td><td>Cycle time (sec)</td><td>-   </td><td>註:  Max cycle time = 60 sec，重覆繼電器或伺服機的命令將會取消任何目前正在重覆的事件</td></tr>
<tr><td>0xB7 / 183</td><td>MAV_CMD_DO_SET_SERVO</td><td>Servo number (5-8)</td><td>On/off  (1/0)</td><td>-   </td><td>-   </td><td>  </td></tr>
<tr><td>0xB6 / 184</td><td>MAV_CMD_DO_REPEAT_SERVO</td><td>Servo number (5-8)</td><td>Cycle count</td><td>Cycle time (sec)</td><td>-   </td><td>註:  Max cycle time = 60 sec，重覆繼電器或伺服機的命令將會取消任何目前正在重覆的事件</td></tr>