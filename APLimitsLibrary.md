#summary Documentation for the AP\_Limits Library

# 簡介 #

AP\_Limits 是從 Andrew Tridgell 編寫的 geofence(電子圍欄) 發展的 ArduPilot library。AP\_Limits 以模組化方式實現電子圍欄以及其他的“限制功能”。

## 快速導覽 ##

> 這裡有個範例：

  * 電子圍欄: 不要讓我的飛機與起飛的地點超過 50 米。

| 參數 | 數值 | 定義 |
|:---|:---|:---|
| LIM\_FNC\_ON | 1  | 開啟電子圍欄 |
| LIM\_FNC\_SMPL | 1  | 簡單模式 |
| LIM\_FNC\_RAD | 50 |  半徑為 50 米 |
| LIM\_ENABLED | 1  | 開啟功能 |


  * 高度限制: 不要讓我的直升機高度超過 80 米

| 參數 | 數值 | 定義 |
|:---|:---|:---|
| LIM\_ALT\_ON | 1  | 開啟高度限制功能 |
| LIM\_ALT\_MAX | 80 | 最高的高度為 80 米 |
| LIM\_ENABLED | 1  | 開啟功能 |


  * GPS 鎖定 : 不要讓我在沒有 GPS 的狀態下降落。

| 參數 | 數值 | 定義 |
|:---|:---|:---|
| LIM\_GPSLCK\_ON | 1  | 開啟 GPS 鎖定功能 |
| LIM\_GPSLCK\_REQ | 1  | 無 GPS 不可激活馬達 |
| LIM\_ENABLED | 1  | 開啟功能 |


AP\_Limits library  的設計是利用不同類型的限制來做簡單擴展。

# 使用限制的功能 #

AP\_Limits 有許多不同的模組。這意謂著你可以在任何時間開啟及關閉系統部份的功能。高度、電子圍欄及其他限制可以混合及相互配合使用，你可以開啟及關閉任何組合的限制。

"主要"的開啟/關閉開關在 LIM\_ENABLED 參數。設為 1 時將會開啟系統的限制功能。

每個 AP\_Limit _module_ 也有相同的開啟/關閉功能，例如 LIM\_FNC\_ON、LIM\_ALT\_ON 等等。

## 電子圍欄 ##

> AP\_Limits 的電子圍欄模組允許你為你的飛行器建立一個封閉區域的虛擬圍欄。如果你的飛行器超過這個區域，不管是什麼原因 (不管飛行員是否介入)，高度限制模組狀會馬上被觸發。你可以在使用電子圍欄時可以結合高度模組功能，或者也可以不使用高度限制。沒有高度限制，圍欄就沒有"天花板"或"地板"。

AP\_Limits 電子圍欄有簡單及複雜兩種圍欄型態。

_Simple_ mode，是一個以發射地點為半徑的圓形圍欄 (發射地點會成為圓形的中心點)。

_Complex_ mode，是一個最高可以有19個點組成的圍欄，但這要是一個封閉多邊形並且要將一個以上的點定義為"中心點"或者家的位置/返回位置。

如果要選擇簡單的圍欄，請將 LIM\_FNC\_SMPL 設為 1。如果要選擇複雜的模式，請將 LIM\_FNC\_SMPL 設為 0。

### 簡單模式的電子圍欄 ###

簡單模式的電子圍欄是一個以起飛點為中心點，半徑單位為米的圓圈。

LIM\_FNC\_RAD 請設定為你想要的半徑。

![http://wiki.ardupilot-mega.googlecode.com/git/images/AP_Limits/aplimits-geofence-simple.png](http://wiki.ardupilot-mega.googlecode.com/git/images/AP_Limits/aplimits-geofence-simple.png)

### 複雜的電子圍欄 ###

一個複雜的電子圍欄是多邊形的，定義為 1 到 N，還有一個返回點，當超出圍欄就會返回這個點(可設為"電子圍欄的中間位置")。

電子圍欄的航點會經由地面站軟體傳送至 APM 並且儲存於 EEPROM。

_註: 請閱讀 Mission Planner 電子圍欄設置說明_

![http://wiki.ardupilot-mega.googlecode.com/git/images/AP_Limits/aplimits-geofence-complex.png](http://wiki.ardupilot-mega.googlecode.com/git/images/AP_Limits/aplimits-geofence-complex.png)

## 高度限制 ##

AP\_Limits 高度限制模式可以為你的飛行器設定最低及/或最高的高度制。它通常與電子圍欄結合成為一個封閉的"箱子"。不管如果你也可以設置一個沒有高度限制的電子圍欄，或者說電子圍欄是可以沒有高度限制的。沒有一個電子圍欄，可以在沒有人工地平線的情況下把高度限制定義為空中的"層別"。

將 LIM\_ALT\_ON 設為 1 為開啟功能。

LIM\_ALT\_MIN 為最小高度，單位為米，由地面算起(落地時的高度 = 0)。如果你設置了一個最小高度(大於 0)，你必須使用遙測模組的命令或者 RC 通道開關啟動 AP\_Limits 然後你就會爬升至最小高度。
LIM\_ALT\_MAX 為最大高度，單位為米，由地面算起。

如果你設定 ALT\_MIN > 0 你就無法設定 ALT\_REQ(在 ALT\_MIN 以下你將無法激活馬達)。如果你已經把 ALT\_REQ 設為 0，在你第一次清除它\_之後_ALT\_MIN 才會開始運作(在你激活馬達時它將不會馬上被觸發，它會延遲觸發直到你清除 ALT\_MIN 以後)_

# 結合高度限制及簡單模式的電子圍欄 #

透過高度和電子圍欄模組的結合，你可以為你的飛機建立一個封閉的"盒子"。如果你違反任何一個限制，它就會觸發。如果回復違反限制後又違反另一個限制(例如：當你的飛機超過高度又跑出圍欄之外)，它將會再次觸發並且計算你所超出的秒數。

![http://wiki.ardupilot-mega.googlecode.com/git/images/AP_Limits/aplimits-altitude-and-geofence.png](http://wiki.ardupilot-mega.googlecode.com/git/images/AP_Limits/aplimits-altitude-and-geofence.png)


# 激活前的檢查清單 #

AP\_Limits 實行激活前的檢查清單。當飛行員準備起飛試圖激活馬達時，AP\_Limits 系統將會檢查是否有任何限制。這個功能是個選項，每個模組皆可以被開啟或關閉。意思是說有些模式是必要。如果模式是必要，AP\_Limits 會在起飛檢查它狀態。

## GPSLock ##

最簡單的 AP\_Limits 模式應該是 GPSLock。這個模式在起飛前需確認你已經有 GPS 訊號(GPS fix)。如果你起飛時沒有 GPS 訊號，你的飛行會無法 RTL，並且電子圍欄會無法運作。
把 LIM\_GPSLCK\_ON 及 LIM\_GPSLCK\_REQ 設為 1，你就可以啟動這個模式並且要預先激活這個功能。現在，如果你激活馬達而沒有 GPS 訊號，你將會由遙測模組得到一個"Limit Triggered"的提示訊息，並且飛行器將會無法激活。當然你可以改變設置並且無視這樣的警告，或者如果你想要飛行沒有 GPS 訊號，就關閉這個限制系統吧。

預先激活的功能在電子圍欄、或者高度限制中很重要。一般而言當限制已經開啟，在起飛時才做這個動作是很不好的。遵了要盡快讓飛行器處於一個安全的高度時，它將會試著\_回復\_因為限制的功能已經開啟，將會啟動 RTL 功能。在最壞的情況下，執行較差的系統，甚至可能起飛，因為它是低於最低高度。

底限是：

  * 起飛前，所有限制應該要很清楚 **如果你已經設定了電子圍欄，你應胲要\_包含\_起飛一起設定。如果你設置了最小高度，應該要大於起飛時的高度。**

把 LIM\_GPSLCK\_REQ、LIM\_FND\_REQ 及 LIM\_ALT\_REQ 設為 1，你要確認你不會因為觸發限制而不小心的起飛。

# 復原程序 #

當一個限制被觸發，AP\_Limits 將會立即開始\_復原程序_。_

在第一版的 AP\_Limits，只有一種復原模式，就是 Return-To-Launch(RTL 回到起飛點)。

只要限制被觸發，飛行器就會切換到起飛點/家的位置做為航點，並且切換至教練飛行模式。如果沒有設置高度限制，就會回到的 RTL 所設置的高度。

如果已經定義了最小及最大高度，回復的高度就會在它們之間。例如設置的高度為(min + (max-min)/2)，請確認飛行器是否回到高度限制的中間位置。為了確保安全操作，返回的高度以發射點來看不可小於4米(如果在這個高度以下，它將被設為4米)。

如果你想要飛機跑完航點後回到完整的 RTL，請將 LIM\_SAFETIME 設成較大的數字(30 秒或更多)就會允許你的飛機在還給你一個穩定模式控制之前回復到完整的模式。

如果你想要飛機的控制權盡可能的"馬上"還給你，可以將 LIM\_SAFETIME 設為 1(秒)。

# 參數定義 #

| 參數 | 單位 | 備註 |
|:---|:---|:---|
| LIM\_ENABLED | Boolean | Enable limits - Master ON/OFF |
| LIM\_DEBUG | Boolean | Send debug messages to the console and as MAVLink STATUSTEXT |
| LIM\_STATE | Integer | Internal State of AP\_Limits. See source code for details, do not set |
| LIM\_SAFETIME | Seconds | Seconds to wait before returning to STABILIZE |
| LIM\_GPSLCK\_ON | Boolean | Enable GPSLock module |
| LIM\_GPSLCK\_REQ | Boolean | Require GPSLock pre-arm check |
| LIM\_FNC\_ON | Boolean | Enable geofence module |
| LIM\_FNC\_REQ | Boolean | Require geofence pre-arm check |
| LIM\_FNC\_SMPL | Boolean | 1 = simple mode, 0 = complex mode|
| LIM\_FNC\_RAD | Meters |  Radius in meters, from launch location |
| LIM\_FNC\_TOT | Count | Number of fence points (set by GCS for complex fence, do not change) |
| LIM\_ALT\_ON | Boolean | Enable altitude module |
| LIM\_ALT\_REQ | Boolean | Require altitude pre-arm check |
| LIM\_ALT\_MIN | Meters | Min altitude in meters |
| LIM\_ALT\_MAX | Meters | Max altitude in meters |