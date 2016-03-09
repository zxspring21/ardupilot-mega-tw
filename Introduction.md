![http://wiki.ardupilot-mega.googlecode.com/git/images/ardu_plane_logo.png](http://wiki.ardupilot-mega.googlecode.com/git/images/ardu_plane_logo.png)

歡迎使用ArduPlane操作說明，此說明會告訴你如何將一般的遙控飛機變為自動駕駛的無人機。只需要將 ArduPilot Mega 自動駕駛儀放入你的遙控飛機，你就可以在地面工作站透過 Mission Planner 的操作將你的遙控飛機轉變成完全程式控制的自動飛行器。

請按照左側功能表的說明。


### The ArduPilot Mega(APM 2.5) autopilot ###

http://wiki.ardupilot-mega.googlecode.com/git/images/APM25encl.JPG

ArduPilotMega 2.5 ([APM 2.5](http://store.diydrones.com/APM_2_5_Assembled_p/br-apmpwrkt.htm))是目前市面上功能最好的 IMU-based 開放碼的自動駕駛備設備(同時也是最便宜的一種 $179!)。

**功能包括**
  * 免費的開放碼韌體版本分別支援一般飛行器(ArduPlane)、多軸飛行器(quads, hex, oct, etc)、直升機(ArduCopter)及地面動裝置(ArduRover)。
  * 簡單的設定程序及韌體安裝，不需要寫任何的程式碼(但如果你想要修正程式碼你也可以使用內嵌的程式工具：Arduino)。
  * 只需點擊滑鼠就可設計出任務腳本。
  * 可以支援數百個3D航點。
  * 回到起飛點，在某個位置停懸、跟隨模式，或者只要在地圖上輕一下就能夠讓飛機飛至這個位置(需安裝遙測系統)。
  * 自動起飛及降落。
  * 強大的MAVLink 協定支援飛行中使用雙向無線通訊。
  * 選用免費的地面工作站：Mission Planner 的功能包含任務規畫、空中即時參數設定、影像播放、合成語音、及完整的資料記錄與重播。
  * 跨各種作業平台，支援Windows、Mac及Linux，使圖形化介面的Mission Planner需安裝於Windows平台(Mac可在Parallels下執行，Linux 可用 Mono)，在其他的作業系統中可使用命令列模式。
  * 支援自動起飛、降落及特殊的動作命令如影像及相機控制。
  * 支援飛行器的「hardware-in-the-loop」模擬。
  * 硬體裝置如下：
    * 3維陀螺儀
    * 3維加速器
    * 3維電子羅盤
    * 高精度氣壓感應器
    * 5Hz GPS 模組
    * 電壓感應器可測量電池狀態
    * 4Mb的資料記錄空間，Missions Planner會自動記錄並且匯出至KML
    * 內建故障安全處理器，當失去無線電訊號時會返回發射的地方
    * (選配)空速計
    * (選配)電流計


---


**RTFM!**

有一天你可以在沃爾碼買到autopilots的裝置，但目前還沒辦法。所有的機體不盡相同但做為一個開源的專案我們試著支援廣大的硬體選擇，這意謂著你要飛行前需先設定自動駕駛儀。

APM已經在標準的RC飛行器運行的很好，可以簡單而快速的讓你享受自動飛行的樂趣，如果你覺得有些設定不符合你的要求需要調整，我們也會試著讓調整的動作變得更簡單。

如果你還有任何疑問，請在實際飛行前先使用[模擬飛行](http://code.google.com/p/ardupilot-mega/wiki/Sim)。