## 使用 DIP 開關設置舵機方向及 Elevon Mode ##

![http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/dipswitches.jpg](http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/dipswitches.jpg)

遙控設置和飛機設置都各不相同，如果你熟悉 RC 的設定，你會知道舵機通常需要反轉的方向。對 APM 而言也是，但較複雜的是你需要為手動(RC)及自動駕駛飛行正確地設置飛機。

程序如下:

  1. 首先為你的飛機設定 RC 飛行參數。在 APM 中使用手動模式，當你移動你的遙桿時，請確認所有的控制項看起來都是正確的。如果有任何的不對的地方，請反轉發射器的通道。
  1. 現在把 APM 調到穩定模式(我假設你已經完成了 APM 設置，包含無線電的設置)並且移動一下飛機，觀察控制面板上的數值如何變化。他們應該會向某個方向移動然後再讓飛機回到水平面飛行狀態。所以當你將機鼻向下，水平線應該會向上移動。 而副翼為傾斜飛機向左，右邊的副翼會上升左邊的則會向下。如果不是這樣你就可以利用 APM 上的 DIP 開關或者透過軟體用 MAVLink 來反轉通道。

註: 方向舵在地面上是有些難以觀察，因為它的動作主要是用來抵消空氣中的慣性力。但是當你橫滾機體時，當需要讓水平線回到水平狀態時，方向舵應該在同一方向移動。所以當飛機的水平線向左邊傾斜，方向舵應該也要略微向左(這就是所謂的 "協調轉向")。如果它在相反的方向移動，請反轉它。也可看[adverse yaw](http://en.wikipedia.org/wiki/Adverse_yaw)來了解這個原理。


## 設置 Elevon 模式 ##

你可以很容易的反轉舵機或選擇使用 APM 擴充板上內建的的 DIP 開關。


![http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/dipswitches.jpg](http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/dipswitches.jpg)

首先，你需要告知你是飛的普通飛機（帶有副翼和/或垂直尾舵）還是帶有升降副翼混控的飛機（三角翼或飛翼）。第四個 DIP 開關決定模式。如果你用升降副翼混控，其他開關的功能也會發生改變，如圖所示：

這裡有一個以 Skyfun delta wing 的範例，這是使用舵面混控:

![http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/elevons.jpg](http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/elevons.jpg)

如果你的設定仍然有問題 -- 例如，橫滾正常但是升降是反轉的，或反之亦然 -- 試看看交換舵機的電纜線的通道。

### Elevon 教學 ###

你的發射器一旦正確地完成手動控制設置，接下可能有3項反轉開關的8種組合。其中2種組合會在手動模式產生正確的舵機輸出，不管如何，只有1種組合可以在手動模式中產生正確的舵機輸出，並且在自控模式中例如穩定模式，可以正確地配對到發射器的輸入端，操作橫滾/升降命令。這需要一點點的嘗試和錯誤，才能找到正確的組合，在這裡有一個教學：


  1. 首先，在手動模式下設置，就是透過 RC 發射器上 elevon 混控做設置。重要的 elevon 插入到哪個通道！以我的 Skyfun 為例，左側的副翼應該插到 Ch1 ，右側的則是 Ch2
  1. 現在手動模式已經可以運作，透過 Mission Planner 的設置過程來設置 APM 的無線電。
  1. 移動 elevon 將 DIP 開關調到最上面的位置。重置控制板。
  1. 現在移到穩定模式，移動機體測試一下。你也許會需要反轉某些通道。在 Skyfun，我已經反轉 Elevon 的 Ch1。一次只要改變一個通道!
  1. 如果橫滾正常但是升降是反轉的，或反之亦然，試看看交換舵機的電纜線 (在接教器及 APM 都要同時做)。


記得: 如果你在 Elevon 模式飛行，你的 RC 發射器也必須被設定為 elevon 混控。Elevon 模式只可以運作於發射器有支援的狀態下(幾乎都有支援)。


## 油門通道反轉 ##


油門通道反向仍然必須在配置文件中設置——我們不希望某人意外撥動一個開關就導致油門升到最大!

如果你需要反向油門通道，修改 APM\_Config.h 文件，將下面一行改成 "ENBALED":

`# define THROTTLE_REVERSE		DISABLED`