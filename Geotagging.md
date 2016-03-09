== 使用 Mission Planner 的地理資訊標記圖片 ==

![http://wiki.ardupilot-mega.googlecode.com/git/images/geo_ref_post.png](http://wiki.ardupilot-mega.googlecode.com/git/images/geo_ref_post.png)

具有 Geo-tagged 的航拍照片使用鑲嵌映射技術可以從地形建立精確的 3D 模型。

Mission Planner 加入了一個很好的工具，就是將 APM 的飛行遙測日誌檔的 GPS 數據加入 EXIF 標籤。

這次的教程會向你說明它是如何運作。(本教程由 Sandro Benigno 及 Guto Santaella 提供範例檔案及截圖。)

### 操作步驟 ###

1: 執行 Mission Planner 並按下 "Ctrl+F"。它會開啟一個隱藏視窗，如下圖所示:

![http://wiki.ardupilot-mega.googlecode.com/git/images/MainGeoref.png](http://wiki.ardupilot-mega.googlecode.com/git/images/MainGeoref.png)

2: 點擊按鈕 "Geo ref images"。
它會帶你進入存取 Geo Tagging 資源的畫面，如下圖所示:

![http://wiki.ardupilot-mega.googlecode.com/git/images/geotagimg.png](http://wiki.ardupilot-mega.googlecode.com/git/images/geotagimg.png)

3: 點擊按鈕 "Browse Log" 然後選擇你飛行時所拍攝的 telemetry log (.tlog) 。
註: 你可以使用這兩個資料來源: 可以從安裝 Mission Planner 的 "Logs" 資料夾或者你可以使用 USB 從 APM 的記憶體下載。


4: 點擊按鈕 "Browse Directory" 選擇放有航拍照片的資料夾。

![http://wiki.ardupilot-mega.googlecode.com/git/images/geotagimg.png](http://wiki.ardupilot-mega.googlecode.com/git/images/geotagimg.png)

5: 為了說明，以下的畫面顯示了本教程的任務:

![http://wiki.ardupilot-mega.googlecode.com/git/images/mission.png](http://wiki.ardupilot-mega.googlecode.com/git/images/mission.png)


6: 接下來請點擊 "Estimate Offset"。它會試圖從 "Log Start Time" 及第一照片的 "Shotting Time" 取出的偏移量。
然後會顯示"offset should be about...". 也許需要猜一下並手動輸入 "Seconds offset" 欄位。

![http://wiki.ardupilot-mega.googlecode.com/git/images/offset.png](http://wiki.ardupilot-mega.googlecode.com/git/images/offset.png)

7: 點擊按鈕 "Do it" ，等待程序結束。"Done... matches" 會顯示號碼，這就是你所拍攝的照片數量。如果沒有就表示同步有問題。

8: 點擊 "Location Kml" 你就可以在 Google Earth 上驗證的每張照片的定位。

![http://wiki.ardupilot-mega.googlecode.com/git/images/kml.png](http://wiki.ardupilot-mega.googlecode.com/git/images/kml.png)

9: 在上面的範例中你會看到照片大概的位置。你可以點擊左側清單上的任何一張圖。如果定位不準確，你可以回到步驟 6 微調 "Seconds offset"。

10: 完成調試後，你只需要點擊 "Geo Tag Images"。這個程序就會加入地理資訊到你的照片，包含了經緯度及高度。
這個程序會建立 "_geotag" 的新檔案。原來的那組照片會保持不變。_

![http://wiki.ardupilot-mega.googlecode.com/git/images/result.png](http://wiki.ardupilot-mega.googlecode.com/git/images/result.png)

11: 你可以藉由可視化的文件屬性明細查看你的照片。你應該可以在 EXIF 看到插入的 GPS 標籤。

![http://wiki.ardupilot-mega.googlecode.com/git/images/properties.png](http://wiki.ardupilot-mega.googlecode.com/git/images/properties.png)