== 使用電腦的遊戲遙桿來控制代替RC控制器的手動控制 ==

![http://wiki.ardupilot-mega.googlecode.com/git/images/gamepad.jpg](http://wiki.ardupilot-mega.googlecode.com/git/images/gamepad.jpg)

ArduPlane 允許你比一般RC遙控系統多使用一種遙控方式，使用電腦遊戲遙桿經由 Xbee 操控。要使用它，你必須具備以下條件：

  1. 無線遙控模組，如 [DIY Drones Xbee telemetry kit](http://store.diydrones.com/Xbee_Telemetry_kit_p/kt-telemetry-xbee.htm)
  1. 一個 USB 遊戲遙桿像 [這種](http://www.amazon.com/gp/product/B0000ALFCI/ref=wms_ohs_product)
  1. 一台筆記型電腦

Mission Planner 可以幫助你很容易的設置遊戲遙桿控制。我們建議您繼續把 RC 模組連接著，因為它有可能在飛行中失去 XBee 的連接，你需要能夠回復到一般的RC控制或者自動駕駛儀故障的情況下可以切換到 「硬體手動模式」。(另外，你可能會想保留 RC 的微調設置，！ArduPlane 會做。)然而，在大多數情況下，你可以使用遊戲搖桿來操控所有的手動飛行，完全不需使用 RC 發射器。

請跟著以下幾點一起來設置吧：一旦控制器是插入，只需選擇「搖桿」(下面紅色圈起來的地方)，它會打開一個訊息視窗，幫您把搖桿按鈕分配不同功能。

![http://wiki.ardupilot-mega.googlecode.com/git/images/joystick.png](http://wiki.ardupilot-mega.googlecode.com/git/images/joystick.png)

**祥細設置介紹:**

  1. 點擊「Auto Detect」並且移動控制器上的搖桿或按鈕就可分配功能。
  1. 點擊「Reverse」核取方塊，就可以反轉轉任何控制方向。
  1. 如果你的飛行器是三角翼(elevon)或飛行翼(flying wing)，Mission Planner 可以混合控制升降舵和副翼頻道，這種方式 RC 發射器就可以使用。只要點擊「Elevons」核取方塊並將它混合至這兩個頻道即可。
  1. 當你完成後，如果您單擊「Enable」，Mission Planner 將開始使用搖桿進行手動控制。所有其他功能將照常運作。
  1. 就如一個 RC 發射器只要在上面輸入「Expo」的值，就可以添加指數控制。
  1. 按下「Save」就可以儲存這個功能的設定值。
  1. 你所做的 RC 接收器微調設置就可以被保留(通過)。
  1. 你可以分配給搖桿的每個按鈕自動駕駛模式(Auto, RTL, Stabilize 等)的功能。