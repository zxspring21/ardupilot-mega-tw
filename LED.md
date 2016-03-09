# LED和它們的涵義 #


---


## APM 2.5 板 ##

![http://wiki.ardupilot-mega.googlecode.com/git/images/APM25leds2.png](http://wiki.ardupilot-mega.googlecode.com/git/images/APM25leds2.png)

| **LEDs:** | **行為:** |
|:----------|:--------|
|Power      | 通電時亮    |
|PPM/Serial | 當偵測到數據時閃爍 |
|ABC        | 請見下列說明  |


---


### APM 2.0 板 ###

![http://wiki.ardupilot-mega.googlecode.com/git/images/APM2/LED_and_their_meaning_APM2.jpg](http://wiki.ardupilot-mega.googlecode.com/git/images/APM2/LED_and_their_meaning_APM2.jpg)

| **LEDs:** | **行為:** |
|:----------|:--------|
|Power      | 通電時亮    |
|3D Fix     | 當 GPS 未鎖定時閃爍；常亮表示已鎖定 |
|ABC        | 請見下列說明  |


---


### APM 1 板 ###

![http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/APM.jpg](http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/APM.jpg)


| **LED:** | **行為:** |
|:---------|:--------|
|Power     |通電時亮     |
|MUX       |觸發開關不為手動模式時亮 |
|PPM       |PPM 編碼器工作時閃爍 |

## APM 1 IMU 板 ##
![http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/LEDs.jpg](http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/LEDs.jpg)


## APM LED 定義 ##

| **LED:** | **行為:** |
|:---------|:--------|
|<font color='2AAAFF'><b>Powe</b></font> |通電時亮     |
|<font color='FF7F00'><b>TX</b></font> |指示數據從 USB/FTDI 口輸入 |
|<font color='FF7F00'>RX**</font>**|只是數據向 USB/FTDI 口輸出 |
|<font color='green'><b>A</b></font> <font color='red'>C</font>|陀螺儀校準時快速閃爍，然後暫停，然後循環閃爍（總共約45秒)。|
|<font color='FF7F00'><b>B</b></font> | 閃爍 = 校驗。 常亮 = 準備起飛但GPS未鎖定 |
| <font color='red'>C</font>| GPS 鎖定 - <font color='red'>C</font>**在等待 GPS 鎖定時閃爍; 當 GPS 鎖定後常亮。**|
| <font color='FF7F00'><b>B</b></font> <font color='red'>C</font>| 常亮 <font color='FF7F00'><b>B</b></font> 及 <font color='red'>C</font>**飛機已準備起飛，GPS已準備完成**|         |