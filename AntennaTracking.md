## 自動化地面追縱天線 ##

http://api.ning.com/files/CLn6cdxUhdPm8nxJuCkTd0tj9-5rIzALp1MnEFZR0XwjhUADZL5*u*WQa9PFB-01zZPuCYUa4phDLsGohYeD8A__/IMG_0415.JPG?width=750

### 什麼是自動追縱天線(Antenna Tracker, AT)? ###

AT 是一個可以追縱空中的飛機、直升機的地面系統。有許多方式可以達到 AT 的功能。

一種是利用雷達偵測高度、角度告訴 AT 飛機的位置，這個方式非常的昂貴而且 DIY 很難做到。

另一種方式就是利用飛機傳回來的訊號，比對 AT 上的電子接收器使用這些訊息就可以讓天線知道方向。這種方式所發出的訊號會比其他方式弱。

然而，另一種可行的解決辦法是買一個在 DIY 預算內的現成系統，但如果你使用這種花俏 AT 系統，那麼它通常是不與其他系統相容。這也可能是超出你的能力來修復或了解可能發生的任何錯誤。

這裡的[APM Mission Planner](http://code.google.com/p/ardupilot-mega/wiki/MPInstallation)(這是 DIYdrones 網站的其中一種地面站軟體)是目前為止較簡單的方式但是卻和其他方法一樣有效。

從 APM2 上的 Global Positioning System (GPS) 就可以追蹤到你的飛機在哪裡，它只是需要這些數據，並塞給你的 AT。只要你的 GPS 可以運作就可以立即追縱!這個建立方式是使用 APM2 與 Mission Planner (MP)結合，但是原來的 APM 也一樣可以用這種方式運作。不管你是使用 APM 1 或 2 AT 的數據來源皆是由 MP 而來，而 MP 也是藉由[遙測模組](https://store.diydrones.com/category_s/13.htm)連結飛機上的資料，所以使用時必須將遙測模組接上。

#### 需要什麼零件 ####

這些是建立追縱天線的主要零件清單。這邊並不包含螺絲、膠水之類的東西。請了解這些零件的作用非常重要的，所以請閱讀這些連結的範例說明。

  * 主體支架，看看是要自己做或是買現成的
  * 天線
  * 2個伺服馬達
  * 伺服馬達控制卡
  * 腳架(或是其他可以安裝平台的裝置)
  * 電池
  * 影像及遙測無線電
  * BEC、冷卻風扇、低電壓警示裝置(這些雖是選配但建議使用)

### 為什麼我要建立它? ###

簡單，只有兩個理由，第一它允許你使用定向天線。有一種是[魚骨天線](http://www.l-com.com/productfamily.aspx?id=6326)另一種是[平板天線](http://en.wikipedia.org/wiki/Patch_antenna)，這兩種是最常使用的定向天線。這些定向天線因集中定向的功率故可增加通訊範圍，提高 AT 到飛機的信號靈敏度。但是在範圍內的數值並非是固定的(量測的單位是[dBi](http://en.wikipedia.org/wiki/DBi#Antenna_measurements))，靈敏度會取得相同數量，如果沒有列出，那麼你可以假設它們是相同的。

代價是後面那支的定向天線。定向天線一定要指向你的飛機(within a certain amount of error)，否則，你首先會注意到強度降低，接下來就會失去連結。

第二個理由就是如果你建立它你就會明白。所有 DIY 的精神就是你了解並有足夠的能力做一些事情，而其他大多數人不能或不會做手工藝。

### 說夠了開始動手建立吧! ###

好吧，這是在建立相關知識，你必須明白並了解這一切是如何運作。

#### 主體 ####

你將會需要一個可以承載天線重量的主體。4 磅的重量是否能夠轉動取決於你舵機的扭距及材質。[這個是我目前正在使用的機體說明書。](http://readymaderc.com/store/index.php?main_page=product_info&cPath=11_27&products_id=96)它目前有安裝2個平板天線每一個的重量是 12 盎司。你可以自己設計你自己的機體，但是你應該要有一台[CNC 機台](http://en.wikipedia.org/wiki/Numerical_control)，任何一個不準確零件都會影響到追踪的準確性，而且可能會失去你的飛機。木製結構使用兩個天線都沒有問題，當使用金屬結構時也許可以將整個機構縮小而且也可增加其耐久性。

特別提一下齒輪的問題應先解決。我的機體有使用到齒輪。你會發現成對齒輪的功能非常有用。首先它們可以可以將扭矩"轉換"成距離(甚至透過力距就可以改變角度)，第二它們可以增加或減少旋轉的速度。有時你可以用它們讓你的機體半自動化的拆卸舵機，就如同剛才我說的它會非常非常的有用。

要選擇齒輪時提醒你注意一些事情。第一就是找出舵機的中心點至 AT 中間旋轉軸的扭距。所有的伺服機都有 10 kg-cm 或 100 oz-in 單位的級距，意思是說當你測量舵機軸心移動 1cm 的力量是 10KG，100盎司也是同樣的道理，量測舵機軸心移動 1inch 的力量為 100盎司。因此，進一步來說如果你想要移動 2 inches 你的扭矩就會減少一半(因為一樣的力量但你的距離卻增加了一倍)，以我們的例子而言大概就只剩下 5 KG 或 50 OZ。

而速度的的變化基本就取決於齒輪的直徑和齒數。據經驗法則越大齒輪的速度較慢，它與齒輪的齒數及大小有關。因此，一個44齒的大齒輪需要配一個齒數只有它直徑一半的22齒小齒輪，這樣小齒輪的旋轉速度就會增加兩倍。就是將轉矩轉換成速度。

#### 天線的選擇 ####

你要決定你該使用什麼樣的天線。頻率是\*最主要\*的考量。有些天線聲稱在某一個頻段內的可用性，但並非都是合法的。像 915MHZ(又名900MHz)就是一個很具體的例子，你的天線在出廠時就已經"調整"到最好的狀態的 912Mhz。請仔細閱讀你正在搜尋天線的規格。以這份指導文件而言我選用的是 1280Mhz (又稱 1.2 or 1.3 Ghz) 及 [L-COM](http://www.l-com.com/home.aspx) 的 915Mhz 平板天線。如果你是使用 DIY store 的[3DR radios](https://store.diydrones.com/3DR_RadioTelemetry_Kit_915_Mhz_p/kt-telemetry-3dr915.htm)(我也是使用這個模組)你也許會想說"什麼是跳頻"？ 你的無線電可能會跑出"有效"頻寬(頻率可由天線做有效傳播)但是如果它的信號下降(又稱 [RSSI](http://en.wikipedia.org/wiki/Received_signal_strength_indication)，Recieved Signal Strength Indicator)及補償，不要擔心，只要確保你的天線在正確的頻率範圍內，你還是可以使用。

#### 伺服機的選擇 ####

你會需要兩台伺服機。一台負責垂直方向另一台則是水平方向。垂直向的只會移動天線而水平向的則會移動整個天線底座，或者也有可能取決於你是如何設計天線的擺放方式。事實上伺服機是個複雜的小設備。這裡會盡量精簡，如果你想找到更多伺服機的詳細資料請上網查詢。你如果想要安裝2個平板天線伺服機的轉矩至少有 110 oz-in，我建議用[卡夢材質的齒輪](http://en.wikipedia.org/wiki/Karbonite_gears)確保不會滑牙，但是你可以先準備一般塑膠型來試看看。

負責垂直向的伺服機它的總旋轉角度大約是90度。不同廠家對於旋轉角的解釋是不同的，所以你必須要好好做事前功課。一個"標準"的伺服機旋轉角大約都是90度。

負責水平向的因為有兩支天線所以我建議轉矩至少要 200+ oz-in，有卡夢材質或金屬齒輸的更好。如果你要購買，在這裡的使用可以選擇數位式的伺服機(強烈建議)，因為它會有些修正動作而且類比伺服機可能無法像一個數位伺服機這麼準確。原因是防止過度旋轉，你的水平移動範圍會在某個限制內，但為了保持讓天線對準目標，你的 AT 會迅速旋轉約 360 度[(1:50 秒的地方就是個例子)。](http://www.youtube.com/watch?feature=endscreen&v=_lxUd96-1tw&NR=1)當它轉的愈快表示你與飛機的通訊時間愈少。如果你是使用 APM Mission Planner 的軟體，你就無法避免這樣的行為。建置一個 AT 如果不去關心水平旋轉範圍將會付出很昂貴的代價。軍事使用它們而且它們的性能還不錯，但是非常的昂貴因為涉及到了集電環的質量。如果你這麼做，可以避免纜線纏繞的問題，而且伺服的選擇範圍會變得更容易。為了建置這個水平的動作你可以使用一個 360度旋轉的伺服機，但真的不需要比這個角度更大。

#### 伺服機控制 ####

你會需要一些裝置將電腦內的資訊傳輸出來(再次聲明這是建立在使用 APM Mission Planner 來驅動 AT 的狀況下)，並且要讓這些訊號可以讓伺服機使用。APM MP 目前提供兩個選項，一個是 [Maestro](http://www.youtube.com/watch?feature=endscreen&v=_lxUd96-1tw&NR=1) 另一個是[ArduTracker](http://www.sparkfun.com/products/8785)。 Maestro 連接的是一塊伺服機控制卡，而 ArduTracker 則需要一塊伺服機控制卡及一個分離式的自駕儀。Maestro 最多可安裝 6 個伺服機，輸入端是使用 micro USB 電纜但是你只會使用到其中 2 個電源 Pin。ArduTracker 的版本只會使用 APM 早期的 ArduPilot 其中一個版本。它已經分離出來而且很便宜，幾年前你也許有一個，我不知道它多少錢，但是 HappyKilmore 的 GCS 是使用[這個建置](http://code.google.com/p/happykillmore-gcs/wiki/Tracking)，以及[它們](http://www.diydrones.com/profiles/blogs/antenna-tracking-in?xg_source=activity)都沒有寫在上面。我用過很多種，你也可以自行閱讀就比較不會出錯。你使用哪一種的伺服機控制器的類型不要緊，但要驅動伺服機你就會需要下載並安裝某些韌體程式。
Maestro 出廠時已經預先裝好，可是它看可能也會需要到他們的網站下載自動駕駛儀的韌體程式。取得正確版本的伺服控制器是很重要的，[請使用這份指導文件](http://vps.oborne.me/gcs/Tracker.html)。基本上你會在這個頁面發現兩個數字，一個是你的伺服機總轉矩設定時要小於伺服機能力的轉矩，然後看到中間頁面這邊可以詳述 Maestro 8 位元的伺服機命令。取得正確方法很關鍵，我可是為它掉了不少頭髮。

#### 電池 ####

伺服機的電壓有時是4.8V、6V，有時是 7.2V 有的甚至更多。大部份的 RC 伺服機的標準電壓是"5V"。這邊是使用 6V。當電池充滿時會輸出 12.5V。如果你沒有正確降壓至可用電壓就會燒毀你的伺服機。你的伺服馬達也會冒煙或者有小小的可能會燒掉主機版，無論結果如何，它的可靠性跑掉了，你就應該要買一個新的伺服機。如果很不幸的在飛行中壞掉，你的 AT 可能會失去與飛機的連結。你會需要一個 BEC  (Battery Eliminating Circuit)。這個案子是使用[這個](http://www.hobbyking.com/hobbyking/store/__4319__TURNIGY_3A_UBEC_w_Noise_Reduction.html)。如果你有做好功課，你可以看一下你所選擇舵機的怠速及滿載的消耗電流，就能挑選出一個可以負荷的BEC。如果你無法取得 BEC，你就會看到伺服機燒毀，然後就準備和你的飛機說BYE BYE。

#### 低電壓警示置 ####

也許你沒有在使用這種東西，但是我有。它很便宜而且可以挽救不只是你的電池，而且它還會告訴你，你的 AT 因電壓過低要準備關閉。它是一個聲音響亮的警報器。買幾個來用吧，說真的不用這麼小氣。

#### 影像的 Rx 及 Tx ####

Rx 及 Tx 分別為接收器及發射器的簡稱。它並不在這次 AT 建置指導的範圍這邊只是要告訴你請確保系統是適合你的。你的 AT 是會變得擁擠和雜亂是因為上面會裝上許多小東西。綁上這些東西好不好由你決定吧。

#### 腳架 ####

你還要一件重要的東西。你的 AT 愈高表示它的傳播信號愈好。可以去買一台但是上面不要有太多的突起物，就像照片中的那種。因為這些突起物會防礙你的線材。注意三腳架使用哪種類型的接頭，這樣你就可以設計如何將你的 AT 接上去。買個堅固一點的可以對抗風力的衝擊，才不會讓你的飛機連線落漆。你的 AT 最重大約 7 lbs(約 3.1 公斤)，所以應該不會影響到你如何選擇腳架。

### 這些圖片價值多少? ###


http://api.ning.com/files/mrMXxvGZGzST*uu2Bd1zOqNaIBfZfT*HoX6Q-rROLkYZ8ptm2k6dm5Ety9ssodpiSPcWy8B9v5UCK-Vrf95bzg__/IMG_0416.JPG?width=300

http://api.ning.com/files/Gr*Od0iYSA10sL2QFgAz-s1e1si4xN-pQ06XLkuhuSlHXBQShEMs*la*enI5GJ6E8QphZ4tFi4XwZKE6bA5XYA__/IMG_0417.JPG?width=300

http://api.ning.com/files/UZIdHUiUcaaMRS3ZfPMMe7*mYmUBrlizO5NoGSQWMC2fKMUaDO3D5*K9yK5tdtT1fOamlS6WEDON2UeGG09lpA__/IMG_0418.JPG?width=300

http://api.ning.com/files/6DLnZfDv*8JaH9FWOlG8H**legwY9qlUmR7aSVuWhpMawU3oJ5MEXN6-VJd7JDEG8vczRa4TnpzqdHstHusjJA__/top.jpg?width=300

http://api.ning.com/files/mNgXdkeMUzvXspzluWq-JjGPHf6oiED8RUbJEXc-GOVKU2xzNBCRDoll2L0lkCXZlYv9RdKeRmUL3i2592jHxQ__/IMG_0420.JPG?width=325

http://api.ning.com/files/CLn6cdxUhdPqsT3jq*1vCBGJED8hNOr*rBHR25ZuvlD8L2nD1grj1Y7o60ybnO2pn480Lwp8jIck01KTK095tQ__/IMG_0422.JPG?width=350

http://api.ning.com/files/rSTp3gcLPnlLGEGAOYzsLHHSD4StNS0JJO09xoCOGKEfk3LYsO5AyVrhXmvZ4GePKo*gv5BWYb4UsBiVLzicOQ__/IMG_0421.JPG?width=350


### 開始組裝 ###

**魔鬼粘及束繩在這邊你會時常用到**!

1) 使用 micro USB 將舵機控制器連接至你的筆記型電腦。

2) 將舵機連接至舵機控制器。如果你是使用 Maestro servo 0 腳位是水平向，servo 1 腳位是垂直向。

3) 將 BEC 設定為5V 或 6V 或者舵機允許的最大電壓然後接上電池。將 BEC 連接到舵機控制器。Maestro 最外測的 BATTERY 腳位將會驅動你的舵機 (由 USB 電纜線做為板子的電源)。如果你不想買新的請不要把極性弄反了。

4) 將電池(這邊假設是 Li-Po)接上低電壓偵測裝置，這一步請小心。

5) 將天線連接到 3DR 無線電模組(絕對不要在沒有接上天線的時候就將無線的電源打開)。將視訊裝置的接收器天線裝上。

6) 你會需要想辦法將電池的 12V 接你到視訊裝置的接收端，應該會需要一些焊接工作。然後再就可以將視訊裝置的接收器的電源裝上。

7) 將 3DR 900Mhz 無線電接上你的筆記型電腦(在連接你的天線之後)。

8) 使用束繩確保所有的電線都有綁緊。這一點很重要。如果沒有弄好你的 AT 將會無法追縱並且會失去你的飛機。

9) 使用魔鬼粘及束繩就可以完成剩餘的步驟!

### 基本使用 ###

1) 當你到達飛場時請將 AT 朝向北方，請用你的眼睛觀察盡可能的接近。

2) AT 校驗一般可接受的範圍是北方 10 度以內。

3) 如果遇到特殊無法向北的狀況是可以解決的，只要將接在伺服機上的小齒輪退下來就能輕易的轉到別的方向。如果你的 AT 主體沒有這種功能，在它完成啟動後只要做些動作就即可(當設定伺服機控制器時，你可以分配預設的 PWM 號碼)。

4) 你想預設伺服的行程範圍內傾斜(tilting)的中置點，所以如果是 90 度的舵機，預設可設定為 45 度。當你第一次實際使用天線要有耐心，傾斜(tilting)的動作並且在 MP 軟體中透過滑動區塊手動調整它或者如果你有信心你也可以自己手動調整舵機拉桿。任何一種方式都可以運作，但是如果你使用滑動區塊你就不會壓壞舵機，它會自然地走過並允許行程。

### 其他事項 ###

我已經放上我的 AT 各種角度的照片(第 2 版)。這邊有些重點，建置時重量盡量保持輕盈。伺服機的強度盡可能取得可負擔重量及尺寸較為合適的。你可以建置一個[無線版本](https://store.diydrones.com/ArduStation_p/de-0001-01.htm)的 AT ，如果你的遙測無線電是 DIY store 所賣的[3DR 或 Xbee 套件](https://store.diydrones.com/category_s/13.htm)。我不知道如何做到這一點，但是並不會比這裡的說明複雜，只是更昂貴。

有兩種方式可以測試，首先你要到戶外並且在開機前先將天線指向北方。然後讓你的飛機在 AT 的周圍移動就好像模擬飛機在附近飛行。你最少要距離 60 英尺，可以再用 100 英尺確認一下。另一個方式是載入之前 APM 2 的飛行記錄，設置「家」的位置，看看你的 AT 是否會跟著移動。

測試你盡可能都要去做，確保整個系統的臨界點。在測試時我建議不要連接你的遙控器(一般稱為 2.4G)來手動控制飛機。保持最原始的備份才不會在失誤時後悔莫及。

現在可以帶著風向標、氣壓計、風速計、啤酒、數位相機等去飛場吧！