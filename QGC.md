# **QGroundControl** #

![http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/QGC_OsgEarth.png](http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/QGC_OsgEarth.png)

QGroundControl 是一個跨平台(Windows/Linux/Mac的地面控制站，支持許多無人系統。目前支持 ArduPilotMega, PixHawk IMU, SLUGS, 和其它一些開源的自駕系統。這是通過使用基本的 MavLink 通信協議實現的。在 APM 2.0 中 ArduPilotMega 支持 MavLink 協議，程序可以再在[SVN trunk](http://code.google.com/p/ardupilot-mega/source/browse/#svn%2FSketchbook%2Ftrunk)下載 (用 SVN 客戶端--如果不清楚的話，查看 [這個教程](Tortoise.md))。

## 特性 ##
本地面站是跨平台的(windows/linux/mac)，包含以下特性:

  * 實時繪製和記錄遙測數據
    * 查看自駕儀標定的和原始的舵機輸出
    * 保存飛行遙測數據記錄
    * 用內建分析軟件讀取遙測記錄
  * 飛行時調整增益
    * 不重新編譯 APM 的情況下調整 PID 增益
    * Request parameters be read to/ written from read only memory.
  * 飛行時改變航點/任務
    * 選擇 起飛/盤旋/降落/導航 模式
    * 以相對於起飛點的形式輸入本地坐標，或者以緯度/經度/高度的形式輸入絕對坐標。
  * 輕量的二維俯視視圖
    * 在線/離線緩存衛星圖
  * 三維視圖
    * yahoo/google 衛星圖，使用基於 xml 的.earth 文件
    * 三維地形渲染
  * 支持上網本
    * 可以將窗口縮小到非常小的屏幕上
    * 所有組件均可關閉/重新打開，可調性非常高
  * 支持多個飛機
    * 使用 Mavlink 通信協議，消息帶有目標系統和源系統的編碼。同時支持廣播式通信

## 下載 ##
  1. 從[這裡](http://qgroundcontrol.org/downloads)下載 QGroundControl。


---

# 標準操作員視圖 #
這個截圖展示了標準操作員視圖，用於設置航點，監視系統總體狀態。

![http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/QGC_Operator.png](http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/QGC_Operator.png)

## 飛行時調整板上參數/增益 ##
板上參數部件允許你為飛機動態讀取/設置增益值。這使得在飛場調整增益變得簡單，不需要要重新編譯 APM。

![http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/QGC_OnboardParam.png](http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/QGC_OnboardParam.png)

## 飛行時調整航點/任務計劃 ##
板上航點/任務計劃部件允許你為無人機設置任務，甚至在飛行時動態調整。

![http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/QGC_Waypoints.png](http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/QGC_Waypoints.png)


---

# 上網本大小的操作員視圖 #
下圖展示了在上網本大小的屏幕上運行的操作員視圖。我們關閉了數個窗口，讓相關信息最大化。用戶可以停靠/取消停靠/關閉/重新打開任何一個部件。

![http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/QGC_Netbook.png](http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/QGC_Netbook.png)


---

# 工程師視圖 #
工程師視圖顯示系統傳來的所有原始遙測數據。它還可以記錄數據，供後續分析。這在鑒定系統和測試控制算法時很有用。

![http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/QGC_Engineer.png](http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/QGC_Engineer.png)


---

# 3D 視圖 #
這是當前3D視圖的一個截圖。他顯示了飛行旗的模型，還可以繪製3D軌跡。這在室內導航和調試時很有用。

![http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/QGC_3D.png](http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/QGC_3D.png)


---

# OsgEarth 視圖 #
正在開發中。與 OsgEarth 集成可以提供戶外的三維地形環境和緩存的衛星照片。緩存的信息可以離線使用。OsgEarth 還能讓加載標準飛機模型文件更加簡單。

![http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/QGC_OsgEarth.png](http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/QGC_OsgEarth.png)


---


# 配置 #

## 下載代碼 ##

在原生支持 MAVLink 的 APM 2.0 以 zip 文件的形式發佈在下載區之後，你可以直接使用它。在此之前，你需要用一個 SVN 客戶端（例如 Tortoise ）將它從 SVN 庫中下載下來。

  1. 下載[APM2.0 程序](http://code.google.com/p/ardupilot-mega/source/browse/#svn%2FSketchbook%2Ftrunk)
  1. 下載 Mavlink: git clone https://github.com/pixhawk/mavlink.git "pathtosketchbook"/libraries/mavlink
  1. 下載 [QGroundControl](http://qgroundcontrol.org/downloads) 或使用源代碼創建: git clone https://github.com/pixhawk/qgroundcontrol.git "base directory"/qgroundcontrol。如果你從源代碼創建，你需要將 "pathtosketchbook"/libraries/mavlink 拷貝到 "base directory"，或者創建一個符號鏈接。

## 測試 ##
  1. 如[此文](Code.md)所述，將arduino 的 sketchbook path 設為包含你的 APM 文件夾和庫文件夾的地址，重啟 Arduino IDE。 入下文所述，創建一個 APM\_Config.h 文件。
  1. 編譯代碼，將固件上傳到板子中。
  1. 啟動 QGroundControl，選擇網絡，增加鏈接，設置通信端口 (`linux 上為 /dev/ttyUSB* , windows 為 COM*`)，然後設置波特率為 115200 (如果使用 GCS\_PORT 3)

### APM\_Config.h 文件 ###
```
#define DEBUG_SUBSYSTEM 0

#define FLIGHT_MODE_CHANNEL 8
#define FLIGHT_MODE_1 AUTO
#define FLIGHT_MODE_2 RTL
#define FLIGHT_MODE_3 FLY_BY_WIRE_A
#define FLIGHT_MODE_4 FLY_BY_WIRE_B
#define FLIGHT_MODE_5 STABILIZE
#define FLIGHT_MODE_6 MANUAL

#define GCS_PROTOCOL GCS_PROTOCOL_MAVLINK
#define ENABLE_HIL ENABLED
#define GCS_PORT 3
#define GPS_PROTOCOL GPS_PROTOCOL_HIL
#define AIRSPEED_CRUISE 25

#define THROTTLE_FAILSAFE ENABLED
#define AIRSPEED_SENSOR ENABLED
```

---


## 測試 ##
<a href='http://www.youtube.com/watch?feature=player_embedded&v=5emVoUjMkxA' target='_blank'><img src='http://img.youtube.com/vi/5emVoUjMkxA/0.jpg' width='425' height=344 /></a>

# 文檔 #
  * http://qgroundcontrol.org/users/start
  * http://pixhawk.ethz.ch/wiki/mavlink/
  * http://qgroundcontrol.org/dev/build_source
  * [DIY Drones 設置指南](http://diydrones.com/profiles/blogs/qgroundcontrol-integration-for-2?xg_source=msg_com_blogpost&id=705844:BlogPost:220896&page=4#comments)