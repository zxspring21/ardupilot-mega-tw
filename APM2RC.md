===連接你的遙控設備===

把你的遙控飛機轉變成無人機，實際上只是將自動駕駛儀放入遙控接收器及飛行伺服機之間，這麼一來自動駕駛儀就可以完全控制你的飛行器。

我們的方法是用母對母的電纜線把RC 接收器與 APM 2 的 input 端連接，然後將伺服機(及電力飛行器的馬達控制器)插入 APM 2 的輸出端。

你需要下列幾種設備：

  * 至少5動的遙控器，建議7動以上。
  * 每個頻道需使用母對母接頭的連接線，[這個](http://store.diydrones.com/Servo_Jumper_Female_double_sided_p/pr-0003-03-10cm.htm)會是不錯的選擇。
  * 電源。電力飛行器通常是使用 ESC。汽油/甲烷動力的飛機，你的無線電就需要額外的電池及 BEC。ArduPilot Mega 的電源通常來自於 RC 系統。
  * 如果你是使用 APM 2.5，我們建議讓它(以及它的配件，如 GPS 及 3DR 無線電)使用包含[Power Module](http://store.diydrones.com/APM_Power_Module_p/br-apmpwr.htm)的電源。你仍然會需要一個 ESC 或 BEC 插到輸出端的任一 Pin 給伺服機供電；Power Module 只設計供電給 APM。

註: 在你的桌上時可以使用 USB 供電給 APM 2。不管如何就是不會從 RC 的輸出端供電，所以在測試 APM 2 時如果你想要看到伺服機作動，你就需要把電池(透過 ESC)接上某一個輸出通道。然後你會發現 ESC 及 USB 電纜可以同時連接在板子上。

電源的選項在[這裡](http://code.google.com/p/ardupilot-mega/wiki/APM25Power)。

### 輸入端 ###

![http://wiki.ardupilot-mega.googlecode.com/git/images/APM2/FRAMES_input_PLANE.jpg](http://wiki.ardupilot-mega.googlecode.com/git/images/APM2/FRAMES_input_PLANE.jpg)


依上圖所示，將遙控器使用母對母連接線接到 APM2 的輸入端。想讓 APM2 控制的每個頻道都需要連接至輸入端。一般而言，已經連接到 RC 接收器的模式開關(APM Input 8 for ArduPlane)通常會分配給 RC 發射器的3段撥動開關(大多數人為channel 5)。

(註: 這邊是 ArduPlane 的說明介紹。ArduCopter 模式開關在 APM input 5，不是 input 8，欲知更多請見[這裡](http://code.google.com/p/arducopter/wiki/APM2RC))

無論是直線或直角連接器，地線應該都在板子邊縁的外側，如下圖所示：

![http://wiki.ardupilot-mega.googlecode.com/git/images/APM2/straight_connector_APM2.jpg](http://wiki.ardupilot-mega.googlecode.com/git/images/APM2/straight_connector_APM2.jpg)

![http://wiki.ardupilot-mega.googlecode.com/git/images/APM2/right-angle_connector_APM2.jpg](http://wiki.ardupilot-mega.googlecode.com/git/images/APM2/right-angle_connector_APM2.jpg)


**PPM-Sum 接收器的介紹在[這裡。](http://code.google.com/p/arducopter/wiki/PPMsumRC?ts=1330332797&updated=PPMsumRC)**

備註：RC接收器的前兩個通道也支援副翼組，你可以透過 Mission Planner 的設定程序告訴 APM 如何操作各個副翼的動作。

如果你是 V 型翼，這個目前的 APM 軟體沒有支援。相對的，你可以使用外部硬體混合 rudder 及 elevator 通道。[這裡](http://www.hobbyking.com/hobbyking/store/uh_viewItem.asp?idProduct=6321)有一個又好又更宜的。

### 輸出端 ###

![http://wiki.ardupilot-mega.googlecode.com/git/images/APM2/FRAMES_PLANE.jpg](http://wiki.ardupilot-mega.googlecode.com/git/images/APM2/FRAMES_PLANE.jpg)

將伺服機及所有需要APM控制的設備接到輸出端，如下圖所示：

四動遙控器的設定
  * 1. aileron
  * 2. elevator
  * 3. throttle
  * 4. rudder

副翼設定
  * 1. starboard (right) elevon
  * 2. port (left) elevon
  * 3. throttle


### 安裝到你的飛行器 ###

使用正確的方法把APM放到你的飛行器很重要。GPS連接器要面向前方，伺服機連接器向後，控制板的右側向上，IMU則放控制板的上方。如圖所示(備注：以防萬一有個小箭頭在板子的下方指出前方的方向)：

![http://wiki.ardupilot-mega.googlecode.com/git/images/APM2/APM2_FWD.jpg](http://wiki.ardupilot-mega.googlecode.com/git/images/APM2/APM2_FWD.jpg)

當APM放到你的飛行器時請確認它安裝是否牢固不可在機體內晃動，這點相當重要，並且盡可能的與飛行方向保持水平狀態。理想的情況下，接近重心位置(振動會減至最小)並固定於一個穩定的平台。

**GPS 模組的安裝指示**

  * 這與 GPS 模組的面向沒關係，只要正方形天線朝上即可。
  * 將 GPS 盡可能地遠離發射裝置(如遙測模組或影像發射器)是最好的安裝方式。
  * 在理想的情況下，GPS 模組盡量直接朝向天空。放在飛機的頂部是一個不錯的選擇。

這裡 3D Robotics Electronics Chassis 的 EasyStar 有其中一種 APM(及 GPS 模組)的安裝範例，這邊有[使用水平垂直的相機雲台的](https://store.diydrones.com/Easy_Star_Electronics_Chassis_No_Pan_Tilt_p/ez-chassis.htm) 或 [沒有使用的](https://store.diydrones.com/Easy_Star_Electronics_Chassis_No_Pan_Tilt_p/ez-chassis.htm)。這裡也有個給 [HobbyKing Bixler](http://www.hobbyking.com/hobbyking/store/__16544__Hobbyking_Bixler_EPO_1400mm_ARF_.html) 使用的雲台。

**機箱：**

![http://wiki.ardupilot-mega.googlecode.com/git/images/EasyStarwithChassis.jpg](http://wiki.ardupilot-mega.googlecode.com/git/images/EasyStarwithChassis.jpg)


**有安裝設備：**

![http://wiki.ardupilot-mega.googlecode.com/git/images/photo2.jpg](http://wiki.ardupilot-mega.googlecode.com/git/images/photo2.jpg)