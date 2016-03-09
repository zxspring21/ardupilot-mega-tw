== 使用 Xbee 做為 APM 2 的遙測模組 ==

![http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/KT-Telemetry-Xbee-2new.jpg](http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/KT-Telemetry-Xbee-2new.jpg)


## 安裝 Xbee 遙測模組 ##

加入無線遙測模組不會很困難，可以大大地擴展您的無人機能力，我們建議使用[900Mhz Xbees](https://www.sparkfun.com/categories/222)下圖所示，這個模組的通訊距離超過 1 mile(約1.6KM)。如果你在歐洲900Mhz未被核准使用，你可以使用2.4Ghz Xbee kit，說明請見[這裡](http://diydrones.com/profiles/blogs/uk-eu-2-4-ghz-telemetry-kit)。

_**重要事項**: 在 APM2 上，**當你的 APM 板已經連接在電腦的 USB 時就不可使用 Xbee。**因為有些電腦系統會自動判斷 USB 插入的裝置所以 Xbee 有可能會和USB共用同一個序列埠。雖然 Winodws 系統會空出某些序列埠給其他裝置使用(want to [connect an Android phone](https://store.diydrones.com/PhoneDrone_Board_p/br-phonedrone.htm), anyone?), 它的意思是說當你測試無線遙測模組時必須將你的飛控板與USB線斷開並且使用其他的方式取得電源。_

## 開始接線吧 ##

### APM 2.0 ###

![http://wiki.ardupilot-mega.googlecode.com/git/images/APM2/telemtry.jpg](http://wiki.ardupilot-mega.googlecode.com/git/images/APM2/telemtry.jpg)

![http://wiki.ardupilot-mega.googlecode.com/git/images/IMG_5385_2.jpg](http://wiki.ardupilot-mega.googlecode.com/git/images/IMG_5385_2.jpg)

將XtremeBee轉接卡(插上Xbee)連接至APM 2，如圖所示。轉接卡應該處於「Master」 模式("Master"及"Slave"只是相反的 TX 與 RX pin)。

我們建議使用[DIY Drones four-wire Xbee cable](http://store.diydrones.com/Xbee_Oil_Pan_connector_cable_p/kt-telemetry-cable.htm)，這是標準的無線遙測模組，它是專門設計給XtreamBee轉接卡與APM的連接，提供一個方便又安全的連方式。


### APM 2.5 ###

在 APM 2.5，請使用專用的遙測埠及電纜，如下圖所示:

http://wiki.ardupilot-mega.googlecode.com/git/images/IMG_5419.JPG

## 地面端 ##

如果你使用標準的USB轉接卡，就可以很容易將USB與晶片連接起來，如下圖：

http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/IMG_4887.JPG

如果你的地面端是使用XtreamBee轉接卡，就可以藉由FTDI的USB線連接至你的 USB 埠，轉接卡應該也是Master模式，如下圖：

![http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/XtreemBee.png](http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/XtreemBee.png)


到這邊就已經完成了!記得選擇正確的Xbee port(你可以在Windows的控制台看到Xbee)，Mission Planner的鮑率請設定57K，其他GCS的連接也是如此。

![http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/xbeebaud.png](http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/xbeebaud.png)


---


### (選擇性設定) 將遙測模組改為使用 UART2 (又稱 Serial3) ###

Xbee 與 APM2 的預設連接是使用 UART0 (在 Arduino 又稱 "Serial")，它是與 USB 共享的通訊方式。如果你希望遙測模組替代成 UART2，你可以修改"AutoMUX UART0" APM2 板子下方的一組跳線。

雖然很難看到，在預設的情況下，會有兩個小跳線在焊點之間，必須用刀片剪斷。然後焊上一個新的焊點，必要確實焊接這兩個焊點。

![http://wiki.ardupilot-mega.googlecode.com/git/images/APM2/BOTTOM_AutoMUX_UART02_small.png](http://wiki.ardupilot-mega.googlecode.com/git/images/APM2/BOTTOM_AutoMUX_UART02_small.png)


---


### (選擇性設定) 開始設定你 Xbee 遙測模組 ###

如果你想的話你可以使用自己的遙測套件，要記住的第一件事就是你的 XBee 模組應該與RC設備在不同的頻率範圍。

一般來說我們建議使用 900Mhz Xbee 模組，但在某些國家900Mhz是不被允許的(包括台灣)，在這些地方你可以使用 2.4Ghz Xbee 模組，設定上我們使用[Xbee Pro wireless 模組](http://www.sparkfun.com/commerce/product_info.php?products_id=8742)，設定有些小技巧，所以請參閱下面的評論，本手冊中看到別人怎麼做，特別是，我們不建議使用 DIY Drones！XtreamBee 的轉接卡，相對的你也可以試著使用[Adafruit](http://www.adafruit.com/index.php?main_page=index&cPath=29&zenid=33b27de3af208ec86b4519c07cd479f3)或[Sparkfun](http://www.sparkfun.com/categories/111)的轉接卡，請注意，DIY Drones 無人機團隊將僅支援並建議使用900MHZ的XBee模組，所以如果你使用其他的通訊模組請尋求其他的社群幫忙，而非DIY Drones的開發團隊。

[這裡](http://diydrones.com/profiles/blog/show?id=705844%3ABlogPost%3A56130)有更多關於如何設置最佳頻率的討論。

所有的 Xbee 模組在APM上皆需要使用轉接卡才可運作，你有兩個選擇：

  * 一個是 DIY Drones [XtreamBee adapters](http://store.diydrones.com/product_p/br-0015-01.htmXtreemBee)在飛行器端，及[USB adapter board](https://store.diydrones.com/product_p/br-0015-02.htm)使用USB線連接在地面/筆記型電腦端。
  * 如果你已經有 [FTDI cable](http://store.diydrones.com/FTDI_Cable_3_3V_p/ttl-232r-3v3.htm)，可以在 DIY Drones 取得兩個 [XtreamBee adapters](http://store.diydrones.com/product_p/br-0015-01.htmXtreemBee)。


## 設定 Xbee 模組 ##

如果你有DIY Drones的遙測套件，你的 Xbee 模組就已經直接使用，但如果你設定你自己的模組，請看下列說明：

Xbee 模組預設鮑率為 9600 bps，你必須修改成APM合適的序列埠鮑率 57600 bps；請將你的 Xbee 模組改成這個鮑率。(如果你想要使用不同的鮑率，你可以修改APM\_Config.h 指令如下`#define SERIAL3_BAUD  [whatever baud rate you want]`)

每一片都要使用 USB 配接器，透過 USB 線連接至你的電腦，並且使用[Digi's X-CTU utility](http://www.digi.com/support/productdetl.jsp?pid=3352&osvid=57&s=316&tp=5&tp2=0)(Mac/Linux 的使用者請見由 motosenso 製作的替代工具)來選擇正確的序列埠與其通訊。記得將新的 Xbee 模組初始設定為 9600 bps，在變更完鮑率後也一併變更相對應設備的鮑率，你也要給模組一個獨立的網路ID(VIDs)這樣他們就可以被配對。只要使用任何3位數，然後請確認你的模組的號碼都是相同的。(備註：如果你飛行的附近有其他的無人機請確認你的網路 ID 是獨立的，沒有被其他人使用)。

當你在X-CTU的數據設定頁面點擊「Read」畫面會和下圖一樣。(在這個範列我們使用的 VID 是999，我已經有將正確的鮑率顯示出來)：

http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/Xbeescreenshot.PNG

註：如果你從 Sparkfun 購買 Xbee 模組而非DIY Drones，請注意他們有時會附帶錯的 firmware，X-CTU也許會試著下載新的程式，有可能會失敗(取消它)。如果你的 Xbee 模組回報是XBP09-DM(而不是正確的XBP09-DP)，請依照下列作法：

  1. 如果你有 XBP09-DP 模組，你必須下載 XBP09-DP 的 firmware。如果你已經下載 XBP09-DM 的 firmware，它也會運作，但在PID-config的設定畫面會失敗。
  1. 當你接上 XBP09-DM 模組時 X-CTU 會回報，略過它。到 Modem Configuration 的頁面並照下列方法設定：
    1. Modem 選擇 XBP09-DP，Function 設定 XBEE-PRO 900，版本 1002 ，選擇版本 1002 是很重要的，如果選擇 1061 則會無法運作。
    1. 在參數設定的畫面點擊「Show Defaults」按鈕。
    1. 在「Modem Parameters and Firmware」的頁面點擊「Write」 按鈕
    1. 回到電腦設定，鮑率改為 9600 按下「Query」，就會顯示 XBP09-DM，請略過。
    1. 回到「Modem Configuration」按下「Read」，modem 應該會顯示 XBP09-DP，版本為 1002。
    1. 選擇版序 1061。
    1. 點擊「Show Defaults」。
    1. 點擊 DD 參數並設定為 0 ，這個步驟也很重要，否則 1161 的 firmware 會下載失敗。
    1. 點擊「Write」，現在你的 XBP09-DP firmware 版本就是 1161。
  1. 變更你的鮑率及 Modem VID，重新載入後就可以正常運作了。

電腦上的設定依然顯示 XBP09-DM ，但你不用擔心。

## 給非 PC 的使用者 ##

MacOS、Linux 或 Windows 的使用者 - 有一個免費的跨平台軟體可以替代 X-CTU，叫做 moltosenso Network Manager。請在[這裡](http://www.moltosenso.com/#/pc==/client/fe/download.php)下載軟體。moltosenso 團隊與我們合作為 ARDUPILOT 寫了一個有關 Xbee 無線模組設置的[特別教程](http://forum.moltosenso.com/viewtopic.php?f=16&t=8)，ARDUCOPTER 的遙測模組也是使用他們的軟體。

## 連接測試 ##

如果你已經在筆記型電腦開啟終端機(也可以開啟 Arduino 介面的 serial monitor)，選擇正確的序列埠，不管你上面是選擇哪種 XBee 模組請設定鮑率(預設為 57600)，一旦完成設定你應該會看到 APM 遙測模組。畫面會一直出現「Serial3.println」並且資料會透過 Xbee 送到地面端，你可以從地面端記錄你所選擇的資料及數據記錄。你也可以開啟地面端軟體設定正確的通訊埠及鮑率，就會開始顯示 APM 的資料。

另外，如果你想測試 Xbee 連接的區間，請同時接上飛行器端 Xbee 模組的 RX、TX Pin 並使用 X-CTU 的區間測試功能，我們使用的模組大約有1英哩的距離。

**註**：如果你的APM已經裝上 Xbee，USB線的電力有可能會不足以驅動它們，請把ESC及鋰電池接上 RC pins 來提供額外的電力。(如果紅色的C LED已經閃爍及變暗或者APM板間歇性運作就是告訴你已經電力不足)

## 測試程式碼 ##

ArduPilot Mega 有四個序列埠所以一般常見的 Arduino 序列命令會要你指定讀取或寫入哪一個埠。例如：Serial1.print(), Serial2.print(). 通訊埠會連接到 USB/FDTI 連接器的是Serial0，通訊埠會連接到 Telecom pins is Serial3

[這裡](http://code.google.com/p/ardupilot-mega/downloads/detail?name=MultiSerialMega.zip&can=2&q=)有一個列出四個序列埠的快速範例，所以你可以檢查你的 Xbee 連接器是否運作，這裡有介紹如何使用它：

**1)** 把 Xbee 模組插入 USB 埠， APM 插入另一個 USB，使用 Arduino 載入範例程式，然後將一個序列埠設定 APM，開啟「serial monitor」設定鮑率為 115200，你就會看到畫面一直重復「port 0」，這是從APM的USB送出的輸出的訊號：

![http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/xbeetest2.png](http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/xbeetest2.png)


**2)** 現在把序列埠換到你指定的 Xbee 重開「serial monitor」，設定鮑率為 57600 (這個鮑率是你之前寫入的)，你現在應該看到畫面一直重復「port 3」，這是從APM的Xbee送出的訊號：

![http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/xbeetest1.png](http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/xbeetest1.png)

## Unbricking an Xbee ##

重要備註：有時 XBee模組會被雜散信號損壞。如果你發現有停止運作的狀況(Adafruit轉接卡的綠色LED不亮)，刷新 firmware 的方法如下

使用 Sparkfun USB 轉接卡：

  1. 將 Xbee 模組由轉接卡上取下。
  1. 轉接卡接到電腦。
  1. 開啟 X-CTU 確認鮑率為 9600
  1. 開啟「Modem Configuration」
  1. 核取「Always update firmwar」
  1. 下拉選單選擇「proper modem」(900Mhz 建議選擇「XBP09-DP」；2.4GHZ Xeebee Pro 2 建議選擇「XBP24-B」)
  1. 點擊「Write」按鈕，幾秒後試著讀取modem，你會得到一個訊息視窗，指出需要採取行動。這邊你要小心的將模組插到轉接卡上，幾秒後就會觸發firmware重新載入。
  1. 你也許會再一次短暫地出現訊息視窗，如果出現了請再重覆前一個步驟應該就可以運作了。
  1. 這個會讓模組鮑率回到 9600，透過 X-CTU 來設定並測試，它應該會回報已經確認。
  1. 一旦你已經確認它可以正常運作，就會讓你確認重置的鮑率(APM的標準是57K)。

_(Thanks to Doug Barnett for these tips)_