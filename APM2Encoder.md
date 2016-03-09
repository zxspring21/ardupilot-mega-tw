== 如何過USB刷新 Atmega32U2 (PPM encoder) ==

The PPM encoder (ATMega32-U2) has an special bootloader that allows you to flash it without needing a special SPI programmer.

### 你需要下列幾種東西 ###

  * Windows XP/Vista/7
  * USB cable
  * 下載並安裝 Flip，請點擊 [這裡](http://dl.dropbox.com/u/42979535/JRE%20-%20Flip%20Installer%20-%203.4.3.exe)下載這個教程的版本. 如果你想要下載最新版本請點擊 [這裡](http://www.atmel.com/dyn/products/tools_card.asp?tool_id=3886)。
  * 載入firmware (HEX file)， APM 2隨板附加的在[這裡](http://code.google.com/p/ardupilot-mega/downloads/detail?name=ArduPPM_v2.2.65_ATMega32U2.hex&can=2&q=). 你也可以在[Git程式庫](http://code.google.com/p/ardupilot-mega/source/browse/#git%2FTools%2FArduPPM%2FBinaries)找到最新的版本。



### 將Atmega32U2改為燒錄(DFU)模式 ###

1) 安裝完flip之後，使用USB線將APM 2.0連接至電腦。

2) 開啟電源，將jumper放到JP2，如下圖所示:

![http://wiki.ardupilot-mega.googlecode.com/git/images/APM2/PPMencoder_APM2_jumper.jpg](http://wiki.ardupilot-mega.googlecode.com/git/images/APM2/PPMencoder_APM2_jumper.jpg)

3) 為了要重置Atmega32U2請使用小鐵片將GND與Atmega32U2的RST短路一下。你可以在ICSP的板邊找到這些Pin孔：

![http://wiki.ardupilot-mega.googlecode.com/git/images/APM2/PPMencoder_APM2_jumper_2.jpg](http://wiki.ardupilot-mega.googlecode.com/git/images/APM2/PPMencoder_APM2_jumper_2.jpg)

4) 重置完後你會聽到Windows電腦發出連接USB的音效。你的板子應該就處於DFU模式，現在可以準備燒錄資料了。

### 使用FLIP上傳firmware ###
1.- 點擊flip圖示開啟flip：

![http://wiki.ardupilot-mega.googlecode.com/git/images/flip_icon.jpg](http://wiki.ardupilot-mega.googlecode.com/git/images/flip_icon.jpg)


2.- 開啟後你會看到window畫面如下:

![http://wiki.ardupilot-mega.googlecode.com/git/images/flip_main.jpg](http://wiki.ardupilot-mega.googlecode.com/git/images/flip_main.jpg)

3.- 點擊紅色箭頭所指的圖示或到主選單選擇「Device->Select」，也可以使用快捷鍵「Ctrl+S」，選擇Atmega32U2點擊「OK」。

![http://wiki.ardupilot-mega.googlecode.com/git/images/flip_step3.jpg](http://wiki.ardupilot-mega.googlecode.com/git/images/flip_step3.jpg)

4.- 點擊紅色箭頭所指的地方或到主選單選擇「Settings->Communications->USB」，也可以使用快捷鍵「Ctrl+U」後點擊「Open」。

![http://wiki.ardupilot-mega.googlecode.com/git/images/flip_step4.jpg](http://wiki.ardupilot-mega.googlecode.com/git/images/flip_step4.jpg)

5.- 如果所以的步驟都正確的執行你會看到Signature bytes等等，如下圖所示:

![http://wiki.ardupilot-mega.googlecode.com/git/images/flip_main_loaded.jpg](http://wiki.ardupilot-mega.googlecode.com/git/images/flip_main_loaded.jpg)

6.- 現在我們點擊紅色箭頭所指的圖示載入HEX或到主選單選擇「File->Load HEX」，也可以使用快捷鍵「Ctrl+L」選擇HEX檔案下載完後點擊「OK」。

![http://wiki.ardupilot-mega.googlecode.com/git/images/flip_step6.jpg](http://wiki.ardupilot-mega.googlecode.com/git/images/flip_step6.jpg)

7.- 現在請確認你已經選擇所有「Operations Flow」的選項，紅色箭頭所指的地方都要打勾。

![http://wiki.ardupilot-mega.googlecode.com/git/images/flip_step7.jpg](http://wiki.ardupilot-mega.googlecode.com/git/images/flip_step7.jpg)

8.- 點擊「Run」紅色箭頭所指的地方，系統就會上傳fireware，幸運的話你已經正確的安裝，你會發現所有的選項皆變為綠色如圖所示:

![http://wiki.ardupilot-mega.googlecode.com/git/images/flip_step8.jpg](http://wiki.ardupilot-mega.googlecode.com/git/images/flip_step8.jpg)

現在可以移除jumper及APM 2.0 的電源。

![http://wiki.ardupilot-mega.googlecode.com/git/images/APM2/PPMencoder_APM2_jumper_3.jpg](http://wiki.ardupilot-mega.googlecode.com/git/images/APM2/PPMencoder_APM2_jumper_3.jpg)

你的飛控板可以上場了!