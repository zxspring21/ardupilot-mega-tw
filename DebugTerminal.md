#summary 如何用人類可讀的文本命令與 APM 交互

# 使用調試終端與 APM 交互 #

## 描述 ##
調試終端地面站協議通過基本的終端程序，以一種人類可讀的基於文本方式與 APM 交互。使用調試終端地面站，用戶可以修改很多 APM 的行為，甚至可以在飛行中修改，該可以讀取很多種信息，更清楚地瞭解 APM 的運行情況。

調試終端主要用於探索和測試 APM 的行為，目前不適合用作最終用戶界面。很多狀態報告是根據代碼中如何計算組織的，而不是根據不看代碼的用戶的直覺組織的。這就使得它是一個理解 APM 正在想什麼的一個好工具，但作為用戶界面來說十分粗糙。當調試終端返回非你所料的數據，檢查產生數據的代碼，看看你能否發現它為什麼如此運行。

一個普遍的問題是數據在 APM 存在的方式和人類容易理解的方式存在衝突。例如，緯度在機器內部是一個整數，數值為角度值乘以一千萬。但是，把它以小數的方式顯示對人來說更容易理解。目前，調試終端混雜著以上兩種顯示數據的方式。最新和最常用的命令傾向於顯示人容易理解的數字。舊的和不常用的命令傾向於顯示原始數據, 這些數據經常是實際意義的 100 倍。

## 設置 ##
下面是使用調試終端與 APM 交互的步驟:
  1. [將串行接口連接到遙測端口上](Wireless.md)
  1. 在 [APM\_Config.h](AdvancedConfig.md) 文件末尾增加以下代碼行:
```
 //Select Debug Terminal as the GCS to use:
 #define GCS_PROTOCOL        GCS_PROTOCOL_DEBUGTERMINAL

 //Use the telemetry port for the Debug Terminal interface:
 //(selecting 0 here would cause the USB serial port to be used instead)
 #define GCS_PORT            3

 //Set the baud rate for the telemetry port to match your XBee setup:
 #define SERIAL3_BAUD        115200
```

## 命令參考 ##
在默認模式下，調試終端可以提供命令語法的助記信息。如果你不記得某條命令，就輸入你記得的那些，然後在後面加上 `-?`。僅輸入 `-?` 可以獲得命令組的列表。例如，`status -?` 將打印一個識別的 `status` 命令列表:

所有的調試命令都對大小寫和空白符敏感。 命令以回車結束（因此在 Arduino 串口監視器中記住選擇 {{Carriage return}}}，不要選擇 `No line ending`)。下面的參考中，`<N>` 表示一個非負整數。`<X>` 表示一個實數。垂線 | 表示 "或"，大括號包括所有可選項。因此，` {A|B|C} `表示你必須選擇 `A` 或 `B` 或 `C`。 方括號表示可選的參數。更多信息可以參考 `GCS_DebugTerminal.pde` 的代碼。(SVN 庫在 [這裡](http://code.google.com/p/ardupilot-mega/source/browse/ArduPilotMega/trunk/GCS_DebugTerminal.pde)).

**`show heartbeat`**
> 自動顯示"心跳"消息，報告 APM 的控制模式，特別是當模式發生改變時。這些數據默認顯示。

**`show attitude`**
> 自動顯示"姿態"消息，表明::
    * 側傾、俯仰、偏航和油門的遙控信號
    * APM 復原的飛機側傾角度和俯仰角度
    * 導航信息，包括目標方位、預期側傾角度和偏航角度。
    * 方向驅動數據，包括側傾和俯仰舵機輸出

**`show location`**
> 自動顯示 GPS 位置和:
    * 空速
    * 爬升率
    * 離航點的距離Distance from waypoint
    * 油門百分比
    * 預期高度和當前高度的差值

**`show severity <N> `**
> 顯示重要程度高於 N 的消息

**`hide {heartbeat|attitude|location} `**
> 關閉相應消息的自動顯示

**`hide all`**
> 關閉所有自動顯示的消息

**`echo <text>`**
> 通過串口線送回 `echo` 和回車之間的文本

**`groundstart`**
> 強制地面啟動，將（重新）初始化並（重新）校準 IMU

**`inithome`**
> 設置當前地點為返航點

**`print altitude`**
> 打印一條高度消息

**`print attitude`**
> 打印一條姿態消息 (參照 `show attitude` 說明)

**`print commands`**
> 打印所有存儲在 EEPROM 中的命令列表 (條數由 wp\_total 決定)

**`print ctrlmode`**
> 打印一條心跳消息

**`print curwaypts`**
> 打印當前自動導航用到的三個航點

**`print flightmodes`**
> 打印飛行模式

**`print kp {servoroll|servopitch|servorudder|navroll|navpitchasp|navpitchalt|throttlete|throttlealt} `**
> 打印選擇的 PID 通道當前的誤差比例增益常數。每個通道的說明請參閱 [通道](PID.md)。

**`print ki {servoroll|servopitch|servorudder|navroll|navpitchasp|navpitchalt|throttlete|throttlealt} `**
> 打印選擇的 PID 通道當前的誤差積分增益常數。每個通道的說明請參閱 [通道](PID.md)。

**`print kd {servoroll|servopitch|servorudder|navroll|navpitchasp|navpitchalt|throttlete|throttlealt} `**
> 打印選擇的 PID 通道當前的誤差微分增益常數。每個通道的說明請參閱 [通道](PID.md)。

**`print kff {pitchcomp|ruddermix|pitchtothrottle} `**
> 打印通道混控常數
    * pitchcomp: Additional up-elevator to add when the plane is banked
    * ruddermix: How much rudder should be deflected with roll to keep the plane in approximately coordinated flight
    * pitchtothrottle: _Currently unused_

**`print location`**
> 打印最後記錄的 GPS 位置 (current\_loc)

**`print navsettings`**
> 打印各種導航常數:
    * 巡航空速(如果裝有空速傳感器)或巡航油門(沒有空速傳感器)
    * 保持在返航點上空的高度
    * 盤旋半徑
    * 航點半徑

**`print pressure`**
> 打印 BMP085 傳感器信息

**`print rlocation [home]`**
> 打印飛機相對於原點的相對位置（笛卡爾坐標）。如果沒有設置返航點（`home`）, 原點就是下一個航點

**`print speed`**
> 打印速度

**`print tuning`**

**`reset commands`**
> 發出一條 reload\_commands() 調用

**`rtl`**
> 開始返航 (return\_to\_launch())

**`set cmd <commandindex> <commandtype> <param1> {here|<alt> <lat> <lng>} `**
> `commandindex` > 0<br />
> `commandtype` = {waypoint|takeoff|land|loiter|loiternturns|loitertime|delay|landoptions|resetindex|airspeedcruise|throttlecruise|resethome|index|`<N>` }<br />
> 設置 EEPROM 中的一條命令 (does not necessarily load the command even if the command index being set is the current one). `param1` 的作用取決於[命令類型](Commands.md), 但是必須是非負整數。當指定一個位置時，`alt`（高度）單位為米(通常相對於起飛點的高度）, `lat`（緯度）和`lng`（經度）的單位為度，數據都是實數。除了用高度和經緯度指定位置之外，還可以用 `here` 替代，將使用飛機當前的位置。This is useful to quickly set up a mission by having an assistant simply fly to the desired locations.
> 例子:
```
 set cmd 1 takeoff 10 15 0 0
 set cmd 2 waypoint 0 here
 set cmd 3 waypoint 0 15 34.090956 -118.032020
 set cmd 4 land 0 0 34.089355 -118.032932
 set cmd 5 landoptions 10 10 15 -5
 set cmd 6 rtl 0 0 0 0
```

**`set cmd <commandindex> <paramtype> <newvalue>`**
> `commandindex` > 0<br />
> `paramtype` = {id|p1|alt|lat|lng|p2|p3|p4}<br />
> 修改 EEPROM 中一條命令的一個參數並保存修改。`alt`（高度）, `lat`（緯度）和 `lng`（精度）分開處理，因此確保僅在描述這些特性時使用這些標識符。 For instance, never set the `lat` parameter on a landoptions command.  This command is particularly useful for setting the correct altitudes after defining a rough course using the `here` identifier

**`set cmdcount <N>`**
> 設置預計的有效命令條數; 實際上這並不使命令變得有效

**`set cmdindex <N>`**
> Sets and loads the desired command.  Index 0 is home, index 1 is the first user-defined command in the mission, and is the command the APM will start with when the plane is initialized

**`set cruise <X>`**
> 設置新的巡航速度（單位米/秒，如果安裝了空速傳感器）或者油門百分比（沒有空速傳感器）

**`set holdalt <X>`**
> 設置並保存新的返航點盤旋高度

**`set kp {servoroll|servopitch|servorudder|navroll|navpitchasp|navpitchalt|throttlete|throttlealt} <X>`**
> 設置比例增益常數。更多信息參見 `print kp`

**`set ki {servoroll|servopitch|servorudder|navroll|navpitchasp|navpitchalt|throttlete|throttlealt} <X>`**
> 設置積分增益常數。更多信息參見 `print ki`

**`set kd {servoroll|servopitch|servorudder|navroll|navpitchasp|navpitchalt|throttlete|throttlealt} <X>`**
> 設置微分增益常數。更多信息參見 `print kd`

**`set kff {pitchcomp|ruddermix|pitchtothrottle} <X>`**
> Sets feed-forward constant.  See `print kff` for more information.

**`set loiterradius <X>`**
> 設置並保存新的盤旋半徑

**`set wpradius <X>`**
> 設置並保存新的航點半徑 (APM必須到達離航點多近的位置)

**`status control`**
> 顯示基本控制狀態信息，包括預期的側傾角和俯仰角

**`status gps`**
> 顯示 GPS 狀態

**`status landing`**
> 顯示著陸狀態

**`status loiter`**
> 顯示盤旋狀態

**`status navigation`**
> 顯示導航狀態

**`status navpitch`**
> 顯示導航俯仰角狀態

**`status navroll`**
> 顯示導航側傾角狀態

**`status rc`**
> 總結所有遙控通道從硬件脈寬檢測到硬件脈寬調製輸出的狀態，

**`status rcinputch`**
> 測量並顯示所有通道的脈寬值; this is as close to the hardware as it is practical to get from the APM main code

**`status rcin`**
> 顯示緩衝的和混控調整之後的通道脈寬等

**`status rcout`**
> 顯示緩衝的和混控調整之後的輸出通道脈寬等

**`status rcpwm`**
> 顯示當前所有通道的硬件 PWM 生成器設置; this is as close to the hardware as it is practical to get from the APM main code

**`status rctrim`**
> 顯示所有遙控通道的修正值

**`status system`**
> 顯示系統狀態

**`status takeoff`**
> 顯示起飛狀態

**`status telemetry`**
> 顯示無線狀態

**`status throttle`**
> 顯示油門狀態

**`status waypoints`**
> 顯示航點狀態