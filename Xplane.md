== 如何用 Xplane 設置半實物仿真模擬 ==

![http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/Xplane.png](http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/Xplane.png)

用 APM 建立一個強大的"硬件仿真"模擬器是很容易的。飛行模擬器使用傳感器和 GPS 數據"欺騙" APM，讓它認為它在飛行，然後 APM 就會照此控制飛機。

整個設置如圖所示:

![http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/X-Plain-Sim.jpg](http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/X-Plain-Sim.jpg)

### 設置步驟 ###

  1. 下載[X-Plane 飛行模擬器](http://www.x-plane.com/downloads/x-plane_10_demo/)，如果你不想購買。免費試用版可以讓你試玩10分鐘。想要[購買完整版](http://www.x-plane.com/store/x-plane_10/)只要 $79。我們目前支援 9.x 和 10.x 的版本。
  1. 用 Mission Planner 加載 APM 的 Xplane 模擬器版本(下圖中紅色圈起來的地方; 選擇一台你想要模擬的飛機)。
  1. 如果你還沒有設置，按固件頁的"APM 設置"按鈕。這將打開一個對話框，按照對話框上「重置」、「遙控輸入」和「模式」頁上的說明操作。現在就準備好模擬了！

![http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/missionplannerHIL.png](http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/missionplannerHIL.png)


### 連接 APM 和 X-Plane ###

任務管理器作為 APM 到 X-plane 的橋樑，會把 APM 的串口輸出數據發送到飛行模擬器。

**注意**: 在模擬模式下，CLI 模式 (和滑動開關)都禁用了。請用任務管理器的配置頁進行設置。

<a href='Hidden comment: 
如果你使用的是 Mac 系統，你可以使用 Perl-based 方案(如果你願意這也可在 Windows 上執行)。你需要這個檔案：

這裡是 Perl 檔案: [http://api.ning.com/files/xRNyASq2LjL3D2W7-D-4tvKSdm-2NifDygSAVsFxnngOUoIC4XkcPnGyPL-zeJJRNrWyuifxCVSQnyMVibddCBg-OzRzLOQ9/XPlane.pl X-Plane.pl]
'></a>

### X-Plane 設置 ###
X-Plane 通過網卡與任務規劃器通信。因此你可以在兩台機器上分別運行 X-Plane 和 飛行規劃器。這對在慢機器上運行 X-Plane 有所幫助。幀速率是非常重要的。

你可以選擇 X-Plane 裡的任何飛機，但是最符合我們目的的飛機是 PT-60 遙控飛機。

下面一些截圖顯示了你需要在Setting菜單 Data Input and Output 裡需要設置的東西:

![http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/Xplane_menu.jpg](http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/Xplane_menu.jpg)


![http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/mavlinkhil.png](http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/mavlinkhil.png)

你可能希望開啟屏幕顯示幀率(Frame Rate)選項。

在 Xplane 的 IP 頁, 把 UDP 端口改成 49005，如圖所示。(任務規劃器也有一個高級 IP 設置對話框，但默認值是 49000。49005 是 Xplane 的輸入端口，49000 是任務規劃器的輸出端口)

http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/xplane2.PNG


如果你在運行 APM 任務規劃器的同一台機器上運行 X-plane，則輸入環回 IP 地址（127.0.0.1），如上圖所示。如果你在不同的機器上運行 X-plane，則輸入另一台機器的 IP 地址（例如 192.168.1.1）.


### 飛行規劃器設置 ###

現在可以運行模擬器了。打開任務規劃器，選擇分配給 APM 的串口，設置為 115200 波特率。單擊 Simulation 頁，可以看到如下屏幕:

http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/missionplannersim.PNG

如果你使用 X-Plane 10.x，你必須選擇「XPlane 10」的核取方塊，如下圖所示：

http://wiki.ardupilot-mega.googlecode.com/git/images/xplane10.PNG

如果你在運行 APM Mission Planner 的同一台機器上運行 X-plane，則默認的 IP 設置應該就可以了。如果你有疑問，可以檢查 "高級 IP 設置"。IP地址應該是 127.0.0.1，端口應該是49000，如圖所示。如果你在不同的機器上運行 X-plane，則輸入另一台機器的地址（例如 192.168.1.2）。兩種情況下端口都應該是 49000。

在單擊 Sim Link Start/Stop 後，如果 APM 已經連上，Xplane 正在運行，你可以看到任務規劃器的模擬器窗口充滿了數據:

如果你選擇 PT-60 的話，你可以加載一個 PT-60 的配置文件。你可以從[這裡](http://code.google.com/p/ardupilot-mega/downloads/detail?name=xplane_PT_60.param&can=2&q=)下載該文件，在任務規劃器的設置頁面/原始參數選單裡加載該配置文件。

打開發射器，檢查接收機的連接。(記住如果你是使用 APM1 必須插上電調和電池，才能給接收機供電；在 APM2 則非必要，無線的電源來自 USB)。當你移動操縱桿時，可以在任務規劃器的遙控窗口看到 APM 的輸出數據發生變化。

第一次測試飛行時，把三個遙控模式開關設為手動、穩定和返航。你可以通過任務規劃器的 MAVLink 設置 (記住在飛行模擬模式下，CLI 不管用)。在任務規劃器連接後，按 control-G可以跳到設置對話框，然後就能找到模式設置。

### 飛行測試 ###

現在用你的RC發射器控制模擬器裡的飛機。首先，按「C」鍵，這樣你就可以從側面看到你的飛機。試試 RC 發射器上的每個搖桿，確保控制面在手動模式中方向正確。如果他們不對，在遙控發射器上逆轉它們，就像普通遙控飛機一樣。

你現在可以嘗試飛行。在 Xplane 裡重新加載飛機，按 "a" 切換到後視圖，按 "b" 鬆開剎車。飛機應該向前移動。你可以用尾舵搖桿在地面上控制轉向。一旦速度足夠，給一點升降舵使其起飛。你就可以向遙控飛行模擬器一樣飛行了。

如果飛的還可以，嘗試把模式開關切換到穩定模式。飛機應該立即水平飛行。如果飛機開始側傾，你需要用 APM 板上的 DIP 開關逆轉副翼舵機。類似的，如果開始俯衝，你需要逆轉升降舵機。

如果穩定模式飛得不錯，嘗試返航。飛機應當返回航線的起始位置，在上方 100m 處盤旋。

如果一切正常，嘗試輸入一些航點，飛自動任務。在任務規劃器裡讀取存儲的航點，讓它把返航點射為存儲的位置（即模擬器裡飛機起飛的機場）。點擊增加一些航點，切換到自動模式，觀察輸出！

總的來說，正確加載和運行的順序如下：

  1. 用任務規劃器加載模擬器版本的 APM 固件並執行設置。
  1. 啟動 Xplane。 在初始化完成，飛機還在地上的時候，按 "a" 鍵切換到後視圖，按 "p" 鍵暫停。
  1. 啟動任務規劃器，選擇正確的端口和波特率，連接 APM.。
  1. 在任務規劃器的模擬器頁，按 ArduPilotSim 按鈕連接。你可以看到輸出框裡出現數據。把發射器模式開關切換到手動模式，檢查輸出是否隨搖桿移動。
  1. 確保油門搖桿放到最低。
  1. 切換到 Xplane。可以起飛了。按 "p" 鍵繼續，按 "b" 鍵鬆開剎車，給油，起飛！


---


### 提示: ###

  * 我在 Xplane 裡飛 PT-60 的效果不錯。我建議巡航速度為 15 米/秒。
  * PT-60 的一個問題是它在地面上跳的很厲害，所以如果你不注意的話，容易打到螺旋槳，然後就出引擎錯誤。這很討厭。如果引擎停下來了，重新加載飛機。握住螺距搖桿，慢慢爬升，然後再給全油門。
  * 記住 APM 總是會自動設置它的「老家」位置，也就是 Xplane 裡的機場位置。它會覆蓋你在任務規劃器裡設置的老家位置。如果你想在模擬器裡選擇不同的機場，必須在 Xplane 的 "Location" 菜單裡選擇。你只能選擇提供的機場，而不是你想飛的任意位置。
  * 記住 CLI 模式已禁用，所以必須通過任務管理器執行所有設置！
  * 如果你想玩玩代碼，如[這裡描述的](Programming.md)用 Arduino 加載固件，而不是用任務規劃器裡預編譯的hex文件，你也可以這麼做。 你住需要按如下所述修改 APM\_config.h 文件:

```
#define HIL_MODE            HIL_MODE_ATTITUDE
```

HIL\_MODE\_SENSORS 目前沒有(2012年1月)運作。HIL\_MODE\_ATTITUDE 會通知！ArduPlane飛機的狀態，但非加速度或roll rates。HIL\_MODE\_SENSORS 原本要將較低階的物理水平加至真正的感應器代碼，進而得到相同或近似的狀態數字，從氣壓計等再加上更多的信息。

Software-in-the-loop (SITL)模擬已經有更進一步的功能，盡可能在最低階的地方模擬 !Arduino 暫存器及加入感應器資訊，因此如果你想要去模擬最真實的輸入是個不錯的選擇。

### 錯誤消息和修正 ###

1. 無法打開串口: 沒有選擇串口或者串口被其他程序佔用。你是否開啟了一個終端連到 APM？提醒你開啟 Mission Planner 時就會將序列埠加入它的序列埠選單，如果USB的驅動載入失敗並且沒有設備插入!Windows 端口，那麼這個選單將缺少實際的端口或可能會預設到另一個端口。

2. 套接字(IP)設置問題。你是否已經打開? : 有另外一個程序佔用了 IP 端口，與 Xplanes 和 APM 規劃器之間的數據通信發生衝突。

3. Xplane 數據問題 - 需要數據輸入/輸出 3, 18, 19, 20 : 重新配置，確保所有的復選框都選上了。你需要重啟 X-Plane。

4. Bad Gains!!! : 至少一個模擬器感度值無效

5. 沒有模擬數據 : Ardupilot Mega Planner 沒有從 Xplane 收到任何數據。檢查 Xplane 設定。

6. 遙控無法控制，移動操縱桿也沒有任何反應? 你的 PID 都設成 0 了？你有設定無線輸入端？預設的配置可能不適合您的RC遙控器，請檢驗最小、最大及微調參數，如果有必要請使用RC遙控器的設定模式不論是從 Mission Planner 或者從命令列設定。

7. 飛行控制偏移，需要將操縱桿壓到一邊才能飛行? 檢查 APM 裡的遙控設置。你配置過遙控器？請見(6)

### 調試 ###

1. 螢幕狀態顯示僅在正確連接 APM 後才會更新。

2. 打開終端，觀察你看到的數據。如果數據可讀，轉到 2b, 否則轉到 2a

2a. 當你單擊 Connect 按鈕，你應該能看到文本框中印出 APM 頭。如果沒有，可能是序列埠號碼或者鮑率不正確。

2b. 打開 APM 規劃器中的終端，查看輸出，驗證設置。它應該以 APM 頭開始，然後持續輸出  AAA????。如果你沒看到 AAA，檢查 APM\_config.h 文件，開啟 HIL, 並且確保你沒有在設置模式裡面（滑動開關位置錯了)。