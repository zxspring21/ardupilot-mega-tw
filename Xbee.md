## Xbee 測試 ##

**說明:**

根據該[說明](Wireless.md)連接 Xbee 模塊。確保 APM 通過 USB 與電腦相連，並且地面 Xbee 模塊也通過 USB 與電腦相連。

在CLI中，輸入 "test" 進入測試模式，然後輸入 "xbee"。在PC上，啟動 X-CTU 工具。確保 X-CTU 中的串口設置為連接到地面模塊的串口，波特率為 57600 bps (默認值) 或 你的 APM 端口的設置。 (在下圖中，我將 Xbees 和 Port 3 的波特率都設為 38400).

**樣例數據:**

在 APM 端，串口監視器應當顯示下面的數據:

![http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/clixbee2.png](http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/clixbee2.png)

在 PC 端, X-CTU 工具應當在終端窗口顯示類似下面的數據:

![http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/clixbee3.png](http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/clixbee3.png)

你也可以測試距離。開始測試，你應該可以看待類似下圖的數據：

![http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/clixbee1.png](http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/clixbee1.png)

在CLI中按回車鍵退出測試。

**附註:**

如果你想修改 Xbee 模塊的速率，可以在 APM\_Config.h 文件中設置。在文件中加上這行，並將 38400 改為你想設置的速率:

`#define SERIAL3_BAUD        38400`