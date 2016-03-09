### 使用地面站軟件 ###

![http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/chasecam.gif](http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/chasecam.gif)

## 什麼是地面控制站? ##

地面控制站通常是一個運行在地面上電腦中的應用程序。它通過[無線遙測](Wireless.md)與 UAV 通信。它顯示 UAV 性能和位置的實時數據，並可以充當"虛擬座艙"，顯示許多儀表，感覺就跟飛真飛機一樣。

地面控制站也可以在 UAV 飛行過程中控制它，上傳新的任務命令和設定參數。它也經常用來顯示 UAV 攝像機拍攝的實時視頻流。

**注:** APM 遙測端口的默認波特率為 57600。請據此設置 Xbee 模塊和地面站軟件。

數個地面站軟件都支持 APM, 還有更多的正在開發中。當它們成熟之後，將被加到這裡(參見左側的菜單項)。目前的選擇包括:

  * [HappyKillmore 地面站](http://code.google.com/p/ardupilot-mega/wiki/HappyKillmore): 只支持Windows。這是一個完整的GCS, 支持很多自駕儀，並且與 DIY Drones 團隊共同開發，完整支持 APM.
  * [任務規劃器](Mission.md): 只支持Windows。 這就是用來規劃任務的那個程序，它也包含了基本的 GCS.
  * [QGroundControl](http://code.google.com/p/ardupilot-mega/wiki/QGC): 一個強大的，高度可定制的 GCS，由設計了 MAVLink 協議的團隊開發。支持 Linux, Windows, 和 Mac.