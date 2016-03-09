== 在 APM 2 上使用 3DR 無線電模組 ==

3DRobotics 的[3DR 無線電模組](https://store.diydrones.com/3DR_RadioTelemetry_Kit_915_Mhz_p/kt-telemetry-3dr915.htm)提供一個不錯的連接方式來設置遙測模組。

連接你的 APM 及 地面站。體積小、價格便宜及不錯的通訊距離，3DR 無線模組使用開源的韌體允許我們與其它無線電設備通訊。


### 無線電特性 ###

  * 非常小的尺寸
  * 重量輕 (不含天線小於 4 公克)
  * 兩種通訊頻率 900MHz 或 433MHz
  * 接收器靈敏度可到 -121 dBm
  * 傳輸功率最大達到 20dBm (100mW)
  * 清楚的序列連接
  * 空中資料傳輸頻寬最大達 250kbps
  * MAVLink 協議框架及狀態回報
  * 跳頻式展頻 frequency hopping spread spectrum (FHSS)
  * 自適性分時多工 adaptive time division multiplexing (TDM)
  * 支援 LBT 和 AFA
  * 可配置的工作週期
  * 內建錯誤校正碼 (最大可以校正 25% 資料位元錯誤)
  * 使用一個小型全向天線就可以使用數公里的範圍
  * 雙向放大器可用於更大的範圍
  * 開放源碼的韌體
  * AT 命令的無線電配置
  * RT 命令的遠程無線電配置
  * 使用 APM 就可以有適當流量控制
  * 基於HM - TRP 的無線模組，Si1000 8051 的微控制器和 Si4432 無線模組

![http://wiki.ardupilot-mega.googlecode.com/git/images/3DRadio/3DR-radio-kit-dip-small.jpg](http://wiki.ardupilot-mega.googlecode.com/git/images/3DRadio/3DR-radio-kit-dip-small.jpg)

## 使用 FTDI-to-USB 電纜線設置 3DR 無線電模組 ##
> 如果前面的說明無法運作，請嘗試以下…

> ## 所有的接頭接好，開始設置 3DR 地面端無線電模組 ##
  * 使用 FTDI-to-USB 電纜線連接 3DR 空中無線電模組到你的電腦上的 USB 埠並且記下 Com port 號碼
    * 利用 Windows > 裝置管理員 > 連接埠，上面會有 com port 號碼
    * 當綠色 LED 閃爍時，你就會知道 FTDI 電纜線是否正確連接到空中無線電模組。

  * 連接 3DR 地面站無線電模組到你電腦上的 USB 埠，並且記下 Com port 號碼
  * 在 MP Flight Data 頁面裡的右上方，鮑率設為 57600，然後選擇地面站無線電模組的 com port 號碼

  * 在 MP Flight 頁面內，按下 Ctrl + A 開啟無線電設置視窗

  * 點擊 Load Settings (從"地面站"無線電模組)

  * 在 Mission Planner 無線電設置視窗，(MP)檢查 Advanced Options box

  * 如果加載的數值與上述建議的設置不同，請再做一次，然後再點擊 Save

### 連接 3DR 無線電模組 ###

重要備註: **當你的 APM 2 已經接上 USB 時你就無法再連接無線電模組(他們共享相同的序列埠)。**在使用無線模組前請確你的 APM 2 沒有接上 USB 電纜線。


你需要2個 3DR 無線電模塊，一個是放在飛機上，另一個在你的地面站。

如果你看到下面的圖片你會看到有些無線電模塊有 USB 連接器，這是為了要與你的地面站連接。

看到下面的圖片你會發現有些無線電模組有 USB 連接器，讓它可以很容易的連接到你的地面站。它用了一個 D2XX FTDI 的驅動IC，你可以在[這裡](http://www.ftdichip.com/Drivers/D2XX.htm)取得。Windows 7 已經內建驅動，如果你是使用 Windows XP 或較舊的版本磺需要自行安裝。

在飛機端有一個 FTDI 6 Pin 連接器，可以讓它直接連接至你的 APM 遙測通訊埠，空中模組連接至 APM 2 的狀況如下圖：

## APM 2.5 專用 ##

使用內附的電纜線

![http://wiki.ardupilot-mega.googlecode.com/git/images/telemcable.jpg](http://wiki.ardupilot-mega.googlecode.com/git/images/telemcable.jpg)

將它插到 APM 2.5 的遙測通訊埠而 3DR radio 這邊，紅色的線接上 +5v 的腳位而最外側黑色線接至 GND :

![http://wiki.ardupilot-mega.googlecode.com/git/images/apm25telem.jpg](http://wiki.ardupilot-mega.googlecode.com/git/images/apm25telem.jpg)


## APM 2.0 專用 ##

![http://wiki.ardupilot-mega.googlecode.com/git/images/APM2/telemtry.jpg](http://wiki.ardupilot-mega.googlecode.com/git/images/APM2/telemtry.jpg)

![http://wiki.ardupilot-mega.googlecode.com/git/images/3drradio.jpg](http://wiki.ardupilot-mega.googlecode.com/git/images/3drradio.jpg)

無線模組的預設序列埠鮑率為 57600，這個鮑率是 APM 遙測模組的預設值，

但是你可以將它變更為任何你想要的鮑率，也可以使用 AT 命令來設定它，或者使用 APM Mission Planner 的無線設介面，也可使用[3DR Radio Configuration Utility](http://vps.oborne.me/3drradioconfig.zip)。


### LED 狀態說明 ###

3DR 無線模組有 2 個狀態 LED，一個紅色一個綠色。這兩個不同狀態的 LED 代表的意思如下：

  * 綠色 LED 閃爍 - 搜尋另一個無線電
  * 綠色 LED 常亮 - 與其他無線電建立鏈接
  * 紅色 LED 閃爍 - 傳輸資料
  * 紅色 LED 常亮 - 處於韌體更新模式


### 使用 Mission Planner 來設置無線模組 ###

最新版本的 APM Mission Planner 有支援 3DR 無線電，只需要透過簡單的圖形用戶界面就可以輕鬆設置。

3DR 無線使用了一個簡單的人機介面。在 Mission Planner (右上角)中選擇已經連接至地面站的 3DR 無線電序列埠，鮑率請選擇 57K。按下 Control-A，就會開啟一個視窗。點擊"Load Settings"，它的數據類似下圖所示(如果遠端無線電也有通電就會顯示它的設置只會，並連接 APM 目前運作的！ArduPlane 或！ArduCopter 代碼)。

![http://wiki.ardupilot-mega.googlecode.com/git/images/3DRadio/Screenshot-3DRradio.png](http://wiki.ardupilot-mega.googlecode.com/git/images/3DRadio/Screenshot-3DRradio.png)

推薦大多數用戶使用這個配置方法。


#### 序列及空中頻寬的'1 byte 格式' ####

SERIAL\_SPEED 及 AIR\_SPEED 參數與 APM SERIAL3\_SPEED EEPROM 參數是使用相同的格式。

頻寬的單位是取整數位的 kbps。所以 '9' 就是 9600 baud, '38' 是 38400, '115' 是 115200 等等。


### 選擇空中資料傳輸速率 ###

AIR\_SPEED 是無線電模組控制傳輸速率的關鍵參數。

預設為 64(是指 64kbps)使用全向天線的傳輸範圍可超過1公里。

將 AIR\_SPEED 設的愈小傳輸範圍就愈小，不過降低了 AIR\_SPEED 也會降低你可傳輸的資料量。

無線電韌體只支援13種空中資料傳輸速率，有2, 4, 8, 16, 19, 24, 32, 48, 64, 96, 128, 192 及 250。

如果你的無線運用因為一些原因需要使用不同的速率，我們可能會增加至註冊表。

如果你選擇了一個未支援的速率，程式就會選擇下一個最高的速率。

空中資料速率選擇，將取決於以下幾個因素

  * 什麼樣的範圍是你需要的
  * 什麼樣的速率是你要傳輸的
  * 你主要傳輸是否為同一個方向，或者任何方向都有可能
  * 你是否有 ECC enabled
  * 你的 APM firmware 是否有自動化的流量控制

在大部份的遙測應用你主要都是從飛機到地面站集中在一個方向發送數據。

大多數的人由飛機發送至地面站的數據量很小，只有偶爾控制封包加上飛機是否存活的封包。

如果你是使用遊戲遙桿操控你的飛機，你就會地面站送出很多的數據至飛機，在這種狀況就要找出一個較高的 AIR\_SPEED，雖然你的範圍將會減少。

ECC 參數會使得傳輸速率有很大的不同，可支援一個已經給定的 AIR\_SPEED。

如果把 ECC 設為 0，就不會發出任何的錯誤修正資訊，無線電使用一個簡單的16 Bit CRC 來定義傳輸錯誤。

在這種情況下，無線電所支援的數據傳輸在一個方向下大約是90%的 AIR\_SPEED。

如果你開啟 ECC(強烈建議)，傳輸速率就會被減半。

ECC 系統會由無線電送出兩倍的數據。

但這是值得的，錯誤率將會急劇下降，在較長的範圍時可能會得到一個更加可靠的連接。

如果你有最新版本的 APM 韌體(ArduPlane 2.33 或以上，或者 ArduCopter 2.54 或以上)，APM 將會自動偵測對應遙測無線電模組的速率，並透過 MAVLink 無線數據包將數據注入 MAVLink 數據流皆是經由這個韌體。

這樣就可以允許你'超額定義'連結，透過設置 SERIAL\_SPEED 會大於無線電實際上可以處理的。

其他製造商在選用數據傳輸速率大多是用 TDM '同步時間'。

這兩種無線電都需要使用彼此跳頻的模式工作。

當迅速改變傳輸通道時它們會緩慢的改變接收通道。

這個與其它無線電同步的程序在較高的數據傳輸速率只需要短短幾秒鐘，但使用較低的傳輸速率則較慢。

對於大多數業餘無人機應用通常將 AIR\_SPEED 預設為 64，再開啟 ECC 的功能就已經很好了。


### 錯誤修正器 ###

如上所述，如果你的 ECC 參數設置為1，無線電就會支援 12/24 格雷錯誤糾正代碼，。

這意謂著每 12 位元的資料無線電就會送出 24 位元，位元計算是利用格雷代碼參照表。

在接收端的過程是相反的，在每12位元發送允許無線電校正位元有3位元的錯誤(即25％錯誤率)。

ECC選項的缺點是，它的可用頻寬會減半，但在大多數的狀況它是值得的，你可以維持可靠的連結有較長的範圍。

在串流中你也是會收到一些'雜訊'。


### MAVLink 框架 ###

如果你把 MAVLINK 的選項設為 1，無線電將會處於'MAVLink 框架'下。

MAVLink 協定是由 APM 遙測數據傳輸到地面站。

當使用 MAVLink 框架，無線電將會盡力配合使用 MAVLink 封包下的無線電封包。

這個意思是如果封包遣失了，你的接收端不用結束另一半 MAVLink 封包 。

這部分封包在地面站控制台上會出現線性雜訊。

無線電韌體為了最好的效率將試著把多個 MAVLink 封包融入至一個無線電封包。

最高的無線電封包大小為 252 bytes。

無線電的韌體支援 MAVLink 0.9 及 MAVLink 1.0 的傳輸格式。


### MAVLink 回報 ###

如果你把 MAVLINK 設為 1，無線電韌體也會去尋找序列埠發出的 MAVLink HEARTBEAT 訊息。

當它收到 HEARTBEAT 的訊息它就會知道 MAVLink 協定正在使用中，它將開始注入 MAVLink 無線電狀態的封包到的串流。

無線電封包含 RSSI (Received Signal Strength Indicator) 層兩端連接的相關訊息，當通訊品質不佳時允許地面站或飛機採取動作。

無線電封也包含了錯誤率的相關資訊，以及序列傳輸緩衝區是否足夠(百分比)。

最新版本的 APM 韌體可以使用這個資訊來自動地配接遙測串流速率至無線電能夠維持的資料速率。


### 功率等級 ###

你必須非常小心配置無線電，在操作時應遵照該國的法律權力限制。

預設的功率等級為 20 dBm 是美國及澳洲所核可的，超過 30 dbm 就需要在跳頻無線電頻率 915-928MHz LIPD 等級的執照。

所以只要你的天線低於 10 dBi 的增益，你應該就有符合 ISM 的規定。

無線電無法支持任意的功率級別。它只能支援下表中的功率級別


| **Power (dBm)** | **Power (milliWatts)** |
|:----------------|:-----------------------|
| 1               | 1.3                    |
| 2               | 1.6                    |
| 5               | 3.2                    |
| 8               | 6.3                    |
| 11              | 12.5                   |
| 14              | 25                     |
| 17              | 50                     |
| 20              | 100                    |

如果你選擇一個不支援的功率級別無線電，將選擇從上述表中的下一個最高功率級別。

請仔細的檢查貴國 EIRP (Equivalent isotropically radiated power) 的功率限制，確保你考慮到的天線增益。

3DR 無線電是一個 DIY 的無線電零件，確保使用它是符合地方性法規是你的責任。

例如，如果你的地方性法規允許 30dBm (1W) EIRP 的最大值，如果你使用的發送增益是 12dB 的傳送增益，天線的增益是 3dBi，你的 TXPOWER 最大只能設定為 14。

如果你不知道如何校驗，我們為你做了一個指南: [認識 dB、Watts 及 dBm](http://code.google.com/p/ardupilot-mega/wiki/db_watt_dbm)。


---


### 使用 AT 命令設定 ###

3DR 無線電支援變種的 Hayes 'AT' 數據機配置命令。

如果你的串行控制台使用目前串列鮑率與 3DR 無線電連接，你可以輸入'+++'告知無線電進入 AT 命令模式。

為了防止數據被一連串命令所影響因此有一個防護時間，所以請確認你在序列連接時在一秒前沒有輸入任何的字元及在你輸入之後也是。

當你進入 AT 命令模式你會從無線電收到'OK'的提示，它會由其他的無線電發出停止傳送資料。

一旦進入 AT 模式，你可以給無線電'AT'命令來控制本地端的無線電，或者(如果已成功連接)你可以使用'RT'命令來控制遠端的無線電。

可用 AT 命令如下：

  * ATI - 顯示無線電版本
  * ATI2 - 顯示機板型態
  * ATI3 - 顯示機板頻率
  * ATI4 - 顯示機板版本
  * ATI5 - 顯示所有使用者設定的 EEPROM 參數
  * ATI6 - 顯示 TDM timing 回報
  * ATI7 - 顯示 RSSI 訊號回報
  * ATO - 離開 AT 命令模式
  * ATSn? - 顯示無線電參數編號 'n'
  * ATSn=X - 設定無線電參數編號 'n' 到 'X'
  * ATZ - 重啟無線電
  * AT&W - 寫入目前參數值至 EEPROM
  * AT&F - 重置所有參數至出廠預設值
  * AT&T=RSSI - 開啟 RSSI 偵錯回報
  * AT&T=TDM - 開啟 TDM 偵錯回報
  * AT&T - 關閉偵錯回報

所有這些命令，除了ATO，大多可用於連接的遠程無線電取代“AT”與“RT”。

最有用的命令可能是“ATI5”，它可以顯示所有用戶可設置 EEPROM 參數。

這將產生一個像這樣的報告：


```
 S0: FORMAT=22
 S1: SERIAL_SPEED=57
 S2: AIR_SPEED=64
 S3: NETID=25
 S4: TXPOWER=20
 S5: ECC=1
 S6: MAVLINK=1
 S7: OPPRESEND=1
 S8: MIN_FREQ=915000
 S9: MAX_FREQ=928000
 S10: NUM_CHANNELS=50
 S11: DUTY_CYCLE=100
 S12: LBT_RSSI=0
```


如果你想要變更參數，請於第一行的 S 暫存器設置。為了示範，這邊把傳輸功率設為 10dBm，使用'ATS4=10'。

大多數的參數會在下次重啟時生效。所以設置完你想要的參數後請使用'AT&W'將它們寫入至EPROM，重啟請使用'ATZ'。

唯一的例外是發射功率，設置完後會立即改變(在重啟後會恢復到舊的設定值除非你使用 AT&W)。


各參數的定義如下:

  * FORMAT - EEPROM 的版本格式。不要變更它!
  * SERIAL\_SPEED - 序列速度，單位是'位元組'(請見下文)
  * AIR\_SPEED - 空中資料速率，單位是'位元組'
  * NETID - 網路 ID。你要互相溝通的無線電模式皆需相同
  * TXPOWER - 傳輸功率單位 dBm。最大值為 20dBm
  * ECC - 開啟/關閉 golay 錯誤修正代碼
  * MAVLINK - 開啟/關閉 MAVLink 框架及回報
  * MIN\_FREQ - 最小頻率，單位是 kHz
  * MAX\_FREQ - 最大頻率，單位是 kHz
  * NUM\_CHANNELS - 跳頻頻道數
  * DUTY\_CYCLE - 允許發送的時間百分比
  * LBT\_RSSI - Listen Before Talk 條件(請見下文)


兩個無線電通訊必須要有相同的：

  * 無線電韌體版本
  * the AIR\_SPEED
  * the MIN\_FREQ
  * the MAX\_FREQ
  * the NUM\_CHANNELS
  * the NETID
  * ECC 設定
  * LBT\_RSSI 設定


在鏈接的兩端，其他設置可能會有所不同，雖然你通常會把兩邊設置為相同。


### 支援不同的國家/地區 ###

找出哪些國家或地區的當地法規的頻率是非常重要的，跳頻通道、功率等級，3DR 無線電可以正確配置並符合您的地方法規。

這裡有些通用資料可以幫助你了解。


| **Region** | **Radio Model** | **Settings** | **Standard** |
|:-----------|:----------------|:-------------|:-------------|
| USA        | 3DR 900         | MIN\_FREQ=902000 MAX\_FREQ=928000 NUM\_CHANNELS=50 | FCC 15.247   |
| Canada     | 3DR 900         | MIN\_FREQ=902000 MAX\_FREQ=928000 NUM\_CHANNELS=50 | RSS-210 Annex 8.1 |
| Australia  | 3DR 900         | MIN\_FREQ=915000 MAX\_FREQ=928000 NUM\_CHANNELS>=20 | LIPD-2000 item 52 |
| Australia  | 3DR 433         | MIN\_FREQ=433050 MAX\_FREQ=434790 TXPOWER<=14 | LIPD-2000 item 17 |
| Europe (most countries) | 3DR 433         | MIN\_FREQ=434040 MAX\_FREQ=434790 TXPOWER<=8 NUM\_CHANNELS>=30 | ETSI EN300 220 7.2.3 |
| Europe (most countries) | 3DR 433         | MIN\_FREQ=433050 MAX\_FREQ=434790 TXPOWER<=8 DUTY\_CYCLE=10 | ETSI EN300 220 7.2.3 |
| United Kingdom | 3DR 433         | MIN\_FREQ=433050 MAX\_FREQ=434790 TXPOWER<=8 DUTY\_CYCLE=10 | [IR2030/1/10](http://stakeholders.ofcom.org.uk/binaries/spectrum/spectrum-policy-area/spectrum-management/research-guidelines-tech-info/interface-requirements/IR_2030.pdf) |
| New Zealand | 3DR 900         | MIN\_FREQ=921000 MAX\_FREQ=928000 | Notice 2007, Schedule 1 |
| New Zealand | 3DR 433         | MIN\_FREQ=433050 MAX\_FREQ=434790 | Notice 2007, Schedule 1  |
| Brazil     | 3DR 433         | MIN\_FREQ=433000 MAX\_FREQ=435000 TXPOWER<=8 | [Resolução ANATEL nº506/2008](http://www.anatel.gov.br/Portal/verificaDocumentos/documento.asp?numeroPublicacao=252315&assuntoPublicacao=null&caminhoRel=In%EDcio-Biblioteca-Apresenta%E7%E3o&filtro=1&documentoPath=252315.pdf) |
| Brazil     | 3DR 900         | MIN\_FREQ=902000 MAX\_FREQ=907500 NUM\_CHANNELS>=11 | Resolução ANATEL nº506/2008 |
| Brazil     | 3DR 900         | MIN\_FREQ=915000 MAX\_FREQ=928000 NUM\_CHANNELS>=26 | Resolução ANATEL nº506/2008 |
| Argentina  | 3DR 900         | MIN\_FREQ=902000 MAX\_FREQ=928000 | [Comisión Nacional de Comunicaciones](http://www.cnc.gov.ar/infotecnica/espectro/uso/destacados01.asp) |
| South Africa | 3DR 433         | MIN\_FREQ=433050 MAX\_FREQ=434790 TXPOWER<=10mW | 2008 RR 5.138, Government Gazette No 31127,<br> Notice No 713 of 2008 and Government Gazette No 31290,<br> Notice No 926 of 2008 refer </tbody></table>

我們很高興這表格有越來越多的國家！請這個訊息張貼在論壇上，這個連結代表適用的法規和信息。此外，請指出，現有的表格中的任何錯誤。

請注意，上述表是大多數的使用者無需任何特殊的許可。如果你的應用程序需要特定的許可證或一個業餘牌照，那麼你就應該知道什麼規則是適用於您。

最後，您有責任遵守。3DR 無線電模組是個“DIY”無線電零件，你需要確保你的使用是符合當地法規。請仔細檢查您的地方性法規。


### 可用頻率範圍 ###

下表可能有幫助你使用符合當地的無線電法規的方式將兩個無線電模組連接起來

| **無線電模組** | **最小頻率 (MHz)** | **最小頻率 (MHz)** |
|:----------|:---------------|:---------------|
| 3DR 433   | 414.0          | 454.0          |
| 3DR 900   | 895.0          | 935.0          |


### Duty Cycle(工作週期)設置 ###

大多數的使用者會將 DUTY\_CYCLE 設為 100。DUTY\_CYCLE 就是最大無線電傳輸封包的時間百分比。

duty cycle 被列入的原因是世界上有些地區允許更高的發射功率或更多的頻率，如果你的 duty cycle 在某個數值以下都是可以被使用的。

所以例如在歐洲，如果你的 duty cycle 不超過 10%，你可以使用 433 的頻寬傳輸。

當您的 duty cycle 設定低於 100%，你可用頻寬將會減少，所以你會發現最好的運作方式是遙測模組使用較高的鮑率。

由 APM 上使用 10% 的 duty cycle 來取得良好的遙測仍然相當實用，但遙測模組的通訊任務相當'bursty(叢發性)'，所以平均傳輸時間普遍不高。

例如你把 AIR\_SPEED 設為 128 啟動 ECC 並且 DUTY\_CYCLE 設為 10，就可以很容易的接收到所有的 2HZ 的遙測訊號。

你只要將 DUTY\_CYCLE 設置為 0 ，就可以把無線電設置為接收端。運作時最好可以將 NUM\_CHANNELS 設成較低的號碼，否則，時序同步(clock synchronisation)會變得很差。


### Listen Before Talk (LBT) ###

3DR無線電模組可以實現'listen before talk' (LBT)功能，使其能夠符合更廣泛的區域監管要求。LBT的是一個無線電需要聽一段時間，看看是否有其他無線電信號，然後才允許傳輸的系統。你的無線電經過非零 LBT\_RSSI 的數值會變得更加“polite(井然有序)”，等到其他人已停止傳輸自己才會開軩傳輸。

要在無線電模組啟用 LBT 你必須先設置 LBT\_RSSI 參數。無線電會認為這個跡象的信號強度，表示該通道是被佔用的。
如果你將 LBT\_RSSI 設為 0，LBT 就是關閉。

最小值不得為 0，我們設 25，表示在接收靈敏度(-121 dBm)以上幾dB。要設置 LBT\_RSSI 你需要知道 LBT 功能的無線電地方法規的訊號等級。
每個增加量超過 25 的 LBT\_RSSI 等於 0.5dB 以上的無線電接收端靈敏度。所以，如果你設置 LBT\_RSSI 為 40，無線電就會考慮通道是空的，但這個要在訊號強度低於 7.5dB 的接收端靈敏度。

另外，您可以使用這個公式取得 dBm 的接收信號強度：
```
  signal_dBm = (RSSI / 1.9) - 127
```

這個公式是近似值，但已經相當接近。更精確的圖 請見 Si1000 數據表。

需要查詢您當地的監管要求，看看你應該使用什麼樣的 LBT\_RSSI 設置。

LBT 在 3DR 無線電的實行，是使用 5ms 的最低接收時間，加上隨機接收時間與歐洲 9.2.2.2 的規則相同。

請注意，在許多地區，您需要結合 AFA(Adaptive Frequency Agility)來執行 LBT。3DR 無線電已實現 AFA 只要你將 NUM\_CHANNELS 的設置大於 1。


### 技術祥解 ###

在進行評估時，如果這個無線電符合您的地方性法規，可能有助於知道它使用什麼技術。

韌體使用同步分時多工(time division multiplexing, TDM)來執行跳頻式展頻(frequency hopping spread spectrum, FHSS)。

具體來說，無線電將 MIN\_FREQ+delta 和 MAX\_FREQ-delta 之間的頻率範圍劃分成 NUM\_CHANNELS 的通道。'delta'表示一個保護範圍，以確保我們保持並遠離允許帶的邊緣。保護範圍設置為通道寬度的一半。通道寬度定義為：
```
  channel_width = (MAX_FREQ - MIN_FREQ) / (NUM_CHANNELS+2)
```

另外，無線電會使用一個以 NETID 為基礎的隨機種子，扭曲基頻增加到一個以上的通道。這意味著兩個無線電使用不同 NETID 號碼，頻率就會略有不同。

無線電使用 GFSK (Gaussian Frequency Shift Keying)對某一特定頻率的傳輸。

TDM 工作原理是把時間畫分成數個 16us 的片段(時槽)。時槽的最大停留時間在任何頻率下皆是 0.4s(這是為了符合美國法規)。TDM 演算法工作原理如下：

  * EEPROM的參數決定了一組 TDM 參數的設定，特別是發射窗口和靜止期，都是以16微秒為單位。你可以使用 ATI6 瀏覽結果。
  * 發射窗口縮放允許3個全尺寸封包被傳送
  * 對於給定的資料速率，靜止期等於兩倍的封包延遲。
  * 兩個無線電自動加入13位元的時槽信息到所有封包來同步它們的時序。時槽的單位是 16us。
  * 每個無線在'轉換時'只會處於發射狀態。所以無線電取得一個發射窗口的時間值，然後只要不是無線電發射時就會有一個靜止期，接下來其他的無線電就會輪到它。我們絕對不會有無線電同時發射的狀態。
  * 發送通道會被組成基於 NETID 的隨機序列
  * 靜止期間，每一輪完整的 TDM，頻率會被變更為下一個通道的兩倍
  * 當沒有發射時，資料會在序列埠 2048 byte 的緩衝區進行緩衝
  * 為了預防緩衝區太多資料(增加延遲和過載的風險)無線電連接的設備會發送緩衝區是否已滿的資訊。APM 的代碼配置少量的遙測速率來保持緩衝的數據量是合理的。
  * TDM 演算法也具有自適性，意思是說，當輪到無線電 A 傳送，它可以送出一個小訊息給無線電 B 說"我現在不需要送什麼，你可以休息片刻"。這就是非對稱負載自動平衡的連接。
  * 在另一個無線電初始搜索的期間，任何時間的連接都是不存在的，無線電進入模式後，它們移動接收頻率非常緩慢，但是會用正常的速率移動發射頻率。這使得兩個無線電找到彼此的初始時序同步。這需要多長時間取決於通道的數目、空中數據傳輸速率和封包遣失率。


在某些地區，你可能需要知道每個通道內的輻射能量分佈。這取決於許多因素，但主要是用於 GFSK 調製頻率偏差。下列公式會給你一個頻率偏差估計：

```
   frequency_deviation = air_data_rate * 1.2
   min freq deviation = 40
   max freq deviation = 159
```

其中 frequency\_deviation 的單位是 kHz，air\_data\_rate 的是每秒 1K 位元。


### 很長的範圍請使用雙向放大器 ###

3DR 無線電可以結合雙向放大器，以擴大覆蓋範圍到很長的距離。

[Shireen](https://www.shireeninc.com/)有很多成功的測試放大器。

Shireen 很好心捐出一個 900MHz 的放大器，讓我們可以測試 900MHz 的 3DR 無線電。

![http://wiki.ardupilot-mega.googlecode.com/git/images/3DRadio/Shireen_amplifier.jpg](http://wiki.ardupilot-mega.googlecode.com/git/images/3DRadio/Shireen_amplifier.jpg)


該放大器增加 12dB 發射增益和 18dB 的接收增益，當無線電啟動和停止傳輸時，會在發送和接收模式之間自動切換 。

它可以運行在 UBEC 的5V，或者可以使用2S或3S 的鋰電池接上內建的開關穩壓器。

我們在澳大利亞的坎培拉，兩山之間約7.6公里鏈接測試放大器。

一端我們使用簡單的線型天線，另一端使用 eBay 上便宜的 3.5dBi omni 天線，外加一台 Shireen 放大器。

這是試驗平台沒有加上放大器

![http://wiki.ardupilot-mega.googlecode.com/git/images/3DRadio/TestRig.jpg](http://wiki.ardupilot-mega.googlecode.com/git/images/3DRadio/TestRig.jpg)

使用以下的設定：

```
 S0: FORMAT=22
 S1: SERIAL_SPEED=9
 S2: AIR_SPEED=24
 S3: NETID=25
 S4: TXPOWER=14
 S5: ECC=1
 S6: MAVLINK=1
 S7: OPPRESEND=1
 S8: MIN_FREQ=915000
 S9: MAX_FREQ=928000
 S10: NUM_CHANNELS=50
```

我們發現7.6 km 的範圍通訊的效果還不錯。

然後我們逐步降低兩端鏈結的發射功率，以量測“衰落餘量”，這使我們能夠估計在滿功率無線電能傳輸多遠。

進行測後，我們發現約 12dB 時兩端的訊號會有衰減，這意味著無線電應該能夠維持在約4倍的範圍內。

請注意，如果你使用一個放大器(或高增益天線)，你需要非常小心，不要超過您的當地法規所允許的 EIRP 等級。


### 監控連線品質 ###

如果你的地面站有支援 MAVLink，飛行時你可以使用它來監控 3DR 無線電連線品質。RADIO.rssi 及 RADIO.remrssi 這兩個是關鍵參數。

第一個是 RSSI (信號強度)等級是本地端接收無線電的信號強度。remrssi 參數則是遠端接收無線電的 RSSI。

這裡是典型的 RSSI，在我們飛場的飛行圖表。

![http://wiki.ardupilot-mega.googlecode.com/git/images/3DRadio/rssi-distance.png](http://wiki.ardupilot-mega.googlecode.com/git/images/3DRadio/rssi-distance.png)

RSSI 規模約為 1.9倍 dBm 的信號強度，再加上一個偏移量。

想要確切對應出 RSSI 及 dBm 間接收的信號強度，請見 Si1000 的資料表，或使用此近似公式

```
  signal_dBm = (RSSI / 1.9) - 127
```

在這次飛行 RSSI 的變化這麼大，原因是當飛機在橫滾轉彎時，因為我在飛機使用一個簡單的線型天線，造成信號衰減。

這次飛行 RSSI 值已經相當足夠，連線的品質也是表現的相當優秀，整個飛行也都是使用預設的無線電參數。


### 傳輸的範圍有多少？ ###

大多數人最常問的問題就是無線電的範圍可以多遠。
這也是一個最難回答的問題，因為它取決於許多因素。

我們已經做了很多評估，使用無線電實際範圍的小型全向天線，不使用放大器試飛。

下面是一個典型的結果：

![http://wiki.ardupilot-mega.googlecode.com/git/images/3DRadio/3DR-915-txpower2-64kbps-ECC.png](http://wiki.ardupilot-mega.googlecode.com/git/images/3DRadio/3DR-915-txpower2-64kbps-ECC.png)

在這個測試中 3DR 900 無線電模組使用預設的參數，除了 TXPOWER 設定為 2dBm，這表示他們發射的最大功率為 1.6%。

從理論上來說，每增加 6dB 發射功率無線電範圍就會增加一倍，所以本次測試所取得的範圍，應該是無線電可實現空中速率 64kbps 的 1/8。

這就是為什麼上圖顯示的距離(單位米)要\*8。
這是裝在 SkyFun 模組，我會將它保持在視距以內，這就是為什麼我做了減少傳輸功率，而不是長途飛行的測試。

無線電在這次整個飛行過程都保持完美連線，所以我們有信心，這些無線電將可以實踐數公里的通訊範圍。

在這次測試中，我的 SkyFun 使用線型天線，地面站則用廉價的 eBay 3.5dBi 天線。

當然，如果我失去了空中數據傳輸速率，範圍將會相當的好。
我覺得 64kbps 對一般用途而言良率還不錯，但如果想測試較長的範圍，我會傾向使用 24 kbps 的。

其他用戶也證實了這些無線電的範圍。例如，我送出的 log 顯示距離地面站超過 4.5km 的飛行還是有一個良好的連線，全程皆使用 3DR 900 的預設無線電設置。
飛機上使用小型全向天線，地面站使用一個 8dB 平板天線。在日誌中訊號的等級，表明它可能已經有幾分進一步。

### 分析範圍問題 ###

如果你發現通訊範圍小於你所預期的，你就要使用飛行時的圖表分析雜訊的問題在哪。

影響通訊範圍最常見的問題就是雜訊。雜訊是最令人困擾的無線電波，它在相同頻率範圍中會干擾你正在使用的無線電。3DR radios 有內建遙測日誌檔可以幫助你分析判斷雜訊的來源。

有3個主要類型的雜訊可能會影響到你的3DR radios

  * 來自於飛機上電子設備的雜訊(例如馬達、ESC、APM 等等)
  * 來自於地面站電腦的雜訊，尤其是它的 USB 埠
  * 來自於附近其他人正在作業的無線電雜訊，有可能和你的 3DR radios 相同頻率。

要知道有什麼樣的雜訊你可以這麼做，開啟 Mission Planner 選擇"telemetry logs"頁面，然後再選擇"Tlog>Kml or Graph"。
當 Windows 彈出選擇 "Graph Log" 的訊息，請從測試飛行的無線電中選擇一個日誌檔。等待一段時間會載入日誌檔，然後會看到日誌檔會有以下資訊：
  * rssi
  * remrssi
  * noise
  * remnoise
將這4個數值全部放在同一個圖框。 你最終將會得到這樣一個畫面:

![http://wiki.ardupilot-mega.googlecode.com/git/images/3DRadio/diag-range-graph.png](http://wiki.ardupilot-mega.googlecode.com/git/images/3DRadio/diag-range-graph.png)

這個圖框會讓你知道四件事情:
  * 在地面上正在接收的信號量
  * 在飛行器上正在接收的信號量
  * 在地面上正在接收的雜訊量
  * 在飛行器上正在接收的雜訊量

要得到最佳的通訊範圍，你要讓兩個雜訊線最低，兩個信號線最高。在上圖(這張圖是從我的 SkyFun 上的一對 3DR-433 radios 取得)你可以看到飛機上的雜訊線高於地面的雜訊線。
也請注意飛行開始時(在我啟動馬達前)飛機上的雜訊線是較低的，在我啟動馬達之後就開始上升。意思是說雜訊是由馬達產生。如果我要取得更大的通訊範圍我會需要讓無線遠離馬達及ESC。

使用 3DR-433 時最常的雜訊來源是來自於地面站的 USB 埠。表示會有較高的無線電雜訊值。如果你發生這種狀況，你可以試著使用不同的 USB 電纜線或者不同的筆記型電腦。
你也可以嘗試在無線電與筆記型電腦間使用 USB 集線器。

如果 'rssi' 及 'noise' 這兩條線在圖上交會你將會失去連結。如果要判斷你的範圍，一個粗略的經驗法則是減去'rssi'和'noise'的數字，然後除以2。
這會告訴你單位為分貝(decibels)的衰落餘量(ade margin)。每 6dB 的衰落餘量範圍就會增加1倍。所以如果你有 18dB 的衰落餘量，你的範圍的測得餘量大約是8倍。

範圍問題的另一個主要來源是天線的位置。地面站的天線應該是沒有任何阻礙，並且離地數公尺。你也許還需要用一個腳架來支稱讓它保持最好的通訊範圍。

### 升級你的無線模組韌體 ###

3DR 無線電模組的韌體是開源的，新的功能是可以依需求加入。你應該定期檢查無線電最新版本的韌體。

最容易的方式是使用 APM Mission Planner。進入 3DR 無線電的設置畫面，按下'Upload Firmware'的按鈕。

在升級完後請仔細的檢查所有的設定。
韌體的更新也許會變更 EEPROM 格式所以可能會把你的設定值變更預設值。

我們也鼓勵你參與開發韌體。先來看看[firmware 源碼](https://github.com/tridge/SiK)一起貢獻補強吧！

### 強制 bootloader 模式 ###

如果你想要讓無線電保持在最新的狀態，你要先將無線電強制調到 bootloader 模式，你才可以透過 Mission Planner 燒錄最新的韌體。

一般韌體上傳的方式是將無線模組連上 planner，送出 AT&UPDATE 的命令將無線模調到 bootloader 模式，就可以接受新的韌體版本。

唯一的方式是讓 planner 送出 AT 命令至無線模組。

如果無法送出 AT 命令，你可以在無線模組上電的時候透過短路 CTS 及 GROUND 腳位來強制進入 bootloader 模式。
進入 bootloader 模式時紅色的 LED 會亮起來。

空中端的 CTS 及 GROUND 腳位很好找，它們會標在板子的背面(它們是 FTDI 連接器的其中兩個腳位)。

上面的 USB 無線模組標示的並不明顯，所以下圖可以幫助你更容易找到它們：

![http://wiki.ardupilot-mega.googlecode.com/git/images/3DRadio/force-bootloader.jpg](http://wiki.ardupilot-mega.googlecode.com/git/images/3DRadio/force-bootloader.jpg)

你就可以進入 bootloader 模式後，你應該就可以燒錄新版韌體。

### 3DR 無線模組論譠 ###

參與發展或者調試無線電的最佳地方就是[3DR 無線電論壇](http://diydrones.com/forum/categories/3dr-radios/listForCategory)。參加論壇讓無線電模組更強大！