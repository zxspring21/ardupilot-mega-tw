**說明**: 本測試僅在如[此說明](http://code.google.com/p/ardupilot-mega/wiki/Voltage)所述的電壓傳感器之後有效。四個數據位是四個分壓器的輸出值。如果你照上述說明所述連接電池，這將表示電池每個電芯的電壓——3S電池有3個電芯，4S電池有4個。由於電芯是串聯的，因此最後一個電池電壓就是電池組的總電壓。

在下圖所示的例子中，我使用了一個3S 11.1v 電池（實際上是11.4v）。第4個分壓器沒有使用，所以可以忽略那一列數據。

**樣例數據**:

![http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/battery.png](http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/battery.png)