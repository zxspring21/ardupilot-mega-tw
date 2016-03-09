== 關閉 APM 2 內建的 GPS ==

如果現在你使用的是 APM 2 內建的 Mediatek GPS，可是你想換成外接式或不同的 GPS 模組，你可以跟著下列簡單的修改說明變更：

只而要將兩個針腳短路焊接即可，如下圖：

![http://wiki.ardupilot-mega.googlecode.com/git/images/disablegps.jpg](http://wiki.ardupilot-mega.googlecode.com/git/images/disablegps.jpg)

## 測試 ##

  1. 先不要接上外接式的 GPS，透過 Mission Planner 連接 APM。HUD 應該會回報 "No GPS"。 這樣是正常的 -- 它意思是尚未安裝 GPS 模組。現在可以切斷板子的連結及電源/移除 USB 電纜線。
  1. 連接外接的 GPS 到 GPS 埠
  1. 接上 USB 電纜線並且重新透過 Mission Planner 連接
  1. 只要有連接上，它應該會回報 "No Fix" (如果你是在室內或者尚未找到衛星訊號)或 "3D Fix" (如果接放到衛星訊號)。不管為哪一種都是正常的狀況 -- 它意思就是你已安裝好新的 GPS !