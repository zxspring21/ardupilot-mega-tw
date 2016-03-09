![http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/KT-Telemetry-Xbee-2.jpg](http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/KT-Telemetry-Xbee-2.jpg)


## 連接 Xbee 無線模塊 ##

安裝無線遙測並不困難，並且它能極大地增強UAV的能力。我們推薦[900Mhz APM 無線套件](http://store.diydrones.com/Xbee_Telemetry_kit_p/kt-telemetry-xbee.htm)它的控制距離能超過1英里。如果你在歐洲，不允許 900Mhz 的話，你可以使用 2.4Ghz Xbee 套件。
它的說明在[http://diydrones.com/profiles/blogs/uk-eu-2-4-ghz-telemetry-kit這裡。

## 連接空中的 Xbee 和 APM ##

**向前的插針:**

如果你想將 Xbee 模塊安在飛機前方，你可能希望插頭指向前方。在此情況下，將4個分離的插針焊到 IMU 板的 "TelemPort" 端口上，如圖所示:

http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/IMG_4847.JPG

現在將黑色的塑料基座從插針上剝離出來(可能有點緊，但搖晃鉗子可以辦到），並彎曲90度，如圖所示: （譯注: 直接用彎針就行了）

http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/IMG_4848.JPG

**向下的插針:**

如果你打算將 Xbee 安在 APM 後方，你可能希望插頭指向下方，這也不會太佔地方。該情況下，將它們焊到板子底部。

這是 EasyStar 上的一個例子:

http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/IMG_4879.JPG

現在APM 和 一個 Xbee 無線遙測模塊在飛機上安好了:

http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/IMG_4880.JPG

## 線路連接 ##

將 XtremeBee 適配器(其上插著 Xbee 模塊) 與 IMU 板通過四根杜邦線相連，如圖所示。適配器應當處於 "Master" 模式. ("Master" 和 "Slave" 就是交換 TX 和 RX 線).

http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/IMG_4841.JPG

你也可以用一個兩端都是母頭的舵機線連接其中3個插針，連線可以稍微乾淨一點。如圖所示:

http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/IMG_4884.JPG


## 地面端 ##

如果你使用官方 DIY Drones 套件裡的 USB 適配器, 只要簡單地用USB線連接，如圖所示:

http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/IMG_4887.JPG

如果你在地面端使用 XtreamBee 適配器，將其連接到一條 FTDI 傳輸線，並插到USB扣上，如圖所示。適配器同樣應該處於 Master 模式.

![http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/XtreemBee.png](http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/XtreemBee.png)

現在完成了！記住在任務規劃器或其他地面站程序裡選擇正確的 Xbee 端口 (你可以在 Windows 控制面板的設備管理器裡查看 Xbee 分配了哪個端口）和 57.6k 波特率

![http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/xbeebaud.png](http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/xbeebaud.png)

---


## （可選）設置你自己的 Xbee 遙測 ##

你也可以打造你自己的遙測套件。首先要記住的是你的 Xbee 模塊應該和遙控發射器的頻段不同。

在一般情況下，我們建議900MHz的XBee模塊。但在一些國家 900MHZ 沒獲批准。在這種情況下，你可以使用2.4GHz XBee 模塊。在該配置中，我們使用這些 [XBee Pro 無線模塊](http://www.sparkfun.com/commerce/product_info.php?products_id=8742)。安裝可有點棘手，所以請看本手冊下面的評論，看看到其他人如何完成。特別地，我們不建議在這些模塊上使用 DIY Drones XtreamBee 適配器。相反，嘗試[Adafruit](http://www.adafruit.com/index.php?main_page=index&cPath=29&zenid=33b27de3af208ec86b4519c07cd479f3) 或 [Sparkfun 適配器](http://www.sparkfun.com/categories/111)。請注意，DIY Drones 團隊將只支持 900MHZ 的 XBee 模塊，所以如果你使用別的東西，請在論壇尋求幫助，而不是向DIY Drones開發者的尋求幫助。

[這裡](http://diydrones.com/profiles/blog/show?id=705844%3ABlogPost%3A56130)是更多如何挑選最佳頻率更多討論。

所有的 Xbee 模塊都需要使用適配器與 APM 相連。可有如下兩種選擇:

  * 飛機上用一個 DIY Drones [XtreamBee 適配器](http://store.diydrones.com/product_p/br-0015-01.htmXtreemBee), 地面/電腦上用 [Sparkfun USB 適配器](http://www.sparkfun.com/commerce/product_info.php?products_id=8687)。
  * 如果你有 [FTDI 傳輸線](http://store.diydrones.com/FTDI_Cable_3_3V_p/ttl-232r-3v3.htm), 買兩個 DIY Drones [XtreamBee 適配器](http://store.diydrones.com/product_p/br-0015-01.htmXtreemBee).

## 設置 XBee 模塊 ##

如果你有 DIY Drones 的遙測套件，你的 XBee 模塊已經設置好可以直接使用。但是，如果你設置自己的，下面是一些指示：

XBee 模塊發貨時默認為 9600bps，你必須改變你的 XBee 模塊的設置以配合APM的串行速度 57600 bps。 （如果你想使用一個不同的速度，你可以通過在APM\_Config.h文件中輸入`＃define SERIAL3_BAUD [你想要的波特率]`來改變。）

將每個模塊連接 Sparkfun USB 適配器板上，插到 PC 上，並使用[Digi 的 X-CTU 實用程序](http://www.digi.com/support/productdetl.jsp?pid=3352&osvid=57&s=316&tp=5&tp2=0)選擇正確的串行端口，並與它們通信。記住開始時設置程序為 9600bps 來連接新的 XBee 模塊，在你改變的速度後，相應地改變程序的串口速度。你還應該給模塊指定一個唯一的網絡標識符（VIDS）來將他們配對。只需使用任何3位數，並確保兩個模塊的 VIDs 相同。 （註：如果你將在其他無人機的附近飛行，檢查網絡ID是唯一的，並且沒有被附近的其他人使用。）

下面是當你在 X-CTU 中的調製解調器配置選項卡中點擊「讀取」時的樣子（例子中我們使用的VID 是 999）：

![http://wiki.ardupilot-mega.googlecode.com/git/images/xbee.png](http://wiki.ardupilot-mega.googlecode.com/git/images/xbee.png)

注意：如果你從 Sparkfun 買的 XBee 模塊，而不是官方的 DIY Drones 套件，請注意他們有時附帶了錯誤的固件。 X-CTU 可能會嘗試下載新的代碼，這可能會失敗（取消它）。如果你的 XBee 模塊報告為 XBP09-DM（而不是正確的XBP09-DP），執行下列操作：

  1. 如果你有 XBP09-DP 模塊，您必須下載 XBP09-DP 的固件。如果您已經下載 XBP09-DM 固件，它將部分工作，但在PID配置屏幕會失敗。
  1. X-CTU 將報告模塊為 XBP09-DM。忽略它。轉到 Modem Configuration 選項卡，執行以下步驟：
    1. 選擇調製解調器為 XBP09-DP，Function Set XBee-PRO 900，版本1002。選擇 1002 非常重要。版本 1161 開始時不起作用。
    1. 點擊 Parameter View 下的 Show Defaults 按鈕。
    1. 在「Modem Parameters and Firmware」中點擊 Write 按鈕。
    1. 返回到 PC Settings，改變波特率為 9600。單擊 Query。它會顯示 XBP09-DM。忽略它。
    1. 返回到 Modem Configuration。點擊 Read。它應該顯示調製解調器為 XBP09-DP，版本 1002。
    1. 現在選擇版本 1161。
    1. 點擊「Show Defaults」
    1. 點擊 DD 參數，並將其設置為0。這一步很重要，否則 1161 固件下載將失敗。
    1. 點擊「Write」。您現在的固件是 XBP09-DP 版本 1161。
    1. 現在改變波特率和調製解調器的VID，重新下載，應該可以工作了。

在PC Setting上的查詢中仍然會顯示 XB​​P09-DM。不要擔心。

**注意！** 如果你的 1161 固件有問題，可以安全地使用 1002 固件，它已證明在所有的XBee PRO上工作良好


## 連接測試 ##

如果你在電腦上打開一個終端程序（也可以使用Arduino IDE 的串口監視器)，選擇正確的串口，波特率設置為剛才 Xbee 模塊的波特率 (默認為 57600)。之後，你可以看見 APM 的遙測數據。代碼中有 "Serial3.println" 的時候, 都將通過 Xbees 向地面發送數據。你可以記錄任何想要的數據。你也可以打開地面控制軟件（設置正確的串口和波特率），它將開始顯示 APM 的數據。

此外，如果你想測試 Xbee 連接的距離，將飛機上的 Xbee 模塊的 RX 和 TX 腳相連，然後執行 X-CTU 程序的距離測試功能。我們使用的模塊距離應該在一英里左右。

## 測試代碼 ##

ArduPilot Mega有四個串口，因此普通的 Arduino 串口命令需要一個標識符來指示你想讀寫哪個串口。例如: Serial1.print(), Serial2.print()。 連接到 USB/FDTI 的串口為 Serial0. 連接到無線模塊的串口為 Serial3.

[這](http://diydrones.com/forum/attachment/download?id=705844%3AUploadedFi58%3A181838)是一個簡單的演示程序，將向所有四個串口打印數據，以便檢查 Xbee 連接是否工作。下面是使用說明:

**1)** 將 Xbee 插到一個 USB 端口，APM 插到另外一個端口。使用 Arduino 加載演示程序, 然後在 Arduino IDE 中將串口設置為連接到 APM 板 的串口。然後打開串口監視器，設置波特率為38400。你應當看見重複的 "Port 0"，如圖所示，顯示 APM 的 USB 端口發送的數據:

![http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/xbeetest2.png](http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/xbeetest2.png)


**2)** 現在將串口切換到連接到 Xbee 的串口，重新打開串口監視器。你應當看到重複的"Port 3", 顯示 APM's 的 Xbee 端口發送的數據:

![http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/xbeetest1.png](http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/xbeetest1.png)

## Xbee 變磚後的修理 ##

**重要事項**: 有時 Xbee 模塊可能因為欺騙信號而損壞。如果你發現你的模塊停止工作(Adafruit 適配器上的綠燈不亮), 下面是重新加載固件的說明:

使用 Sparkfun USB explorer 板:

  1. 將模塊從接口板上拆下
  1. 將接口板連接到電腦
  1. 打開 X-CTU，波特率設為 9600
  1. 切換到 "Modem Configuration"
  1. 選上 "Always update firmware" 復選框
  1. 從下拉菜單中選擇合適的 modem (900Mhz 的 Xbee 推薦選擇 "XBP09-DP"; 2.4GHZ Xeebee Pro 2 選擇 "XBP24-B")
  1. 從下拉菜單選擇合適的功能集和固件版本 ("ZNET 2.5 ROUTER/END DEVICE AT" and "1247" (目前))
  1. 單機 "Write" 按鈕。嘗試讀取model數秒之後，會顯示一個提示框，說需要操作。在這時，**小心地\*將模塊插到接口板上。數秒之後，應該觸發重新加載固件。
  1. 一會兒之後可能出現同樣的提示框。如果出現，使用接口板上的重置按鈕。如果板子沒有重置按鈕，將重置插針接地。
  1. 確認正常工作後，重新設置波特率和 ID，與另一個模塊相匹配**

_(Thanks to Doug Barnett for these tips)_