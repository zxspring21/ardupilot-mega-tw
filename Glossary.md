## 詞彙表 ##

**2.4 Ghz**: 一個常用的數字（擴頻）電台通信頻率，常見應用包括 2.4Ghz 無線遙控、藍牙和一些視頻傳輸設備。它和以前模擬遙控通信中常用 72Mhz 頻帶不同。為了避免頻率衝突，建議使用 72Mhz 的遙控設備 + 2.4 Ghz 視頻傳輸， 或者 2.4 Ghz 遙控設備 + 900 Mhz 視頻設備。

**AGL**: 地面以上高度（Altitude above ground level）

**AHRS**: 姿態航向參考系統（Altitude Heading Reference System）。慣性導航單元加上程序代碼，根據傳感器輸出建立飛機的 XYZ 坐標和航向。

**APM**: [ArduPilotMega](http://www.sparkfun.com/commerce/product_info.php?products_id=9710).

**AMA**: 航空模型學會（Academy of Model Aeronautics）。美國主要的模型飛機組織。 對業餘無人機懷有敵意，禁止在 AMA 飛場飛行。但是每個 AMA 分會和飛場的政策有些區別，可能在某些飛場測試飛機和一些技術並不違反協會規則。

**Arduino**: 一個開源的嵌入式處理器項目。包括一個基於 Atmega168 和一些比較的輔助器件的硬件標準，和一個基於類 C 語言的軟件編程環境。官方網站在[這裡](http://www.arduino.cc/en/).

**ArduCopter**: Rotary-wing autopilot software for the ArduPilot Mega electronics

**ArduPlane**: Fixed-wing autopilot software for the ArduPilot Mega electronics.

**ArduRover**: Ground and water autopilot software for the ArduPilot Mega electronics

**BEC**: 電池降壓電路。ESC 中的電壓調節器(請見下方說明)，並且可以獨立運作。為 RC 設備、自動飛行器及其他電路板上的電子設備提供一個穩定的 5V 電壓。

**Bootloader**: 存儲在微處理器上的非易失存儲器上的一段特殊代碼，可以與 PC 交互，下載用戶程序。

**COA**: 授權證書（Certificate of Authorization）。一個 FAA 為無人機飛行的批准文件。更多細節參見[faa.gov](http://www.faa.gov/about/office_org/headquarters_offices/ato/service_units/systemops/aaim/organizations/uas/coa/) 網站和[DIY Drones 常見問題](http://www.diydrones.com/profiles/blogs/regulatory-faq).

**DCM**: 方位餘弦矩陣。卡曼濾波的替代品，計算量更小。更多細節參見 [這裡](http://diydrones.com/forum/topics/robust-estimator-of-the)。

**Eagle file**: 由免費的 [Cadsoft Eagle](http://www.cadsoftusa.com) 程序生成的電路圖和 PCB 設計文件（以及告訴 PCB 廠如何生產板子的相關文件）。這在硬件開源世界是最通用的標準，但它本身不是開源程序。不言而喻，它不是最理想的，並且 Eagle 軟件笨拙而難以學習。希望有一天能有開源的替代品。

**ESC**: 電子調速器（Electronic Speed Control）。在電動飛機中用來控制電機的設備，連接主電池和遙控接收器。通常包括一個 BEC （Battery Elimination Circuit，穩壓電路），為遙控設備和其他板上的設備（例如自駕儀）提供電源。

**FPV**: 第一人稱視覺（First-person view）。一種使用機上的攝像頭和與地面的無線連接，讓地面上戴著視頻眼鏡的飛行員以座艙視角飛行的技術。

**FTDI**: 一種將 USB 轉換為串口通信的標準。以芯片的方式提供，可以用在帶有 USB 接口的板子上，或者以[[傳輸線](http://store.diydrones.com/FTDI_Cable_3_3V_p/ttl-232r-3v3.htm)的形式連接到引腳。FTDI 是國際未來技術設備（Future Technology Devices International）的縮寫，就是生產這個芯片的公司的名字。

**GCS**: 地面控制站（Ground Control Station）。 運行在地面電腦上的軟件，可以接受無人機傳來的遙測信息，顯示它的狀態，包括視頻和其他傳感數據等。也可以在無人機飛行過程中傳輸命令。

**Hard Iron magnetic distortion （鐵磁失真）**: 由於飛機上的磁體或磁性物質引起的羅盤失真。這些失真相對於頭指向總是保持一個固定的方向，可以通過給三維磁力計讀數加上一個固定的偏移來補償。

**HIL**: 半實物仿真(Hardware-in-the-loop simulation): 使用在另一台機器上的軟件產生數據，模擬本應從自駕儀的傳感器發出的數據。自駕儀照常運行，並不知道數據是模擬的，而假設它們就是真實傳感器數據。半實物仿真使用連接到仿真器的真實自駕儀硬件，與軟件模擬自駕儀相對。在「開環」仿真中，軟件模擬器向硬件自駕儀輸送數據；而在「閉環」仿真中，硬件向軟件模擬器輸送數據。

**I2C**: 一種串行總線，支持多個低速外設（例如傳感器）同時連接到一個微處理器。詳情參見[這裡](http://en.wikipedia.org/wiki/I%C2%B2C)。

**IDE**: 集成開發環境（integrated development environment）, 例如[Arduino](http://arduino.cc/en/Main/Software) 編輯/下載/串口監視程序。通常還包括一個調試器。

**IMU**: 一個慣性測量系統(inertial measurement unit)，例如 ArduPilot ["OilPan"](http://store.diydrones.com/product_p/br-0012-01.htm)。通常包括至少3個加速度計（測量 x, y 和 z 維度上的重力矢量）和兩個陀螺儀（測量傾斜和俯仰軸的角速度）。單獨使用任何一種都不夠有效，因為加速度計在運動時會偏移（即，在短時期內包含很大的噪音），而陀螺儀會隨時間漂移。兩種傳感器的必須在軟件中結合起來決定飛機的真實姿態和運動，以建立姿態航向參考系統（AHRS，見上文）。一種結合的辦法就是卡曼濾波（見下文）。

**Inner loop/Outer loop**: 內循環/外循環。 通常指自駕儀的穩定功能和導航功能。穩定功能必須實時運行，通常每秒100次（「內循環」），而導航功能可以降低到每秒一次，並且可以容忍延遲和中斷（「外循環」）。

**INS**: 慣性導航系統(Inertial Navigation System)。一種基於一個初始 GPS 讀數和後續的動作和速度傳感器讀數，運用航位推測法計算位置的方法。當 GPS 失效或者短暫丟失信號時很有用。

**ICSP**: 電路中串行編程(In Circuit Serial Programmer)。一種給微處理器加載代碼的方式。通常是PCB上的一個6針插頭（雙排，每排3針）。要使用這種方式，你需要一個支持 SPI 標準的編程器。

**Kalman Filter**: 卡曼濾波器。在程序中一種相對複雜的算法，用來融合加速度計和陀螺儀數據，以產生飛機姿態和運動的更精確的實時描述。更多資料請參考 [這裡](http://tom.pycke.be/mav/71/kalman-filtering-of-imu-data)。

**LOS**: 視線（Line of Sight）。參見下文的 VLOS。

**LiPo**: 鋰聚合物電池，又稱 LiPoly。鋰離子電池是它的一個變種。這種電池比鎳氫和鎳鎘電池輕，而且功率更大。

**MAVLink**: The Micro Air Vehicle communications protocol used by the ArduCopter and ArduPlane line of autopilots。更多祥細 MAVLink 資訊請見[這裡](http://qgroundcontrol.org/mavlink/start)。

**MAV**: Micro Air Vehicle. 小型 UAV。更多祥細資訊請見[這裡](http://en.wikipedia.org/wiki/Micro_air_vehicle)。

**NMEA**: 美國國家海洋電子協會（National Marine Electronics Association）的 GPS 信息標準。當我們提到「NMEA 語句」時，我們指的是 GPS 模塊發出的文本字符串，例如 $GPGGA,123519,4807.038,N,01131.000,E,1,08,0.9,545.4,M,46.9,M,,**47**

**Oilpan**: [ArduPilot Mega IMU Shield](http://store.diydrones.com/product_p/br-0012-01.htm).  一個 arduino 形式的蓋板，與 ArduPilotMega 一起工作。包括各種傳感器(陀螺儀、加速度計、氣壓計等)，可以讓 ArduPilotMega 成為一個自駕儀。

**OSD**: 螢幕顯示（On-screen display）。一種將數據（通常是遙測信息）集成到實時視頻裡發送給地面的方式。

**PCB**: 印刷電路板（Printed circuit board）。在使用中，指的是一個為特定用途設計和「工廠製造」的電路板。相反的是麵包版或原型版，它們可以在不同的項目中重複使用。

**PDB**: 配電板。用在多旋翼機體中將電源分配到多個ESC的板子。

**PIC**: 指揮飛機的機師（Pilot in Command）。根據 FAA 的一項規定，如果由於娛樂而免除執照時，無人機必須在機師的直接控制下。參見上文的視線。（不要跟 Microchip 公司的 PIC 處理器混淆了）

**PID**: 比例/積分/微分控制（Proportional/Integral/Derviative）。一種機器控制算法，能夠提供更精確的傳感-運動控制循環，而具有更少的過控制。更多細節參考[這裡](http://en.wikipedia.org/wiki/PID_controller)。

**POI**: 景點拍攝。UAV 會讓相機保持指向某一個點。

**RTL**: Return to Launch. 飛回起飛點"家"的位置(簡單說就是請飛機飛回來)。

**SiRF III**: 大多數現代 GPS 模塊使用的標準。包括 !SiRF III 二進制模式，它是上面提到的基於 ASCII 碼的 NMEA 標準的一個替代品。

**Sketch**: 一個 Arduinio 項目中的代碼文件、驅動和其他 Arduinio IDE 生成的文件。

**SVN**: Subversion 版本控制程式庫的簡稱，放置了 DIY Drones 與其他開發人員的源始碼。

**Thermopile**: 一個紅外感應器。通常在 UAV 中成對使用，根據觀看水平方向前後和兩側的紅外信號計算傾斜和俯仰角度。依據是地面和天空間總存在紅外梯度，通過保證一對傳感器的讀數相同，就可以保證飛機水平飛行。可以在[diy drones 商店](http://store.diydrones.com/Thermopile_MLX90247_p/mlx90247esf-dsa.htm)買到。

**UAV**: 無人飛行器（Unmanned Aerial Vehicle）。在軍事中，它們通常叫做無人飛行系統 (Unmanned Aerial Systems, UAS), 表明飛機只是天空和地面的複雜系統中的一部分。地面的無人機器人稱為無人地面載體（Unmanned Ground Vehicles, UGVs），無人潛水器稱為無人水下載體（Autonomous Underwater Vehicles，AUVs）。機器船稱為無人水面載體（Unmanned Surface Vehicles，USVs）。

**VLOS**: 視力（Visual Line of Sight）。不依賴於人工視力輔助設備（除眼鏡外），機師能夠從地面清楚看見飛機並能控制飛機的能力。FAA 規則要求。

**WAAS**: 廣域增強系統（Wide Area Augmentation System）。一個由衛星和地面站組成的系統，提供 GPS 信號修正，位置精度比未修正的 GPS 高5倍以上。更多資料參考[這裡](http://en.wikipedia.org/wiki/Wide_Area_Augmentation_System)。

**Xbee**: 為常用業餘無人機推薦的 ZigBee 兼容的無線調製解調器的商品名稱。可以在 [sparkfun](http://www.sparkfun.com/commerce/product_info.php?products_id=8876) 找到。還推薦一個安裝板，比如 [這個](http://www.sparkfun.com/commerce/product_info.php?products_id=8687) 或 [這個](http://store.diydrones.com/product_p/br-0015-01.htm).

**ZigBee**: 一個無線通信標準，比藍牙距離遠，比 WiFi 功耗低。