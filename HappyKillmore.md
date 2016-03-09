## HappyKillmore 地面站 ##

![http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/chasecam.gif](http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/chasecam.gif)

## 特性 ##

本地面站只支持 Windows 系統，包括以下特性:

  * 移動 3D 地圖顯示，帶有頭頂、追蹤攝像和第一人稱飛行視角。
  * 可以保存和重播任務 (即將發佈導出 KML 至 Google Maps 功能)
  * 集成實時視頻 (如果使用攝像機)
  * 提供命令行解析器，用於設置 APM


## 安裝程序 ##

你需要:
  1. [Happy Killmore 地面站程序](http://code.google.com/p/happykillmore-gcs/downloads/list)

安裝程序將自動下載和安裝所需的文件，但如果沒有自動安裝，下面是使用到的程序：
  1. [dot.NET 2.0 framework](http://www.microsoft.com/downloads/en/details.aspx?FamilyID=0856eacb-4362-4b0d-8edd-aab15c5e04f5&displaylang=en) (在 Vista 和 Windows 7 上已經預裝，因此如果你用這兩個操作系統就不用下載了。)
  1. [DirectX 用戶運行時](http://code.google.com/p/happykillmore-gcs/downloads/detail?name=directx_Jun2010_redist.exe&can=2&q=)，如果你機器上沒有安裝的話。
  1. [Google Earth](http://www.google.com/earth/download/ge/) 和 [插件](http://www.google.com/earth/explore/products/plugin.html), 如果你沒有安裝的話。

## 使用 HappyKillmore 地面站 ##

http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/HKGCS_serial.PNG

首先，選擇正確的串口 (可用Windows資源管理器查看端口號) 並設置正確的波特率。如果你用 USB 連接 APM，那麼選擇分配給 APM 的串口，波特率設為 115,200。如果你用 Xbee 連接，選擇分配給 Xbee 適配器的串口，波特率為 57,600。單擊 "Connect" 按鈕。

如果你的 APM 板處於 CLI 模式 (滑動開關朝向遙控插頭一側), 你就可以通過命令行(Command Line)頁與之通信了。

如果你的 APM 板處於飛行模式 (滑動開關朝向 GPS 插頭一側), 你可以在 APM 完成啟動過程（校準陀螺儀並閃燈）之後，在地面站的儀表盤上觀察完整的遙測數據（如最上面的圖所示）。

如果你切換到串行數據（Serial Data）頁，可以看到這樣的數據:

![http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/gcs_serial.png](http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/gcs_serial.png)

## 說明手冊 ##

HK GCS的完整的說明手冊在[這裡](http://code.google.com/p/happykillmore-gcs/wiki/home?tm=6).


## 錄製飛行 ##

http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/HKGCS_record.PNG

要錄製飛行, 連接串口, 點擊數據文件（Data File）, 在組合框內輸入新文件的名稱。單擊紅點按鈕 (錄製按鈕)。要停止錄製，再單擊錄製按鈕一次。

現在你錄製的文件會在組合框的下拉列表中顯示。點擊播放按鈕將播放選擇的飛行記錄。數據的記錄格式是串口接收的原始數據加上時間戳和結束符。該保存/播放功能目前與超級終端記錄的飛行數據不兼容。當前還不支持 KML 文件。

地面站還可以加載 APM 的任務。將 ArduPilotConfigTool.exe 生成的 .txt 任務文件放到 missions 文件夾中（該文件夾在地面站程序目錄中)。點擊任務（missions）頁，用組合框選擇保存的任務文件。

## 注意事項 ##

(當前) 最小屏幕分辨率為 800X480 (也就是說會佔滿大多數上網本和舊型號筆記本的屏幕)。 在儀表盤的左下方有一個按鈕，可以在小屏幕下放大儀表盤。

在串行數據（Serial Data）頁，最大姿態（Max Attitude）、最大 GPS (Max GPS)和最大航點（Max Waypoint）設置可以根據你的電腦速度調整性能。如果有延遲，首先減小 Max Attitude 值，然後減小 Max GPS 值。此外，在設置（settings）頁，地圖更新速率（Map Update Rate）也可能導致延遲，可以調小一些。

程序有兩個實時攝像頭（Live Camera）頁。每次只能選擇一個。一些用戶希望同時觀看Google Maps和視頻，另一些用戶希望觀看儀表盤和視頻。

還有一個小的注意事項是，當改變窗口大小時，程序會自動嘗試最佳的佈局 (2行3列、3行2列，或3行三列，其中座艙或3D模型以兩倍大小顯示)。在該模式下，單擊座艙或3D模型可以將它放大到2倍。