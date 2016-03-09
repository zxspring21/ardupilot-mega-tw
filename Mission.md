## Mission Planner 工具 ##

http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/missionplanner2.PNG

任務規劃器由 Michael Oborne 開發，實際上它的功能不僅局限於任務規劃。下面是一些特性:

  * 使用Google Maps，點擊添加路徑點
  * 通過下拉選單選擇任務命令
  * 下載和分析任務記錄文件
  * 為你的飛機配置 APM 設置項
  * 與 PC 飛行模擬器交互，建立一個硬體擬真的 UAV 模擬器
  * 觀察 APM 的序列輸出

**注:** 你也可以用 HappyKillmore GCS 規劃任務，它也提供了點擊輸入功能和完整的腳本功能。選擇哪個完全是個人愛好。HK GCS 說明在[這裡](HappyKillmore.md)。本教程剩餘部分將集中於 APM 任務規劃器。

### 設置軟件 ###

如果你已經準備好，可以在[這裡](http://ardupilot-mega.googlecode.com/files/ArdupilotMegaPlanner.zip)下載 Mission Planner(它的名稱是 APM !Mission Planner x.x.xx.msi)。

它需要 Windows 環境和 .net Framework 3.5 ( Windows Vista 和 Windows 7 已經預裝，因此不需要單獨安裝)。如果你是使用 Windows XP 你可以自己到[這裡](http://www.microsoft.com/net/download.aspx)下載)。

Mission Planner 將在屏幕上方打開一個任務條，並顯示於 Mission Planner 的視窗。在任務條的 Options 菜單中，選擇指派給 APM 板的正確串口。同時單擊 `"APM Source Location"`，導航至 APM 代碼文件夾。Mission Planner 將在此文件夾中讀取和寫入文件。

注: Mission Planner 支持 APM 和 ArduCopter。在使用時確保你選擇對應軟件的功能菜單！

Mission Planner 主要的功能在屏幕上方的標籤頁中表示。每項功能的詳細說明在本說明書左側的導航欄可以找到。