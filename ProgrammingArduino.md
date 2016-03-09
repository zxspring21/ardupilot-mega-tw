## 使用Arduino為ArduPilot Mega編程 ##

(這是通用的APM編程說明，使用簡單的演示程序展示基本操作。在下一步我們將下載並使用完整的APM軟件。)

### Arduino加載代碼說明 ###

打開Arduino，單擊 **File** 菜單, 單擊 **Open** ，導航至你的代碼文件夾，加載你想使用的素描文件（sketchfile），該文件通常與文件夾名稱相同，後綴為`.pde`。這裡，我們打開 `ArduPilotMega_demo.pde` 文件，加載[遙控輸入測試程序](http://www.sparkfun.com/datasheets/DevTools/Arduino/ArduPilotMega_demo.zip):

![http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/demo.png](http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/demo.png)

確保在Arduino的 **Tools** 菜單中，選擇的開發板是 **Arduino Mega (Atmega1280)**.

![http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/board.png](http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/board.png)

在Arduino軟件的 **Tools** 菜單中，確保你選擇了正確的串口(FTDI 傳輸線會新建一個串口). 如果你不確定你的FTDI傳輸線對應的串口號，查看Windows設備管理器（可以在控制面板中找到）。它應改看起來像這樣:

![http://wiki.ardupilot-mega.googlecode.com/git/images/serialport.png](http://wiki.ardupilot-mega.googlecode.com/git/images/serialport.png)

在蘋果電腦中通常只有一個串口 —— 也就是 FTDI 電纜創建的那個。如果你有超過一個序列埠，選擇名稱中有「ftdi」的那個。

上傳軔體時，單擊"Upload to I/O board"按鈕（向右的小箭頭）。在30秒內不會發生任何事，此時代碼正在編譯，然後 ArduPilot 的電源旁的 LED 將熄滅，此時板子正在重啟並下載軔體（如果你用 USB線連接 IMU 板，板上的一個黃色LED在上傳軔體時會快速閃爍）。在一分鐘以內， Arduino程序的底部將報告「Done uploading」，指示軔體已成功上傳。

**注**: 如果你加載上面列出的範例程序，你需要打開Arduino 序列埠終端機(工具欄最右邊按鈕)，將鮑率設為57600來查看輸出。你需要將 RC 遙控接收機連到APM的輸入端上。另外注意某些早期板上的 Atmega 328 晶片(PPM編碼器)的熔絲位設置不正確。如果是那樣的話，你的板子將不能讀取任何通道，並且輸出錯誤的舵機信號。如果存在這種情況，請發回 Sparkfun 進行重新編程，或者根據[這個教程](Encoder.md)自己重燒軔體。

### 調試提示 ###

如果你在上傳過程中遇到問題（看到一串紅色的錯誤信息），參考[這裡](http://diydrones.com/profiles/blogs/arduino-debugging-tips)的調試提示。

記住，觀察Arduino 的序列埠監視器(通常鮑率為38400)總是一個好辦法。監視器是一個無價的調試助手，將告訴你它在幹什麼。

### 其他演示程序 ###

[這裡](http://www.sparkfun.com/datasheets/DevTools/Arduino/ArduPilotMega_dancing.zip)是另一個有趣的程序。如果你的 APM 輸出端已經插入數個伺服機，程序將讓它們跳舞!

<a href='http://www.youtube.com/watch?feature=player_embedded&v=U0Smrhy1xYg' target='_blank'><img src='http://img.youtube.com/vi/U0Smrhy1xYg/0.jpg' width='425' height=344 /></a>