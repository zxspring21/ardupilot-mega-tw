=連接 PPM-Sum 接收器=
_在 FrSky 的接收器稱作 CPPM_

**PPM\*及PWM是2個完全不一樣的無線資訊協定。**PPM\*的優點是只需要透過1個通訊埠得到所有的通道資訊。也可以讓你取得額外的通道，例如 FrSky D8RSP 接收器就可以輸出 7 個 PPM 頻道，在 CPPM 模式時可以到達 8 個。

不管是 APM1 及 APM2 你只要將跳線插入輸入端的通道 2 及 3(只可以使用訊號腳)。PPM 輸入應該會提供給通道 1。


## APM 2 ##
![http://wiki.ardupilot-mega.googlecode.com/git/images/APM2/FRAMES_input_PPM.jpg](http://wiki.ardupilot-mega.googlecode.com/git/images/APM2/FRAMES_input_PPM.jpg)


## APM 1 ##

為了讓你在 APM 1.x 板上使用PPM-sum 你也許會需要更新你的 PPM 編碼器的韌體。

**[APMv1.x. Arducopter 的 PPM 編碼器](http://code.google.com/p/ardupilot-mega/downloads/detail?name=ArduPPM_v0.9.87_Arducopter-APMv1.4.hex)**

**[APMv1.x. Arduplane 的 PPM 編碼器(支援 CH8 的無線通訊)](http://code.google.com/p/ardupilot-mega/downloads/detail?name=ArduPPM_v0.9.87_Arduplane-APMv1.4.hex)**

**[燒錄 Atmega328p (PPM 編碼器)](http://code.google.com/p/ardupilot-mega/wiki/Encoder)**

**[ArduPPM 編碼器操作手冊](http://code.google.com/p/ardupilot-mega/downloads/detail?name=ArduPPM_v0.9.87_manual.txt)**

![http://wiki.ardupilot-mega.googlecode.com/git/images/APM1/PPM_APM14.jpg](http://wiki.ardupilot-mega.googlecode.com/git/images/APM1/PPM_APM14.jpg)