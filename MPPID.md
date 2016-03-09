## 配置 PID ##

http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/missionplannerPIDsAPM.PNG

APM 的基本代碼設計和默認設置可以很好地控制小型和中型飛機，例如 EasyStar、SuperStar 和 Skywalker。但如果你的飛機不同，或者使用與眾不同的配置，你可能需要調整設定值。其中多數設定是"Propotional Integral Derivative" (PID) 常數。PID 是指 APM 和大多數自動駕駛儀使用的一系列控制算法（更多關於 PID 控制的說明可參見[這裡](http://en.wikipedia.org/wiki/PID_controller)).

PID調整有一點類似魔術，[這裡](Tuning.md)描述了一些基本竅門。

任務規劃器提供了一個修改絕大多數 APM 的 PID 設定的圖形界面。修改的方法非常簡單（修改你想要的設置，然後單擊 "Write PIDs" 按鈕保存到 APM 的 EEPROM 存儲器中), 但每個設定的涵義卻並不簡單。詳細說明請參見[此文檔](AdvancedConfig.md)。 也許有一天自適應控制器將自動配置這些參數，但可惜現在還無法做到。也許在 APM 3.0可以做到!