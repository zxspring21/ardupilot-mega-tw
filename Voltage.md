**使用 APM 測量電池電壓和電流**




## APM1: 使用內建的電壓感應器 ##

APM 擴充板包含電壓感應器，以分壓電路的形式連接到處理器的模擬輸入端。你可以在任務規劃器中啟用這個測量器。

要使用它，最簡單的連接電池的方式是用電纜連接到鋰電池的平衡充電口。如果你沒有這樣的電纜，可以在這裡買到：[3S 插件](http://www.rcdude.com/servlet/the-1652/Balance-Lead-Extension-for/Detail)，[4S插件](http://www.rcdude.com/servlet/the-1653/Balance-Lead-Extension-for/Detail)。

如下圖所示，將電纜焊接到 APM 1 IMU 擴充板的相應針腳。引腳標籤在擴充板的底部。黑線應該連接到 GND 引腳，紅線(或離地線最遠的線)應該連接到旁邊的針腳，標記為AN0。我也把 3S 電纜另外兩根電線焊接到爬過便得針腳，但它們沒有做任何事情 —— 只是為了確保牢固地連接電纜。


http://wiki.ardupilot-mega.googlecode.com/git/images/IMG_5340.JPG


您還必須在下面標明的引腳中焊接 3.9K 歐姆電阻(包括在擴充板套件裡)。電阻的方向並不重要。


http://wiki.ardupilot-mega.googlecode.com/git/images/IMG_5342.JPG

### 設置 ###

電池測量的設置在任務規劃器的"配置"選項卡中，如下所示。

你需要一次測量幾個電壓來校準它，。用萬用表測量來自你的 ESC 的 BEC 電路(ESC 連出的三線遙控電纜的紅色和黑色的電線，為 APM 板供電)的電壓，填入「APM的輸入電壓」字樣。然後用萬用表從電池的平衡充電口測量電池的輸出電壓，填入「測量電池電壓」字樣。

「電池電壓(Calc'd)」的數據將在任務規劃器的飛行數據螢幕顯示。

![http://wiki.ardupilot-mega.googlecode.com/git/images/batteryscreen2.png](http://wiki.ardupilot-mega.googlecode.com/git/images/batteryscreen2.png)


---


## 選項2：使用 AttoPilot 感應器測量 APM 1 或 APM 2 的電流和電壓 ##

配置好監視電池電壓和電流後，APM 將提供當前電壓和電流，以及累計消耗的電量(毫安培小時)。這是最精確的測量電池剩餘容量的方法。需要一個外部電流感應器。
![http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/currentsensor.png](http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/currentsensor.png)

外部電流感應器是必需的。默認是 AttoPilot 90A/50V 電壓/電流感應器，它可從 [SparkFun](http://www.sparkfun.com/products/9028) 買到(如上所示)。

該感應器提供了電池電壓和電流的比例輸出。輸出為為 12 位 3.3V ADC 設計，量程為 51.8 伏特，89.4 安培。

### 連接 APM 1 板 ###

如圖所示，連接 AttoPilot 和 APM。使用 AN0 和 AN1 電壓感應器引腳和相鄰的接地引腳。

焊上 3 針頭。從底下數第 4 針是地線(黑色)。下一針是電池的電壓(紅色)。第三針是電池的電流(白色)。

![http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/AttoPilot_current.jpg](http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/AttoPilot_current.jpg)


### 連接 APM 2 板 ###

![http://wiki.ardupilot-mega.googlecode.com/git/images/APM2/Atto_APM2_2.jpg](http://wiki.ardupilot-mega.googlecode.com/git/images/APM2/Atto_APM2_2.jpg)

### 設置 ###

電池測量設置的任務計劃配置「選項卡」。

你需要測量一個電壓來校準它，。用萬用表測量來自你的 ESC 的 BEC 電路(ESC 連出的三線遙控電纜的紅色和黑色的電線，為 APM 板供電)的電壓，填入「APM 的輸入電壓」字段。

「電池電壓(Calc'd)」的數據將在任務規劃器的飛行數據螢幕顯示。

![http://wiki.ardupilot-mega.googlecode.com/git/images/batteryscreen.png](http://wiki.ardupilot-mega.googlecode.com/git/images/batteryscreen.png)


---


## 選項 3: 使用 APM 2.5 的電源模組量測 APM 2.5 上的電流及電壓 ##

APM 2.5 有一個連接頭可以讓你連接電流與電壓監控器，並且也可以供電給 APM。 APM 2.5 電源模組的輸出比例為12位元的 5V ADC，範圍為 50V 90A。板上內建一個 5.3V 及 2.25A 切換開關。請注意電源模組的最大電壓為 18V，這是板子上變壓器的最大允許電壓。

### 與 APM 2.5 連接 ###

![http://wiki.ardupilot-mega.googlecode.com/git/images/3DR-current-sensor-top.jpg](http://wiki.ardupilot-mega.googlecode.com/git/images/3DR-current-sensor-top.jpg)

6線電纜請插到6線連接器即可連接電源模組及 APM。你的電池連接到電源模組的公端並且將它的母端則插到 ESC 或配電板。

**ArduPlane 的使用者請注意:** you must remove the APM's JP1 jumper when using the Power Module so your electronics are only powered from the Power Module's onboard regulator and not from your ESC. By removing the jumper you can use the output rail to distribute power from your ESC or BEC to your servos.

**ArduCopter 的使用者請注意::** you must remove the APM's JP1 jumper when using the Power Module so your electronics are only powered from the Power Module's onboard regulator and not from your ESCs. You can leave the jumper present if you are using "no-BEC" ESCs (the jumper's presence does not matter in this scenario). The two-wire PDB power cable should still be connected to the APM's output pins, as this is the ground connection between the APM and the ESCs.

![http://wiki.ardupilot-mega.googlecode.com/git/images/3DR-current-sensor-APM-conn.jpg](http://wiki.ardupilot-mega.googlecode.com/git/images/3DR-current-sensor-APM-conn.jpg)

### 設置 ###

電池的量測可於 Mission Planner 的 **Configuration** 頁面設置。設定步驟是類似於！AttoPilot 的感應器。

透過選擇就可開啟電壓及電流感應器:

**4: Volts & Current** from the _Monitor_ dropdown,

**4: 3DR IV Sensor** from the _Sensor_ dropdown,

**2: APM2.5 3DR IV** from the _APM Ver_ dropdown.

然後填寫你的電池容量。

俅必需去量測從電源模組上所流到 APM 二極體及保險絲上的電壓及電流，只要量測下圖中保險絲上的焊點就可以很容易的知道。輸入你所量測到的電壓至\*1. APM Input voltage**。**

資料會顯示在\*3. Battery voltage (Calced)**，這個數值就會顯示在你的飛行資料的畫面。**

![http://wiki.ardupilot-mega.googlecode.com/git/images/3DR-current-sensor-planner2.png](http://wiki.ardupilot-mega.googlecode.com/git/images/3DR-current-sensor-planner2.png)

**註:** 如果要關閉電流或電壓監控，你可以到 Advanced Parameters List 將 **BATT\_CURR\_PIN** 或 **BATT\_VOLT\_PIN\*設置為**-1