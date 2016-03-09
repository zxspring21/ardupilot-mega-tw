## 首次 APM 設置 ##

我們建議你在首次設置 APM 時用任務規劃器。 （它專為 Windows 實際，但在 Mac 上可以用虛擬機運行，在 Linux 下可以基於 Mono 運行。或者，如果你不想使用這些，你可以使用[CLI 模式](http://code.google.com/p/ardupilot-mega/wiki/CLI)，這在任何操作系統上都能工作。）

下載完韌體之後，請確認已選擇正確的的序列埠及鮑率(115K)，請點擊右上角的 Connect。Mission Planner 將透過 MAVLink 連接 APM。

現在你可以按下紅色圈起來的「setup」按鈕：

![http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/mavsetup.png](http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/mavsetup.png)

這將打開一個對話框，指導你進行基本設置，如下所述。

注意: 你\*必須\*把一個電調或其他 5V 電源插到 APM 的 RC 引腳上，給接收機供電。 USB 電源不會給 接收機供電。如果你沒有單獨為 RC 系統供電，APM 就不能收到任何遙控信號。


---


### 設置步驟 ###


1) **校準遙控輸入**

![http://wiki.ardupilot-mega.googlecode.com/git/images/instructional/radio_setup.png](http://wiki.ardupilot-mega.googlecode.com/git/images/instructional/radio_setup.png)

你必須（用ESC或5V電源）給APM的RC引腳供電，發射機必須打開。理想的情況下，你已經調整好手動的 RC 模組和所有必要的調整值，所以這些 RC 的輸出端會反應出這些微調的結果。如果你依指示還無法調整你飛機的 RC 模式，在你的飛機出動後你也許需要重新校驗你的 RC(在戶外你可以很容易的作到)。


信道分配如上所示。當你移動的RC搖桿，相應的進度條會移動。點擊「校準遙控」，設置遙控的極限。會出現紅色的條，你應該把他們移動到你所連接的每個的通道的極限位置。當你完成時按保存按鈕。

如果有必要的話在這個畫面你也可以反轉你的伺服機及設置 elevon 模式。

設置完成後請按下 done

http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/MPradio.PNG

2) **設置飛行模式**

你可以在空中用RC發射器的切換開關選擇不同的飛行模式。開關通道應該連接到 APM 輸入8。可用的模式的全部細節在[這裡](FlightModes.md)。 （如果你想從你的發射機選擇以上三種模式，相關指導在[這裡](Sixmodes.md)）當你移動切換開關，你會看到綠色高亮變化到不同的行。你可以用每一行的下拉菜單分配模式。請注意，飛行模式6無法手動改變。它是「硬件手動」，即由APM板故障保護電路控制，作為安全措施控制，保證總是能夠切回到RC控制。

![http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/mpmodes.png](http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/mpmodes.png)

3) **配置硬體**

在此標籤中，你可以告訴 APM 你連接了什麼可選的傳感器。在你使用的傳感器上點擊復選框。(APM 目前不支持聲納，它的主要用在 ArduCopter 上)

![http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/mphardware.png](http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/mphardware.png)

對於電子羅盤，一旦你啟用感應器有一個校準選項可用：

  1. 你也可以什麼也不做，程式碼也會嘗試使用飛行時的 GPS 和 IMU 讀數比較指南針的讀數的找出偏移和磁偏角。優點：不用麻煩使用者。缺點：它需要飛行幾分鐘以獲得正確的，所以首次發射的指南針是不準確的。
  1. 在 Mission Planner(如下圖所示)中手動校驗。你可以自己輸入磁偏角如下圖所示，只要按下"Live Calibration"按鈕，然後移動並旋轉一下你的飛行器約 30 秒，這樣它就會記錄資料及計算感應器的磁偏角。優點：它是有效的。缺點：這是一個有點不準確，尤其是大飛機，因為它無法反映馬達在運行時的磁場干擾。
  1. 重播飛行時的日誌檔。使用後面所提的使用日誌校驗是一個非常好的選項，你只需重播之前的飛行記錄日誌檔(.tlog)，代碼就會比對 GPS 及 IMU 電子羅盤的讀值，作出必要的修正。優點：它運作的非常好。缺點：你必須要有之前的記錄，如果你下載一個你沒有真正飛行的 .tlog 檔案，你的磁偏角將會是一個錯誤的值，就需要再做一次或者冒著較差飛行效果的風險。


為你的地理位置手動輸入磁偏角，你可以點擊下面的連結會開啟網頁瀏灠器並找到一個正確的數值。輸入你的位置它就會給你磁偏角，如下面圈起來的地方：

![http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/declination.png](http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/declination.png)

在例子中，我輸入了 "14.13" 到磁強計裡(軟件會自動把十進制數轉換為度/分)

4) **如果需要的話，設置逆轉舵機、副翼升降混控模式**

設置說明在[這裡](http://code.google.com/p/ardupilot-mega/wiki/ReversingTop).

5) 現在，如果你連上 MAVLink，切換到"飛行數據"選項卡，你會看到人工地平線隨板子移動。記住當你進入此選項卡後要把板子靜止 15-20 秒，因為 IMU 的必須首先校準。完成之後，HUD 將開始移動。

http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/Missionplanner1.PNG