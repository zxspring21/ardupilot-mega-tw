## APM測試套件 ##

APM 附有17個測試功能，可以檢查所有主要的子系統。因此你可以一個一個檢查它們是否工作正常。

要使用測試功能，在CLI中輸入 "test"，然後輸入"help"，可以看到所有的測試功能:

![http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/tests.png](http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/tests.png)

可用的測試包括:

  * **"pwm**: 顯示目前每個遙控通道的輸入讀數
  * **"radio"**: 顯示目前每個遙控通道的輸入讀數
  * **"passthru"**: 顯示 PWM 訊號在手動模式時通過遙控的讀數
  * **"failsafe"**: 測試無線電失去訊號的狀況。請按照測試的說明。
  * **"battery"**: 顯示當前的電池電壓(需安裝電壓監視器)
  * **"relay"**: 測試板上的繼電器(每5秒開關一次，你應該能聽到滴答聲)
  * **"waypoints"**: 顯示當前設置的航點
  * **"xbee"**: 顯示從Xbee無線模塊讀入的數據(需安裝Xbee模塊)
  * **"eedump"**: 導出板上EEPROM存儲器的當前數據
  * **"modeswitch"**: 顯示目前模式所切換的開關位置
  * **"gps"**: 顯示GPS模塊的當前數據。如果 GPS 沒有鎖定，那麼結果是 0
  * **"rawgps"**: 顯示 GPS 模組的原始輸出，通常用於診斷 GPS 的問題
  * **"imu"**: 顯示當前的x,y,z軸姿態
  * **"airspeed"**: 顯示差分氣壓傳感器數據(需安裝差分氣壓傳感器)
  * **"airpressure"**: 顯示板上的絕對氣壓傳感器的數據
  * **"compass"**: 顯示地磁計的數據(需安裝地磁計)
  * **"logging"**: 回報記憶卡的版本及容量


請點擊左側導航欄相應項目，查看每個測試的說明和典型數據。