==命令行解析器和設置/測試模式==

如果需要，你可以通過命令行解析器（Command Line Interpreter，CLI）設置和測試APM。它有點類似於傳統的DOS提示符。只有透過 USB 連接才有作用；無法透過 Xbee/3DR 無線模組連接。

  1. 在 Mission Planner 中點擊 Terminal，將打開 Terminal 視窗（確保選項選單裡的串口鮑率設置為 115200）。它會自動帶你到 APM 的 CLI 選單（如果沒有，點擊窗口，按下「Enter」鍵三次）：

http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/mpterminalAPM.PNG

現在可以鍵入命令。在任何模式下，鍵入 "exit" 可以退出。

在下面的例子中，我將使用另一個串口終端 （這裡是 Arudino 串口監視器）。你可以使用任何終端，但是任務規劃器的終端是最簡單的。

這裡我輸入 "help" 查看命令列表:

![http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/help.png](http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/help.png)

起始命令包括:

  * **"logs"**: 記錄回讀信號/設置模式。（在飛行之後使用）
  * **"setup"**: 初始設置模式
  * **"test"**: 測試模式

## 設置 ##

設置過程根據你的遙控設定和需要的飛行模式配置APM。輸入 "setup" 然後按回車鍵進入該模式。

**在飛行前必須進行遙控設置和飛行模式設置。你還應該測試GPS鎖定（在測試模式中使用gps命令），這通常需要在空曠的戶外進行。**

允許的設置命令包括:

  * **"reset"**: 重置APM為默認設置
  * **"radio"**: 設置遙控（見下文）
  * **"modes"**: 設置觸發開關每個位置對應的飛行模式
  * **"compass"**: 開啟磁力計。命令為 "compass on" 或 "compass off"
  * **"declination"**: 為磁力計設置當地磁偏角。你可以在[這裡](http://www.ngdc.noaa.gov/geomagmodels/Declination.jsp)找到當地磁偏角。儘管它以分和秒的形式給出，輸入時候還是按10進制數輸入。例如 `14° 10' E` 的輸入為 14.10。
  * **"battery"**: 開啟電池監控。輸入選項 0-4 (repeat to enter additional options):
```
     0 = 電池監控關閉
     1 = 監控 3 芯電池
     2 = 監控 4 芯電池
     3 = 監控電池電壓
     4 = 監控電池電壓和電流
```
  * **"show"**: 顯示 EEPROM 中當前所有設置
  * **"erase"**: 擦除 EEPROM

### 遙控設置 ###

_注: APM 無法提供電源給 RC 接收器或伺服機(僅管 RC 接收器可以供電給 APM)。如果你的 APM 電源是來自 USB，你也必須要連接 ESC/Lipo 或者接收器的電池到 APM 的 RC 接腳(一般來說，ESC 會接到接收器 Out 3，而 APM 的電源也是經由接收器而來)。如果你不單獨給 RC 系統電，APM將無法讀取RC輸入的任何信號。_

在這個模式中你必須移動發射器搖桿到它們的極限位置，如下所述:

移動右搖桿到右上角，再到右下角，再到左上角，再到左下角。對左搖桿重複以上操作。移動順序其實不重要，重要的是每個搖桿都碰到了4個角。

這是一張典型的遙控設置過程的截圖:

![http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/setup2_cn.png](http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/setup2_cn.png)

**注**: 如上圖所示，你連接的通道的讀數的最小值應該在1000-1300左右，最大值在1900-2000左右。(如果讀數恰好為1000和2000，那就是說通道沒有連上。) 如果你的讀數都在1500左右，可能有三個原因:

  1. 在測試過程中你沒有將搖桿移動到極限位置（4個角落）
  1. 你的接收連接不正確，可能是插反了，或者插錯引腳，或者沒有連上
  1. 你的APM板子版本較老，需要更新PPM固件。參閱[相關說明](Encoder.md)

### 飛行控制模式 ###

下面敘述如何設置飛行模式：

在CLI中，進入設置模式。輸入 "modes" 並按回車。現在當你撥動遙控上的開關時，你可以看到窗口中顯示對應的飛行模式。如果你想改變飛行模式，使用發射器上的「方向/副翼」搖桿。將搖桿左右移動，飛行模式就會變化。輸入回車鍵保存設置並退出。

參見這個例子：

![http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/modes_cn.png](http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/modes_cn.png)

這裡是一個視頻教程:

<a href='http://www.youtube.com/watch?feature=player_embedded&v=E7RE1B0lhk4' target='_blank'><img src='http://img.youtube.com/vi/E7RE1B0lhk4/0.jpg' width='425' height=344 /></a>

### 檢查舵機反向設置 ###

現在是檢查舵機反向設置的好時候。相關說明在[這裡](Reversing.md)。記住如果你的飛機有升降副翼（飛翼或三角翼），你還要用撥動開關設置混控。如果你的飛機是普通飛機，但是發現通道1和2有某種關聯，那就意味著你不小心設置了升降副翼混控。將撥動開關撥到下方，切回普通模式。

## 記錄 ##

該模式允許你讀取和管理記錄在16MB數據記錄器中的飛行記錄文件。

**注**:  你必須在使用記錄功能之前先執行erase命令。沒有使用erase命令將導致不正確的記錄和其他問題。

  * **"dump (n)"**: 讀取記錄 "n"
  * **"erase"**: 清除所有記錄
  * **"enable (name) or all"**: Enable logging "name" or everything
  * **"disable (name) or all"**: Disable logging "name" or everything

## 測試 ##

你可以在交互測試模式中測試你的硬件和設置。請參閱[詳細說明](Test.md)。