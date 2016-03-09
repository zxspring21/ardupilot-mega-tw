=== 電路板供電的替代方式 ===

**3DR 電力模組**

如果你是使用 3DR 電力模組請至這裡找尋說明:
http://code.google.com/p/ardupilot-mega/wiki/Voltage

**電力需求簡介**

_**單一電源供給**_

| Power Options | Nominal  | Abs MAX | JP1 status |
|:--------------|:---------|:--------|:-----------|
| Power on Output PWM connector | 5.37V +-0.5 | 6V      | JP1 connected |
| Power on Input PWM connector | 5.00V +-0.5 | 6V      | JP1 connected |

_**雙電源供給**_

| Power Options | Nominal  | Abs MAX | JP1 status |
|:--------------|:---------|:--------|:-----------|
| Power on Output PWM connector | 5.00V +-0.5 | 6V      | JP1 open   |
| Power on Input PWM connector | 5.00V +-0.5 | 6V      | JP1 open   |
註: 如果 JP1 是開啟的，電力需來自於輸入及輸出的 PWM。

板子在出廠時就已經設定電源就是來自你的輸出端。當你在工作台上進行設定及測試時，你可能會通過USB電纜供電板，但是你的飛機上，你的給電方式會需要使用內建的電源系統，通常是透過 ESC 使用鋰電池。在四軸飛行器就要透過你的配電板(PDB)，但是ESC的電壓可會超過5V。

在下面的圖片中，紅線及黑線就是由 PDB 來的 5V 電源線。你可以將它們插到 APM 2.5 輸出端上任兩個 5V 及 Ground (中間及最外側)。四軸飛行器還有一條橘線及白線的四線電纜，這是一條從 PDB 來的訊號線，這些線會傳達 ESC 的命令給 APM 2.5。

下面是 APM 2 的圖片； 但概念是適用於 APM 2.5。

![http://wiki.ardupilot-mega.googlecode.com/git/images/pdbpower.jpg](http://wiki.ardupilot-mega.googlecode.com/git/images/pdbpower.jpg)


APM 2.5 可能會 2 個不同的電力來源，一個是來自於輸入端的 RC 系統，另一個則是輸出端的(伺服機或 ESCs)。這取決於 JP1 跳線(請見下列說明)。如果跳線是開啟的(出廠預設)，板子的電力來自於輸出端。I如果跳線是關閉的，板子的電力來自於輸入端，但是輸出端就需要有一個獨立的電力來源。如果你想要在飛機上使用兩個獨立的電力來源，一個給伺服機，另一個給電子設備，理想的輸入電壓是 5.37v +/-0.0v ，標準的 ESC 可能無法提供。


**注意: 輸入電壓不要超過 6.0V DC 不然會損壞你的電路板。**

有些人會考慮到電壓在瞬間大電流時可能會下降，將輸入電壓設置稍微高於中位數(但小於最大值)。

APM 2.5 消耗相對較小的電流(約 200 mA)，一個電源能夠提供 300 - 500 mA 將會相當的足夠。

太短或太長的電源線，壞掉或老化的接頭，或者 APM 電源的電流不足造成所謂"欠壓"的狀況可能會導致不可預知的操作。

電源是很常見的問題，被這些問題偷襲會令人相當的沮喪。沒有良好而乾淨的電源，任何自動駕駛儀或飛行控制器都可能會無法使用並潛藏危機。

下列是 APM 2 的圖片；但概念是適用於 APM 2.5。

![http://wiki.ardupilot-mega.googlecode.com/git/images/APM2_JP1.jpg](http://wiki.ardupilot-mega.googlecode.com/git/images/APM2_JP1.jpg)