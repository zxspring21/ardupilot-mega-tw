## 數據記錄 ##

有兩種方法記錄 APM 飛行數據：使用內建 16MB 的 Flash 存儲器，並在地面上下載，和/或用地面站記錄在飛行中的 XBee/3DR 遙測數據流。

### 記錄遙測數據 ###

**Mission Planner :**

當 MAVLink 連接時遙測數據被自動記錄。文件在你的 Mission Planner 文件夾下的「log」子文件夾裡，並給定的數據/時間命名（可以重命名）。裡面會有兩種類型的副檔名：".tlog" 及 ".rlog"。一般來說你只會使用到`tlog`的檔案；`rlog`主要是用於除錯並且包含所有從 APM 的序列輸出，包含除錯訊息。

你可以加載和回放任何一個`tlog`，也可以單擊 KMZ 按鈕，把記錄轉換為 Google Earth 可以顯示的 KMZ 文件。

![http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/mavlogs.png](http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/mavlogs.png)


### 板上數據記錄 ###

APM 板上的 16MB 數據記錄存儲器會自動錄飛行的數據和APM的性能。

在 CLI 模式下只能使用 USB 連接 APM，你可用任務規劃器的 Terminal 頁面的按鈕下載這些日誌。他們將被保存在你的日誌文件夾中。如果你單擊「重建KML」，會該文件夾下創建一個可以在 Google Earth 上查看的任務。

![http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/dataflashlogs.png](http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/dataflashlogs.png)

在每天的飛行前清空存儲器裡的記錄是個好主意。如果存儲器滿了，新的紀錄會存儲內存的頭部，覆蓋最舊的記錄。


下面是板上數據存儲器可以記錄的數據類型。你可以在[CLI](http://code.google.com/p/ardupilot-mega/wiki/CLI) Logs 菜單下輸入 {enable [記錄名]}}} 打開或關閉它們，如下所述：

| **記錄名** | **默認** | **功能** |
|:--------|:-------|:-------|
|ATTITUDE\_FAST|未啟用     |記錄基本姿態信息，50Hz（使用更多空間）|
|ATTITUDE\_MED|啟用      |記錄基本姿態信息，10Hz (比 LOG\_ATTITUDE\_FAST 需要空間少點)|
|GPS      |啟用      |記錄 GPS 信息，10Hz.|
|PM       |未啟用     |記錄 IMU 性能監視信息，每 20 秒.|
|CTUN     |未啟用     |記錄控制循環調整信息，10 Hz。這個信息對調整舵機控制循環感度有用。|
|NTUN     |未啟用     |記錄導航調整信息，10 Hz.  這個信息對調整導航控制循環感度有用。|
|MODE     |啟用      |記錄飛行模式變化。|
|RAW      |未啟用     |記錄原始加速度計和陀螺數據，頻率 50Hz（使用更多空間）。|
|CMD      |啟用      |記錄執行的新命令。|


## 使用 Mission Planner 讀取和分析記錄 ##

下載和分析記錄文件最方便的方法是使用任務規劃器，它可以顯示圖標數據，生成Google Earch使用的KML文件，靈活管理數據。詳細說明請參見[這裡](MPDatalog.md).

## 使用CLI讀取記錄 ##

你也可以用[CLI](CLI.md)下載記錄。 在CLI中輸入 {{{logs}}, 並按 Enter 鍵進入該模式。可用的命令包括:

  * **"dump _n_"**: 顯示記錄 _n_。
  * **"erase"**: 清除所有記錄。
  * **"enable _name_"**: 開啟記錄 _name_。  輸入 "all" 開始記錄所有信息。
  * **"disable _name_"**: 停止記錄 _name_。  輸入 "all" 停止記錄所有信息。

注意如果 APM 啟動時，滑動開關的位置推離板子的邊緣，那麼記錄將從 Flash 存儲器的起始位置開始保存，也就是說會覆蓋以前的記錄內容。