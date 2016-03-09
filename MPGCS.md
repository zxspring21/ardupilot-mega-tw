## 使用任務規劃器地面站 ##

![http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/hud_cn.jpg](http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/hud_cn.jpg)

上圖是任務規劃器的主要地面站視圖，並顯示了抬頭顯示器 （HUD）。一旦你已經使用 USB 或 無線遙測模組連接 MAVLink，螢幕上的儀表和位置將會顯示由 APM 發送的遙測數據。

一些提示：

  * 地圖上的當前位置只有在鎖定 GPS 或使用飛行模擬器時才會顯示。
  * 請記住人工視圖的運作方式：當機鼻向右時，視圖就會向左。(只要轉轉你的頭你就會知道我的意思)。這是很正常的原理!請不要告訴我們它是相反的。
  * Autopilot 狀態中，顯示的含義如下:
    * "WPDist" : 到下一個航點的距離（單位是米）
    * "Bearing ERR": 你的 UAV 與到下一個航點的直線偏移了多遠
    * "Alt ERR": 你的 UAV 與目標高度偏移了多遠
    * "WP": 下一個到達的航點
    * "Mode": 當前自駕儀模式
  * "Ardupilot 輸出" 指自駕儀前四個通道的輸出
  * 你可以用 Mission Planner 或其他地面站向空中的飛機發送改變模式和其他命令，但要注意，必須在自動駕駛儀控制下他們才能生效。當你的RC撥動開關在手動位置時，就不在自動駕駛儀控制下，因此命令不會生效。其他位置（穩定，飛線，自動或任何其他的自動駕駛儀控制模式）下MAVlink命令生效。
  * 你可以利用 Windows 的控制台中的 "Text to Speech" 選項變更合成語音。
  * 如果你雙擊 HUD，它將彈出，可以在第二個屏幕上全屏顯示。
  * 如果你雙擊速度表，你可以設置需要顯示的最大量程。
  * 如果你啟用了調整復選框，並雙擊調整，你可以繪製status頁上的任意數據的圖。這意味著你可以實時顯示高度、姿態和很多其他選項。
  * 你可以使用自定義圖像代替 Google Maps。按 control-F，這允許你上傳自己的圖像。使用時會需要全球地圖，這是目前在 planner 中輸出時所需的格式的關鍵步驟之一。


---


### 指導模式 ###

![http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/guided.png](http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/guided.png)


高級無人跡的一個最常用的特性就是實時的點擊式任務控制。與預先規劃的任務或者人工控制飛行不同，操作員在地圖上點擊，告訴飛機「現在飛到這裡」。


現在 APM 也實現了這個功能。你可以在地圖上右鍵單擊，選擇「飛到這裡」。無人機將飛到那裡，然後盤旋，直到你給它下一個命令。我們稱這種模式為「指導模式」。這種模式更多命令將在最近添加，但是功能已經內置好了。


註：指導模式是一個獨立的飛行模式。如果你進入該模式，將一直保持這個模式，直到你改成其他模式。所以如果你告訴它「現在飛到這裡」，在到達之後會在航點盤旋，直到你告訴它幹點別的事情。這裡說的別的事情包括飛到下一個指導的航點（保持在指導模式）或改為其他飛行模式。如果你改到自動模式，你的任務將從停止的地方繼續執行。
