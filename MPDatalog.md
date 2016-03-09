## 下載和分析記錄文件 ##

http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/MPlogdownload.PNG

## 下載記錄文件 ##

首先，確保滑動開關處於 CLI 模式 (朝向舵機尾部)，並且在任務規劃器的配置菜單中選擇了正確串口。

在任務規劃器中選擇 "Log Download" 頁，將顯示板上存儲器中的記錄列表。你可以選擇下載單個文件，也可以全部下載。它們將存儲在你的 APMMissionPlanner/logs 文件夾, along with a KML, 可以在 Google Earth 中打開。

**注:** 下載一個大記錄文件將花費很長時間 (幾分鐘)。在軟件報告結束之前不要中斷下載進程。你可以通過 IMU 板上的 Rx 燈確認數據確實正在傳輸。數據傳輸中燈亮，傳輸完畢燈滅。

### 分析記錄文件 ###

http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/planner6.PNG

在下載記錄文件後，就可以分析了。單擊一個要分析的記錄文件，可以打開記錄瀏覽器。

記錄理解起來有些困難，下面是基本內容:

  * 每行代表一條記錄，通常每秒記錄若干次。
  * 起始的 256 行為任務命令 ("CMD")--向下滾動，忽略它們。其後姿態數據（"ATT"）和 GPS 數據("GPS")將交替顯示。如果 GPS 數據是 0，那麼意味著此時 APM 沒有鎖定 GPS。
  * 你可能對姿態數據最感興趣。它包括三種形式: 橫滾、俯仰和偏航。單擊表中的任意一個單元格，以圖表方式顯示該類型的數據。你最多可以選擇5種數據。
  * 你可以向記錄文件中增加從性能監視到導航計算等許多數據字段。完整的列表和說明在[這裡](AdvancedConfig.md)。

你可以點擊任何單元格增加數據.


你可以使用滑鼠滾輪來放大縮小數據，或者在感興趣的的數據拖動一個框，將其放大到整個窗口。

## 教學影片 ##

<a href='http://www.youtube.com/watch?feature=player_embedded&v=62TmGiwFiDU' target='_blank'><img src='http://img.youtube.com/vi/62TmGiwFiDU/0.jpg' width='425' height=344 /></a>

<a href='http://www.youtube.com/watch?feature=player_embedded&v=IcVlJCR8N2g' target='_blank'><img src='http://img.youtube.com/vi/IcVlJCR8N2g/0.jpg' width='425' height=344 /></a>


### 記錄文件參數定義 ###

所有的參數定義在[這裡](https://code.google.com/p/ardupilot-mega/wiki/APM_Parameters)。