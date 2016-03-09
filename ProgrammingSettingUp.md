## 設置 ArduPilot Mega 編程環境 ##

### 設置 Arduino 編輯軟體 ###

首先，下載及安裝最新版本的 Arduino，你可以在我們的[下載頁面](http://code.google.com/p/ardupilot-mega/downloads/list)找到(Ardupilot 的 Arduino 程式庫在每次建立中都是最大的 -- 我們打破了標準編譯器的記錄!)。他們稱作"Arduino (version) relaxpatch"(版本號碼不重要)，有 Windows 版本及 Mac 版本)。

If you've never used Arduino before, please use [these setup instructions](http://arduino.cc/en/Guide/HomePage) to become familiar with Arduino basics.


### 設置 Sketchbook 資料夾 ###

最後，你必須定義 Ardunio 放置「素描（Sketch）」(指組成一個程序的文件集合)和庫文件的文件夾。

在某個地方建立一個文件夾，可能在「我的文檔」中或桌面上(如果你用過Arduino，你可能已經設好了)。打開Arduino集成開發環境，打開\*Preferences**對話框。將Sketchbook location設到你新建或正在使用的`Sketchbook`文件夾。這是我的設置:**

![http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/sketchfile.png](http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/sketchfile.png)

修改了目錄設置之後，必須關閉Arduino並重新打開，才能識別新的設置。


### 安裝驅動軟體 ###

首先，下載及安裝 Arduino，你可以到[這裡下載](http://arduino.cc/en/Main/Software)。如果你之前從未使用過 Arduino，請閱讀[這些設置介紹](http://arduino.cc/en/Guide/HomePage)來熟悉 Arduino 的基礎功能。

然後，安裝 APM 的USB驅動。多數人使用常規的 USB-A 轉 microB 傳輸線 (一頭是普通 USB 接口，另一頭是 micro USB 接口)，並通過IMU板連接APM。但是如果你不用IMU板，也可以用一條FTDI傳輸線。下圖顯示了如何連接這些傳輸線。

當你第一次將APM或FTDI線連到電腦上時，Windows 7將識別出FTDI USB轉串口芯片並安裝正確的驅動。但如果沒有識別出來，或者你使用老版本的Windows，你可以從[這裡](http://www.ftdichip.com/Drivers/VCP.htm)下載相應驅動然後再安裝。安裝完之後，重啟電腦，再插入連接線，在Windows設備管理器（在控制面板中）中將顯示這個設備，如下圖所示（你的COM端口可能不同；它是由Windows根據你連接過多少其他設備自動指派的）。這就是你將在Arduino和所有與APM的USB交互中使用的端口號。

註：如果你使用FTDI連接線，你必須在控制面板/設備管理器中修改FTDI/USB線的COM端口。找到如圖中所示的USB-串口（你的端口可能不是3，不過沒關係），在屬性/端口設置/高級中，確保選中"Set RTS On Close"。該設置只需要修改一次。

![http://wiki.ardupilot-mega.googlecode.com/git/images/eighteen.jpg](http://wiki.ardupilot-mega.googlecode.com/git/images/eighteen.jpg)
