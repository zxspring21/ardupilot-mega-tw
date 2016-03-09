# 如何用 Flightgear 設置硬體擬真模擬器 #

_註: 在 ArduPlane 上使用 FlightGear 模擬器的方法是由社群所免費提供使用。它應該是可以正常運作，但是自從官方的開發團隊沒有繼續更新，如果有任何的問題及幫助的需求可以在 DIY Drones 論壇提出，而不是在這裡_

## 你會需要這些東西 ##

1. Flight Gear v2.x [Flightgear](http://www.flightgear.org)

2. ArdupilotMegaPlanner [Windows](https://code.google.com/p/ardupilot-mega/downloads/list)

3. APM 上設置 Ardupilot HIL (透過 APM Planner)

4. Flightgear 的 Mavlink.xml 數據[格式文件](https://ardupilot-mega.googlecode.com/svn/Tools/trunk/FlightGear/MAVLink.xml)

5. 建議使用 Windows 作業系統: 檔案: [system.fgfsrc](https://code.google.com/p/ardupilot-mega/downloads/detail?name=system.fgfsrc) 請放到 "C:\Program Files (x86)\FlightGear\data" 資料夾。 這將加載 Rascal 的遙控飛機和其他參數。載入的資料請見[這裡](http://wiki.flightgear.org/Fgfsrc)，你可以依自己的需求修改。


## 配置說明 ##

**安全第一:** 請先移除無刷馬達上的 3 條線，不然它可能會在你推動油門時轉動(如果你正好在手動模式)。


1. 下載並安裝 FlightGear 飛行模擬器

2. 把 Mavlink.xml 文件拷貝到 ` C:\Program Files (x86)\FlightGear\data\Protocol`

3. 到 Mission Planner > 'Configuration tab | Adv Parameter List' 儲存目前的參數，這樣你就可以在使用完模擬器後重新載入參數。

4. 在 MP 的 Firmware 頁面載入 'HIL Simulator | Plane' ardupilot 的韌體到你的 APM。

5. 開啟 Mission Planner 的 Simulation 頁面。

6. 選擇 FlightGear，然後點擊 'Start FG Plane' 的按鈕。

7. FG 載入之後點擊 MP 的 'Sim Link Start/Stop' 按鈕。

8. 在 FG 內按下鍵盤上的 'v' 可以將視角切換到飛機外，移動搖桿看看飛機是否會跟著移動。在 Mission Planner 中跟平時一樣要設置無線電包含了校驗及模式開關設定。

9. 在 FG 中按住鍵盤上的's'啟動飛機的引擎，然後推動油門就可以起飛。