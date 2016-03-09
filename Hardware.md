# ArduPilot Mega 硬件 #

(作者 Jordi Munoz)

  * ArdupilotMega 板也稱為: APM, 紅板, 控制器, 或主板。板子由 SparkFun 製造。
  * ArduPilotMega 蓋板/Oilpan 也稱為: APM 蓋板, APM Oilpan, the oilpan, 蓋板, 傳感器板, 藍板或從板。板子由 DIYdrones 製造。
  * The original version of APM had an ATmega1280 processor. In early 2011, this was upgraded to an ATmega2560 processor and all boards shipped since then have used the 2560. The pictures below show the original board.

**板子正面:**

![http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/d972wmb_2f33fzqft_b.jpg](http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/d972wmb_2f33fzqft_b.jpg)

**板子背面:**

![http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/d972wmb_3htt634d2_b.jpg](http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/d972wmb_3htt634d2_b.jpg)

## 板子供電 ##
通常情況下，你用遙控系統為板子供電，要麼將遙控接收器的通道連接到 ArduPilot Mega，要麼將電調連接到 ArduPilot Mega 的油門輸出通道上。

但是，APM 板也有自己的電源系統，因此可以用單獨的電池直接供電 (比如你不用遙控系統，或者希望將 APM 的電源與遙控的電源隔離開）。要這麼做的話，你要焊開 SJ1 跳線 (如下圖所示)，並將一塊 7v 到 11v (最好是 7.4v 2C 電池）直接連接到 +- 腳上。內建的 5V 穩壓器 (LM317) 最大可以提供 1A 電流。

![http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/apm14power.jpg](http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/apm14power.jpg)

連接到板子上的其他組件 (例如 Atmega1280, Atmega328, LED, 復用器等)的5V 電源線中間串聯了一個 500mA 可恢復保險絲。這個保險絲只負責集成電路部分，而不管舵機部分，這樣你就可以用大電流舵機而不會意外地觸發保險絲（保險絲觸發後將關閉所有電子部件，想像一下如果飛機正在空中...）。使用保險絲可以在短路的情況下保護板子。在老版本的 Ardupilots 很多人出過這個事故，包括我...

下面的圖顯示了我所說的部分:


## APM 1280/2560 ##

![http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/Drawing1.png](http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/Drawing1.png)

Arduino Mega 的核心是一個 Atmel 製造的 Atmega2560 微控制器，帶有 256kB 閃存和許多引腳!(較舊的 1280 有 128k 的記憶體)

這個怪物有 4 個 16位定時器，每個定時器有 3 個獨立的輸出捕獲(PWMs)和 1 個輸入捕獲。用一些代碼技巧我們可以使用一個定時器來執行 2 個輸出捕獲和 1 個輸入捕獲。輸出捕獲用來產生脈寬調製信號控制舵機，輸入捕獲用來解碼脈寬調製信號或者 PPM 信號。在這裡我們用一個定時器來解碼 Atmega328p 發送的 PPM 信號。這個 Atmega328p 將 8 通道的信號合成到一個通道中(一石八鳥，實際上是十鳥)，另外兩個輸出捕獲用來控制舵機。每個定時器我們只用了 2 個輸出捕獲(總共 8 個輸出捕獲)，另外一個輸入捕獲用來讀取編碼在 PPM 幀裡的 8 個舵機輸入信號。換句話說我們可以讀寫 8 個 PWM 通道，卻只用少於 1% 的 CPU 處理能力。 ;-)

板子還有一個 16 通道模數轉換器，解析度為一般般的 10 位。這些引腳還可以用來充當數字輸入輸出引腳。我們還引出了空餘的數字輸入輸出引腳，4 個串口 (一個用來變成，一個用來連接標準 EM-406 GPS 接口).

與 APM IMU 板一起, 4 個串口的功能如下:

|Port 0:|USB|
|:------|:--|
|Port 1:|GPS|
|Port 2:|Dataflash|
|Port 3:|Xbee|

Atmega 1280 預先燒錄了 Arduino Bootloader，但是你也可以在任何時候用 SPI 端口處理微控制器的內部設置。

## PCB設計文件 ##

APM 板:

  * [電路圖](http://www.sparkfun.com/datasheets/DevTools/Arduino/ArduPilotMega_v12.pdf)
  * [PCB](http://www.sparkfun.com/datasheets/DevTools/Arduino/ArduPilotMega_v12.zip)

## 針腳定義 ##

所有針腳的定義和功能說明在[這裡](https://spreadsheets0.google.com/ccc?key=t2UjzAY9aBvnXBuw2AFgAnQ&authkey=CKzJv_IP&hl=en#gid=0)