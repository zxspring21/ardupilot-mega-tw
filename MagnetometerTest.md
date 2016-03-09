## 地磁儀 測試 ##

**說明:**

1.0代碼不支持地磁儀。但如果你有地磁儀的話，可以用  \libraries\APM\_Compass\examples 目錄中的 `APM_Compass_test` 文件測試。

將該固件傳到你的板子上，通過串口終端觀察數據。串口波特率為38,400。

連接地磁儀的說明在[這裡](Magnetometer.md).

(**注**: 目前板子的方向標誌是錯的。正確的標誌請參見[該帖](http://www.diydrones.com/forum/topics/hmc5843-3-axis-magnetometer)。)

**典型數據:**

![http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/magtest.png](http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/magtest.png)

**故障檢修:**

記住地磁儀只關注方向。如果方向數據反了，可能是你把板子上下顛倒了(即將地磁儀焊接到板子上那樣)。不用擔心——在設置裡面可以配置。