## 遙控輸入 ##

**說明**: 照[此說明](RCSetup.md)連接遙控接收機和APM。 打開發射器，移動搖桿。

輸入以脈寬調變(PWM)值的方式顯示。輸入則以舵機偏移角度的方式顯示。在串口控制台中輸入回車退出本測試。

**典型數據:**

![http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/rctest.png](http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/rctest.png)

**故障檢修:** 如果所有的顯示值都不隨你的遙控輸入變化，可能的原因包括:

  1. 你沒有配置遙控輸入。參見[相關說明](CLI.md)。
  1. 遙控連線不正確。(插反了?)
  1. 你拿到的可能是早期有問題的固件。你可以自行升級固件，請參考[本說明](Encoder.md)。（譯注:國內版本應該不存在該問題）