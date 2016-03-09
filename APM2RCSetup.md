===首次的APM設定===

我們建議你使用Mission Planner做為首次設定APM的軟體。(軟體為Windows平台但Mac系統可於VM中使用，Linux也可以在Mono下執行。如果你不想使用這套軟體，也可以使用不分作業系統的[CLI模式](http://code.google.com/p/ardupilot-mega/wiki/CLI)

下載完韌體之後，請確認已選擇正確的的序列埠及鮑率(115K)，請點擊右上角的 Connect。Mission Planner 將透過 MAVLink 連接 APM。

(如果是你第一次使用 APM，程式碼在一開始時會自動格式化你的記憶卡，這可能會干擾與 MAVLink 的連接，並且會回報連接失敗。如果真的發生了這種狀況，請等幾分鐘後再重新設定。)

現在你可以按下紅色圈起來的「setup」按鈕：

![http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/mavsetup.png](http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/mavsetup.png)

這個動作會帶你到 configuration 畫面。


---


### 設定步驟 ###

1) **如果你是使用標準的機身，請下載已經預先做好的設置檔案**

一般的機身如 Bixler、Skyfun 及 Skywalker，我們已經有提供設置的檔案，而這些檔案都已針對這些飛機進行調整。你可以到[這裡](http://code.google.com/p/ardupilot-mega/wiki/ConfigFiles)下載並使用 Mission Planner 上傳至 APM。你仍然需要依據你的硬體來設置它們，所以不管如何，請繼續接下來的設置步驟。

2)**校驗RC輸入端**

![http://wiki.ardupilot-mega.googlecode.com/git/images/instructional/radio_setup.png](http://wiki.ardupilot-mega.googlecode.com/git/images/instructional/radio_setup.png)

你的發射器必須打開。理想的情況下，你已經調整好手動的 RC 模組和所有必要的調整值，所以這些 RC 的輸出端會反應出這些微調的結果。如果你依指示還無法調整你飛機的 RC 模式，在你的飛機出動後你也許需要重新校驗你的 RC(在戶外你可以很容易的作到)。

每個通道分配如上所示。當移動RC遙桿時，相關的Bar就會移動，按下「Calibrate Radio」設定無線電的極限值，你已經連接的每個通道皆需設定，當超出極限值會出現紅色的Bar。

在這個畫面如果有必要你也可以設定相關的伺服機及所需的elevon mode。

按下儲存即可完成。

http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/MPradio.PNG

2)**設定飛行模式**

當飛機飛在空中可以使用RC發射器上的撥動開關切換APM的飛行模式，在這裡有祥細的模式說明，(如果想在發射器上改變3個模式以上請參考[這裡](http://code.google.com/p/ardupilot-mega/wiki/Sixmodes))，當你撥動開關時會發現異動處會有綠色的亮光，可以使用下拉選單去設定各種模式。請注意不可手動變更 Flight Mode 6，這是一個「hardware manual」，意思是說它是被APM的failsafe迴路所控制並且可以回復至RC控制的安全措施。

![http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/mpmodes.png](http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/mpmodes.png)

3)**設定硬體**

在這個頁面可以設定你的APM上有連接什麼配件，只要點擊各個感應器的核取方塊就可以使用(目前APM尚不支援聲納測距儀，主要用於ArduCopter)

![http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/mphardware.png](http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/mphardware.png)

你一旦開啟磁力儀(電子羅盤)的功能，你就要去設定磁偏角的校驗項目：

  1. 你可以什麼也不做，程式碼會試著找出所有的偏移，透過飛行時的 GPS 及 IMU 即時的讀值來比對磁偏角與電子羅盤。優點: 使用者什麼事也不用做。 缺點: 在飛行時會花些時間來取得正確的磁偏角，所以電子羅盤在第一次使用時會不準確。
  1. 在 Mission Planner 內手動校驗(方法如下)。你可以輸入下面說明的磁偏角，然後按下 "Live Calibration" 按鈕，當它開始記錄資料並且計算校驗感應器時請移動你的飛機約 30 秒。優點：它是有用的。缺點：會有點尷尬，尤其是大型飛機。它無法反應馬達飛行時所產生的磁場干擾。
  1. 重播飛行日誌檔。這是一個最好的選項，如之前所說的使用日誌檔校驗，你只要重播之前飛行的記錄(.tlog)程式就會與 GPS 及 IMU 的讀值比對，但必須將電子羅盤接上。優點：它運作的非常好。缺點：你必須已經飛行過，下載的 .tlog 檔案可能在你沒有實際飛行時會擾亂你的校驗，將會須要再飛行一次或者冒著較差的飛行效率的風險。


手動輸入你的地理位置磁偏角，打開一個網頁瀏覽器，點擊鏈接，你就可以找到正確的數值。輸入你的位置，它會給你一個磁偏角，如下面圈起來的地方：

![http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/declination.png](http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/declination.png)

以我目前的位置為例目前的磁力線就是「14.13」(軟體會由十進制轉單位為度/分)。

4)**如果你是使用標準的機體結構，直接載入設定檔即可**

一般的機身如Bixler、Skyfun及Skywalker我們已經有支援的設定檔，你可以在[這裡](http://code.google.com/p/ardupilot-mega/wiki/ConfigFiles)下載並使用Mission Planner寫至APM。

5)現在如果你切換到Flight Data頁面連結MAVLink，你會發現當板子移動時顯示器上的水平線也移動，當你已經切換到這個頁面記住移開板子時需先靜止15-20秒，IMU必須先行校驗。一旦完成HUD就會開始移動。

http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/Missionplanner1.PNG