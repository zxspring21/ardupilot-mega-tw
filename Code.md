## 用 Arduino 下載和使用 APM 程序 ##

首先，如果你還沒有 Arduino，請到[這裡](http://arduino.cc/en/Main/Software)下載。

獲得 Arduino之後，下載[最新的 APM 程序](http://code.google.com/p/ardupilot-mega/downloads/list)。它的名字為 ArduPilotMega(版本號).zip。 **解壓主文件夾到你的桌面上。** 在主文件夾下有兩個文件夾："ArduPilotMega" 和 "libraries"。 將它們拖動到上一步中你定義的Arduino Sketchbook文件夾中。下圖顯示了我的例子 :

![http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/sketchfile.png](http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/sketchfile.png)

這是我放置庫文件和APM代碼的文件夾（高亮顯示）:

![http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/folders.png](http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/folders.png)

我們建議你就用這個文件設置。如果你修改了， Arduino可能不知道如何找到庫文件，然後就出現編譯錯誤。

**重要事項:不要將整個 APM (版本)文件夾拖動到你的素描目錄中。如果你這樣做，代碼將不能編譯。** 只應該將它內部的兩個獨立的文件夾--ArduPilotMega 和 libraries--拖動到上圖所示的目錄中。在將它們放置到素描文件目錄中之後，你就可以刪除桌面上的APM(版本)目錄了。

現在打開Arduino IDE，單擊 **File** 菜單，單擊 **open** ，找到 ArduPilotMega 目錄，單擊 "ArduPilotMega.pde"。這將打開目錄中的所有文件，並在開發環境中以標籤頁的形式顯示出來。

**重要: 代碼預設為 APM 1。如果你是使用 APM 2，你必須加入這行程式到 APM\_Config.h 的檔案:**

`# define CONFIG_APM_HARDWARE APM_HARDWARE_APM2`

現在你應該可以編譯代碼並上傳到APM板中。確保USB或FTDI電纜連上了IMU板/APM板，並且在 Tools 菜單裡選擇了正確的開發板。如果你的板子用的是 ATMega1280 處理器 （APM 板上的一個大芯片，寫了 "Atmega1280"），那麼選擇 "Arduino Mega (Atmega1280)"。如果你用的是 ATMega2560 芯片，則選擇 "Arduino Mega 2560"。確保你選擇了分配給你板子的正確的COM端口（可以在Windows 設備管理器裡查看），單擊上傳按鈕。

編譯代碼需要一到兩分鐘，之後Arduino將在底部的狀態窗口中報告"Binary sketch size: XXX bytes (of a 126976 byte maximum)"。然後它將開始向APM上傳編譯好的固件。在此期間IMU板上的 RX和 TX 燈將快速閃爍（顯示數據正在傳輸）。約一分鐘後，LED將熄滅，Arduino IDE將報告固件已上傳完畢。此時你的APM板已經編程完畢。

## 疑難解答 ##

![http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/error.png](http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/error.png)

如果你遇到了問題，或者 Arduino 顯示如上的錯誤，按 [這裡](http://diydrones.com/profiles/blogs/arduino-debugging-tips)的提示逐條調試。