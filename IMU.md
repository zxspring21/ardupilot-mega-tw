## IMU 輸出 ##

**說明**: 本測試記錄板子移動時，DCM算法的輸出結果。當傳感器校準時，IMU 板上的LED將快速閃爍20-30秒，然後開始顯示數據。偏航(yaw)數據可能略有漂移，因為它只能根據運動時的GPS數據和/或地磁計（如果使用了的話）數據進行校正，而這些數據在室內通常不正確。

**旋轉板子時的典型數據 (roll, pitch, yaw):**

![http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/imutest.png](http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/imutest.png)

**故障檢修:** 如果板子移動時數據不變，可能有電路連接問題，最可能是焊接錯誤引起的。檢查焊點!