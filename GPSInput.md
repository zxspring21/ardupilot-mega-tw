
## GPS輸入 ##

**說明**: 本測試顯示GPS模組的輸出。該模組應該插在APM板的GPS端口上。通常情況下，只有在戶外空曠地點測試GPS才有意義。某些GPS模組在木製建築內也可以鎖定衛星（如果GPS與天空之間沒有間隔太多層的話，但是結果不可預料）。當GPS模組冷啟動時（一天以上沒有通電），通常需要約15分鐘才能鎖定衛星。

**典型數據:**

![http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/gpstest.png](http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/gpstest.png)

**故障檢修:** 如果你在戶外很長時間（15分鐘以上）都無法鎖定衛星，可能的原因包括:

  * 如果你使用 MediaTek GPS 模組, 需要在上電之後重置 APM 板，才能正確發送配置字串。我們未來會修正這個問題，但現在應在測試GPS之前按一下重置按鈕。
  * 你確定將 GPS 插到 APM 板上，而不是 IMU 板上那個差不多的端口（寫著 "NO GPS!"）上?
  * 傳輸線有問題 (檢查連接器的針是否彎曲)
  * GPS 固件損壞。重新加載固件的說明在這裡：[uBlox](http://code.google.com/p/ardupilot/wiki/ublox), [MediaTek](http://code.google.com/p/ardupilot/wiki/MediaTek)
  * 你使用的GPS模組不受支持。當前僅支持 DIY Drones 的 uBlox 和 MediaTek 模組