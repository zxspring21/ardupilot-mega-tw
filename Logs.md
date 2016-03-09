## 可用的數據記錄類型 ##

這裡的資料型態可以被記錄於板子上dataflash的記憶體。可以將它們打開或者輸入至 `enable [log name]` CLI 記錄選單：

| **Log 名稱** | **預設值** | **作用** |
|:-----------|:--------|:-------|
|ATTITUDE\_FAST|DISABLED |記錄基本的高度訊息至 dataflash，記錄頻率為 50Hz (會使用較多的空間)|
|ATTITUDE\_MED|ENABLED  |記錄基本的高度訊息至 dataflash ，記錄頻率為 10Hz (使用的空間會少於 LOG\_ATTITUDE\_FAST)|
|GPS         |ENABLED  |記錄 GPS 訊息至 dataflash，記錄頻率為 10Hz|
|PM          |DISABLED |每20秒記錄一次 IMU 效能監控訊息。|
|CTUN        |DISABLED |記錄控制迴路調整信息，記錄頻率為  10 Hz。這個信息在調整舵機的控制迴路增益值是非常有用。|
|NTUN        |DISABLED |記錄導航調整信息，記錄頻率為  10 Hz。這個信息在微調導航控制迴路增益值是非常有用的。|
|MODE        |ENABLED  |記錄發生變化時的飛行模式。|
|RAW         |DISABLED |記錄原始的的加速度計和陀螺儀數據，記錄頻率為 50 Hz(會使用較多的空間)。|
|CMD         |ENABLED  |記錄流程中新的命令|