# 簡介 #

SITL（軟體在環）模擬器，可以讓你不用任何硬件而運行 ArduPlane 或 ArduCopter。它是一個用普通的C+ +編譯器編譯自動駕駛儀代碼得到的一個本地可執行文件，可讓你無需硬件條件下測試代碼的行為。

# 詳情 #

HIL (硬件在環) 模擬是測試 APM 代碼的一個非常有用的方法。但是它有一系列限制，使得對某些任務來說不太合適。主要的限制包括:
  * 它不能運行所有自駕儀代碼，因為當硬件放在桌子上時，底層驅動代碼無法得到合適的輸入。
  * 不能使用在普通 C++ 開發中很有用的高級編程工具（例如調試器和內存檢查器）

ArduPilot 的 SITL 版本克服了這些限制。它仍然運行相同的代碼，但這個時候作為一個在PC上的本地可執行文件運行，並使用一些 C++ 技巧來在寄存器級模擬 APM 板硬件，所以關鍵的底層硬件驅動程序（如ADC、陀螺儀、加速度計和GPS）以如同在真實飛行中一樣運行。

## 生成 SITL 可執行文件 ##

SITL build（又稱作為 _desktop_ build），是在命令行中使用 'make' 命令生成的。如果你在 Linux 或 MacOS 下生成，那麼這很容易。如果你在 Windows 下生成，那麼你將需要安裝 Cygwin 來構建一個合適的類 Unix 環境。

### 先決條件 ###

開始構建之前，您需要確保安裝了幾件事情：

  * GNU 的 C++ 編譯器，稱為 g++
  * [MAVProxy](https://github.com/tridge/MAVProxy)，你可以從這裡的 Git 庫下載 git://github.com/tridge/MAVProxy.git - [祥細說明在這裡](http://www.qgroundcontrol.org/mavlink/mavproxy_startpage)
  * [pymavlink](https://github.com/tridge/mavlink)，你可以從這裡的 Git 庫下載 git://github.com/tridge/mavlink.git
  * [pyserial](http://pyserial.sourceforge.net/)，這是Linux上常見的包，在 MacOS 下使用 「sudo easy\_install pyserial」 安裝

如果你想要模擬一個quadcopter！ArduCopter然後就是你所需要的。

如果你想模擬一個四軸 ArduPlane，那麼你還需要下載，編譯和安裝的 JSBSim 開發快照，參見 http://jsbsim.sourceforge.net/download.html。 JSBSim 的可執行文件應在你的路徑 (PATH) 下。

### 構建 ###

要構建 ArduPlane SITL build，運行這個命令:
```
 cd ArduPlane
 make -f ../libraries/Desktop/Makefile.desktop
```

這將建立一個叫 ArduPlane.elf 的可執行文件。建立 ArduCopter.elf 的方式相同，但在 ArduCopter 目錄下。
請注意，構建可發出一系列警告，他們與 Arduino 的庫的頭文件的一些小問題有關。

## 開始 ##

你可以像運行任何本地可執行程序一樣運行 ArduPlane.elf 可執行文件。當它啟動時，它會在 TCP 端口5760 等待一個 地面站的 MAVLink 連接。此時模擬暫停，直到地面站連接。這當然與真正的硬件不同，但方便測試。

SITL 有一些啟動命令行選項：
  * -H 選項指定氣壓計模擬的初始海拔高度。當你啟動飛行模擬器存在延遲時，這可以確保高度不會突然變化。
  * -s 選項允許您設置的 APM1 「滑塊開關」，讓其進入命令行界面。要看 DataFlash 日誌的話，這就特別有用。
  * -w 選項在啟動時擦除 EEPROM 和 DataFlash。這相當於刪除 eeprom.bin 和 dataflash.bin 文件。

## 輸入和輸出 ##

運行時, SITL 接受兩種類型的網絡報文:
  * 從飛行模擬器發出的 sitl\_fdm 包，提供飛機的狀態更新。[sitl.cpp](http://code.google.com/p/ardupilot-mega/source/browse/libraries/Desktop/support/sitl.cpp) 描述了數據包格式，即 「struct sitl\_fdm」 。
  * 包含 8 個 PWM 值的 16 字節的接收器輸入結構
兩種數據包都在通配符網絡接口的 UDP 端口 5501 接收。

該模擬器將在 UDP 端口 5502 產生一種輸出數據包。數據包有 22 個字節，包括 11 個的 PWM 值，表示 APM 的 PWM 線路輸出。默認情況下，產生頻率為 50Hz，但你可以用 -r 命令行選項控制該頻率。

## EEPROM 和 DataFlash ##

APM 的 4kByte EEPROM 用，使用一個 4kByte 文件「eeprom.bin' 仿真。當生成 SITL 時，這個文件自動生成在當前工作目錄下。更新 EEPROM 方法與正常的 APM 相同（即通常通過 MAVLink 連接地面站）。

2MByte !APM1 上的 DataFlash 使用 2MByte 文件 dataflash.bin 模擬。當生成 SITL 時，這個文件也會自動創建。閱讀內容通常的方法是通過 CLI 接口，可以和一個正常的硬件的 APM 一樣的方式啟動。


## 串口仿真 ##

對 APM 的串行端口仿真使用 TCP 套接字。第一個串行端口（通常是通過USB連接）被映射到 TCP 端口 5760。遙測串行端口映射到 TCP 端口 5763。 GPS 串行端口映射到內部的GPS傳感器仿真。

你可以使用 telnet 或 netcat 連接到這些串行端口。有時可以用於連接到 CLI。 例如，在用 -s 開關啟動 ArduPlane.elf 進入 CLI 模式後，你可以這樣做：

```
$ telnet localhost 5760
Trying 127.0.0.1...
Connected to localhost.localdomain.
Escape character is '^]'.

Init ArduPlane V2.27 Alpha

Free RAM: 4096
Entering interactive setup mode...

Move the slide switch and reset to FLY.

ArduPlane V2.27 Alpha] 
```

但是，通常更有用的方式是連接到 MAVLink 兼容的地面站。例如，如下用 MAVProxy 連接：
```
mavproxy.py --master tcp:127.0.0.1:5760
```

如果要連接到 CLI，在 mavproxy 增加命令行選項 --setup。

你還可以使用TCP連接選項連接到 APM 任務規劃器。它可以設立任務。

## 傳感器仿真 ##

SITL 的一個關鍵部分是其對 APM 的各種硬件傳感器的仿真。傳感器模擬如下：

  * 陀螺和加速度計傳感器通過模擬 ADS7844 ADC 的進行寄存器級仿真。仿真的當前狀態的正確模擬值在 [sitl\_adc.cpp](http://code.google.com/p/ardupilot-mega/source/browse/libraries/Desktop/support/sitl_adc.cpp) 裡計算。
  * 空速傳感器（皮托管）也通過 ADC 的寄存器級傳感器驅動模擬
  * UBlox GPS 使用在[sitl\_gps.cpp](http://code.google.com/p/ardupilot-mega/source/browse/libraries/Desktop/support/sitl_gps.cpp)中的代碼在串行水平模擬。GPS 設置為沒有啟動衛星鎖定的最初啟動。當接收到從模擬飛行通過 sitl\_fdm 包發送緯度/經度/高度數據，模擬衛星鎖定
  * 氣壓計和指南針目前通過用於HIL仿真模擬的 setHIL() API 仿真。這些可能等 I2C 仿真層完成時移動到寄存器級仿真。

## 連接到飛行模擬器 ##

要真正飛 SITL，你將需要一個飛行模擬器。SITL 帶有 Python 接口腳本，可以支持飛 ArduPlane 的 JSBSim 飛行動力學模型，或飛 ArduCopter 的 sim\_quad 四軸物理模型。這些接口腳本都有選項，可以按 FlightGear 的原生 FDM 格式傳送飛行數據，允許你在 FlightGear 顯示飛行。

### 使用 sim\_quad ###

sim\_quad 是四軸飛行器在 ArduCopter 上的一個簡單的物理模擬。它提供了相當水平的模擬，足以測試 ArduCopter 代碼。

sim\_quad.py 腳本在APM Git樹中的「Tools/autotest/pysim 目錄下。像這樣啟動：
```
sim_quad.py --home -35.362938,149.165085,584,270 
```

home選項是必需的，並需要指定四軸在世界上的初始位置和朝向。形式為經度，緯度，海拔，朝向。高度是海平面以上多少米，朝向的單位是度。

啟動後，sim\_quad 將向 SITL 發送 sitl\_fdm 數據包，並將收 PWM 控制值。默認情況頻率為 1kHz。

模擬器將在 UDP 5503 端口以原生 flightgear FDM 格式發送數據，讓你在可以在 flightgear 裡查看飛行。一個包含正確的啟動選項的腳本在 Tools/autotest/fg\_quad\_view.sh。 flightgear 裡顯示的模型在 Tools/autotest/aircraft/arducopter 裡。

為了向模擬器提供RC輸入，你需要在 UDP 5501 端口提供 PWM 數據包，如 「輸入和輸出」 一節所述。最簡單的方法是使用 MAVProxy：
```
mavproxy.py --master tcp：127.0.0.1:5760 - sitl 127.0.0.1:5501
```
你可能還希望添加選項 --out 127.0.0.1:14550，以便把 MAVLink 數據包轉發到另一個地面站，例如 APM 任務規劃器 或 qgroundcontrol。

在 MAVProxy 中，你可以使用 rc 和開關命令來控制 RC 的輸入。歡迎提供支持通過真正的 RC 發射器或操縱桿控制的腳本代碼。

### 使用 JSBSim 模擬器 ###

如果你是模擬 ArduPlane，那麼你將需要使用 JSBSim 飛行模擬器。 JSBSim 是一個複雜的飛行模擬器，被多家知名的飛行模擬系統用作飛行動力學系統的核心。我們之所以使用 JSBSim 是因為它提供了獲得極高的幀速率模擬的方式，這對 SITL 的寄存器級傳感器仿真是必不可少的。

為了幫助 ArduPlane 連接 JSBSim，我們提供一個 Python 接口腳本 runsim.py。這個腳本處理啟動和運行 JSBSim，並翻譯 SITL 模擬輸入和輸出的細節。

runsim 腳本在 Tools/autotest/jsbsim/runsim.py，是這樣運行的：
```
runsim.py --home=-35.362938,149.165085,584,270 -script=jsbsim/rascal_test.xml --fgout=127.0.0.1:5503
```

home 選項與 sim\_quad.py 相同。--script 選項指明 JSBSim 的啟動腳本，指定模擬的飛機和不同的初始條件。在這種例子中，我們模擬一個 Rascal110 R/C 模型。fgout 選項告訴 runsim 在 UDP 5503 端口以原生的 FDM 格式向 flightgear 輸出數據。

請注意 rascal\_test.xml 包含一個 reset\_CMAC.xml 文件參考，這個文件也包含設置模型初始位置的緯度/經度（堪培拉模型飛機俱樂部）。

啟動之後，你可以像使用 sim\_quad 一樣用 flightgear 觀看飛行。Tools/autotest/fg\_plane\_view.sh 腳本可以以正確的選項啟動 flightgear。注意 flightgear 運行與否和模擬無關：在會話中發送了一個 UDP 數據流，flightgear 將根據這個數據流流顯示模型的當前位置和方向。flightgear 裡的飛機選擇和其他渲染選項並不重要，因為它是作為顯示模式運作。Rascal 模型可以添加到 flightgear 裡，參見http://www.flightgear.org/download/aircraft-v2-4/

與 sim\_quad 相同，你應該附加一個地面站例如 MAVProxy，並提供 RC PWM 輸入。目前最簡單的方法是使用 MAVProxy 開關和 RC 命令。

JSBSim 模擬默認情況下，將運行在1kHz，這意味著它和真正的硬件傳感器速度大致相同。

### 使用 fakepos.py ###

當調試 ArduPilot時，有時需要提供恆定的或可預見改變的傳感器的輸入，而不是一個真實的飛行模擬器的輸入。例如，如果你修改 DCM 的代碼，提供恆定的陀螺儀輸入可能是有用的。

Tools/autotest 裡的 fakepos.py 腳本提供了這種能力。使用它的方式是編輯該腳本，以提供按你想要的模式的傳感器輸入，然後和 SITL 一起運行腳本。

## 使用 autotest.py ##

創建 SITL 的主要原因是允許建立 ArduPilot 自動測試系統。自動測試系統是一套 Python 腳本，自動執行以上步驟，對 ArduPlane 和 ArduCopter 進行一系列測試。每個git的提交後的結果報告在[autotest.diydrones.com](http://autotest.diydrones.com/)

你還可以自己運行自動測試，只要運行 Tools/autotest/ 裡的 autotest.py 腳本。一個有用的選項是 --viewerip，可以告訴腳本輸出 MAVLink 和 flightgear 數據包到一個本地 IP 地址來查看飛行。

你也可以要求自動檢測跳過特定的測試，例如，如果你是修改 ArduPlane，不妨使用：

```
autotest.py --viewerip=127.0.0.1 --skip='*ArduCopter*'
```

你需要在 APM Git 樹目錄的父目錄下建立一個 「buildlogs 目錄，測試將把飛行試驗記錄放置在該目錄中。

ELF 生成之後，你可以運行 autotest.py，跳過除了你想測試 fly.xxxxx 之外的其他步驟。

ArduPlane飛行試驗的例子在 arduplane.py 裡，請檢查裡面的內容，查看可以 SITL 可以執行的各種飛行模式和運動。如果模擬的飛機沒有在測試中墜毀，並且達到了一些基本目標，例如高度、距離和航點，就可以認為測試「通過」。對飛行"質量" 沒有判決，但是留下了足夠的飛行數據，未來這也可能自動化。

## 例子 ##

則個視頻展示了用默認的 fly.ArduPlane 自動測試腳本，按 arduplane.py 裡的命令飛 "Rascal" 的航跡。所有的自動測試參數都是默認的。

<a href='http://www.youtube.com/watch?feature=player_embedded&v=jZYPlINuJz8' target='_blank'><img src='http://img.youtube.com/vi/jZYPlINuJz8/0.jpg' width='425' height=344 /></a>