**常見故障解答**

常見問題的解決：




---


## 我的 APM 2 被鎖定 ##

這個問題可能是記憶卡沒有被正確的初始化。要解決這個問題，請將它拿出來\_再啟動 APM 2。你應該可以在 CLI 模式成功測試。如果真的是如此，有一個簡單的方法可以處理。將記憶卡插回去，在終端螢幕出現時把板子插上電源。就會將記憶卡重新格式化(這將需要一段時間)。讓它插入5-10分鐘。之後你應該就會看到"ready to fly"的訊息。你只能這樣做一次。


---


## 我無法安裝 Mission Planner ##

如果你是使用 Windows XP，請確認你已經安裝 Microsoft .net Framework 3.5 。你可以到[這裡下載](http://www.microsoft.com/en-us/download/details.aspx?id=22)。

如果你的 DirectX 出現安裝錯誤，表示你的 Windows 的 DirectX 版本不是最新的。請至[這裡下載](http://www.microsoft.com/en-us/download/details.aspx?id=35)。


---


## 我無法使用 USB 連接 Mission Planner ##

  1. 請再確認一次你 USB 的 COM port 號碼及鮑率(115200)。也同時檢查 Windows 的裝置管理員上面的 APM COM port 已經被註冊。如果有它會將它列出來。
  1. 你使用的是否為  MP 安裝版程式，是否有安裝驅動，安裝是否完整及成功?
  1. 你的 APM 是否有下載飛行韌體(ArduCopter 或 ArduPlane)?
  1. 你有按下 MP 的 Connect 嗎?


---

## 我無法使用 Xbee 連接 Mission Planner ##

首先，你要知道當你使用無線遙測模組連接 APM 2 時，就不可再連接 USB 電纜(因為它們是使用同一個序列埠)。請再次確認沒有連接 USB。

再來檢查你的 Mission Planner 的序列埠是否有選擇 Xbee 的序列埠號，這個序列埠號會連接你的 PC 並且將它的鮑率設為 57600。

請確認你已經完成完整的 Xbee 設置程序，請見[這裡。](http://code.google.com/p/arducopter/wiki/AC2_telemetry)在頁面的下方執行測試代碼，這樣可以確認你的 Xbees 是可以通訊的。**請注意 Xbees 必須在 X-CTU 燒錄分位才可使用 57k 的鮑率。**

如果你的 Xbees 突然停止運作，它可能是電纜鬆了，導致信號被干擾。您可以透過[這裡](http://code.google.com/p/arducopter/wiki/AC2_telemetry)的指示就可以解決這個問題。

## 我無法使用 3DR Radios 連接 Mission Planner ##

請記得當你使用無線遙測模組連接 APM 2 時，就不可再連接 USB 電纜(因為它們是使用同一個序列埠)。請再次確認沒有連接 USB。

再來檢查你的 Mission Planner 的序列埠是否有選擇 3DR radio 的序列埠號，這個序列埠號會連接你的 PC 並且將它的鮑率設為 57600。

## 飛機在返航模式下迂迴前進或徘徊；而不是向我飛來並在頭上盤旋 ##

你需要調整飛機的感度。我們假設你已按照飛行測試和[這裡](Tuning.md)的調整說明做了。那麼飛機應該在穩定模式下飛得不錯，並且在返航模式下會試圖回來。如果在頂風下飛回來很艱難，或者很容易偏離航線，那麼在任務規劃器的配置界面執行以下操作，直到解決問題:

  1. 將導航側傾 P 增加 25%
  1. 將導航側傾 P 增加 25%
  1. 將偏航矩感度增加 25%


---

## 使用 APM 2.x 時我的 ESCs 無法激活(馬達無法運作) ##

僅管 APM 2.x 可以在每一個我們所測試的 ESC 上運作的很好，只是這類產品有無數種變化而且有少數(尤其是一些中國廉價的產品)無法將標準的 APM 啟動處理的很好。如果你的無法激活(當插上電池時沒有聽到嗶嗶聲，以及在任何的 APM 模式下油門桿無法使馬達旋轉)，你也許是運作失常的其中之一。我們會持續改善程式碼以減少這個問題，但是暫時處理方法如下，這麼做可以讓你先啟動 APM 後再啟動 ESC：

  1. 先不要插上 LiPo 電池，使用 USB 供電給 APM。
  1. 一旦啟動後再插上 LiPo 電池。
  1. 現在可以拔下 USB 電纜線。


---

## 我的油門只有在手動模式下有作用 ##

這是一個安全機制，你的油門只有在地面的手動模式或者自動模式的自動起飛功能才會啟動。除非你的飛機已在空中活動，不然在其他的自動模式下都無法被啟動。


---


## 除了手動模式，其他模式都沒有舵機信號輸出 ##

若自駕儀處於穩定模式下，當你傾斜你的飛機或APM板時，舵機應移動來補償。在該模式下你也應該能夠將通過遙控搖桿移動舵機。如果他們不動，檢查以下內容：

  1. 遙控針腳是否用電調或其他電源供電了？
  1. 你的電池是滿的嗎？PPM 編碼器是比其他的 APM 更容易發生欠壓情況。當你接上電源時，如果你藍色的 PPM 編碼器 LED "閃爍較慢"，可以試看看換上剛充好的電池。
  1. 你在設置過程中設置了遙控嗎? 如果沒有，現在就設置。如果已經設置過，重新切到 CLI 設置菜單，輸入"reset"，然後輸入"radio"，重新設置一次。記住你必須用電調或其他電源給遙控供電。你插上接受的那些通道最低值應該在 1000 左右 ( 900 到 1100 都正常)，最高值在 1900 左右( 1800 到 2100 都正常).


---


## 無法讀取無線電的輸入訊號 ##

  1. 你ESC的RC引腳或其他5V電源是否有電？(必須要有電)。如果RC接收機的電源 LED 沒亮，這意味著 RC 設備是沒有得到電源。
  1. 你肯定 RC 的連接器有插在正確的位置嗎？請檢查所有的信號線是否有連接在板子上。
  1. 發射器是否開啟
  1. 將舵機插入接收器其中一個備用通道，並確保它可以運作。
  1. 我們已經向 Spektrum 回報這個討厭的綁定程序問題。要綁定接收器和遙測(TM1000+ AR8000到DX8)模塊，將它們(TM1000、AR8000)連接在一起。將發射器關閉(DX8關閉)，按下的遙測模塊(TM1000)和接收器供電側的小按鈕(接上鋰電池但不要接上4線連接器，接收器和遙測模組會開始閃爍(如果它們不閃爍就是TM1000故障)。當這種情況發生請按下無線電轉教練/綁定按鈕，它會綁定(距離至少保持10英尺)。確保它結合時，它會說「binding dsmx ------ receiver with telemetry」，如果它第一次無法綁定遙測模組您可能需要做第二次。


---


## APM 接上 USB 可以運作，但是電源使用 RC 設備(ESC/Lipo)就不能 ##

APM 允許 RC 的電源或透過 APM 的內建電源穩壓使用一個單獨的電池運行如[這裡](http://code.google.com/p/ardupilot-mega/wiki/Hardware?wl=es)所示。焊接跳線 SJ1 就決定。出廠預設的跳線是放在 RC 設備。

如果由於某種原因， RC 設備連接到電源，電路板卻沒有電，請檢查跳線是否焊接。如果沒有，如下圖所示，在兩個焊盤只要焊接BLOB把它們連接起來。

![http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/amonet-3.jpg](http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/amonet-3.jpg)


---


## 當我編譯時，在Arduino IDE底部窗口得到了一系列紅色錯誤，如下所述 ##

```
ArduPilotMega.cpp:17:24: error: FastSerial.h: No such file or directory
ArduPilotMega.cpp:18:23: error: AP_Common.h: No such file or directory
ArduPilotMega.cpp:19:51: error: APM_RC.h: No such file or directory
ArduPilotMega.cpp:20:77: error: APM_ADC.h: No such file or directory
```

解決辦法: 你沒有將庫文件放在正確的目錄中，也沒有在Arduino IDE的配置菜單中設置正確的目錄。參見[本說明](Code.md), 確保所有東西都在正確的位置，重新啟動 Arduino 並重新編譯。


---


## 當我編譯時，我得到了一些\*不同\*的錯誤 ##

```
C:\Users\Chris\Documents\Arduino\libraries\APM_RC\APM_RC.cpp: In function 'void TIMER4_CAPT_vect()':
C:\Users\Chris\Documents\Arduino\libraries\APM_RC\APM_RC.cpp:40: error: 'ICR4' was not declared in this scope
C:\Users\Chris\Documents\Arduino\libraries\APM_RC\APM_RC.cpp: In member function 'void APM_RC_Class::Init()':
C:\Users\Chris\Documents\Arduino\libraries\APM_RC\APM_RC.cpp:73: error: 'COM1C1' was not declared in this scope
C:\Users\Chris\Documents\Arduino\libraries\APM_RC\APM_RC.cpp:77: error: 'OCR1C' was not declared in this scope
```

解決辦法: 在編譯/上傳之前你忘了將開發板類型設為 "Arduino Mega (Atmega1280)"。


---


## 我的 MUX 燈一直閃爍，而且 RC 的讀數很奇怪。舵機可能像瘋了一樣亂擺 ##

舵機像瘋了似的抖動著。

解決辦法：APM 的 Atmega328 的PPM 編碼器固件可能損壞。刷新/升級的說明在[這裡](Encoder.md).


---


## 我用 MediaTek GPS，儘管模塊的鎖定藍燈常亮, APM 也不顯示鎖定，在遙測中無法獲得 GPS 數據 ##

在遙測模組中無法取得 GPS 訊號。

解決辦法:

可能的原因有多種。首先，保證你在配置文件中選擇了正確的 MediaTek 版本。如果的模塊是在2010年12月以前從 DIY Drones 買的，它的版本應該是1.0: 在配置文件中選擇 GPS\_PROTOCOL\_MTK。如果你在之後買的，就是1.6版的固件: 配置文件中選擇 GPS\_PROTOCOL\_MTK16 。

MediaTek 的啟動過程中有一個時鐘錯誤。我們正在解決。現在應該在板子上電之後按一下重置按鈕（即熱啟動)。MediaTek 模塊第二次將接受正確的設置字符串，APM 將顯示鎖定。

最後，如果還不正常，檢查連接線是否破損。


---


## GPS 無法鎖定, 並且/或者 板子不斷重啟 ##

解決辦法: 你確定把 GPS 模塊插到 APM 板上，而不是 IMU 板上？（寫著 "NO GPS!"）


---


## 無法訪問數據記錄存儲器 (讀取代碼當機) ##

解決辦法: 你是否記得焊上了 連接 IMU 板和 AT1280 ICSP 端口的 2x3 插針，如[組裝說明](Assembly.md)所述?