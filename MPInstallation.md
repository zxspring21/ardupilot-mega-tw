## 步驟一: 下載與安裝 Mission Planner ##

首先，下載 Mission Planner 安裝程式。你可以在我們的[下載頁面](http://code.google.com/p/ardupilot-mega/downloads/list)找到。它的名稱為`APMPlanner[version].msi`。選擇 64-bit 或 32-bit 版本，取決於如果你是使用 64-bit Windows 或 32-bit Windows。

(**Windows XP 使用者請注意**: 你的電腦需先安裝 .dot Framework 3.5。如果你尚未安裝，請到[這裡](http://www.microsoft.com/en-us/download/details.aspx?id=22)下載。

![http://wiki.ardupilot-mega.googlecode.com/git/images/installation.png](http://wiki.ardupilot-mega.googlecode.com/git/images/installation.png)

安裝程序將會安裝必要的驅動程式。你也許會稍等一會。之後請選擇"Install this driver software anyway."


![http://wiki.ardupilot-mega.googlecode.com/git/images/driver1.png](http://wiki.ardupilot-mega.googlecode.com/git/images/driver1.png)

(註: 如果你出現 DirectX 安裝錯誤息，代表你的 Windows 沒有更新到最新版本的 DirectX。請到[這裡](http://www.microsoft.com/en-us/download/details.aspx?id=35)下載。)

現在可以將你的 APM 板插入，等到 Windows 可以辨識出它就會安裝正確的驅動程式。**不要插在 USB 分接器 -- 這樣就不是直接插在你的電腦上**(許多分接器電源不是很穩定)。

APM 現在應該可以被辨識出來並且會顯示在你 Windows 的裝置管理員(你可以在 Windows 的控制台找到)如下圖所示(你的序列埠也許會是不同的號碼；它是由 Windows 基於你多少其他設備連接所分配)。所有的 USB 皆透過這個序列埠與 APM 互通。

_(註：如果你也在電腦上使用 Xbee 無線模組做飛行遙測及規畫任務，Windows 也會分配給模組一個不同的序列埠，這些你也可以在控制台看到。)_

![http://wiki.ardupilot-mega.googlecode.com/git/images/driver4.png](http://wiki.ardupilot-mega.googlecode.com/git/images/driver4.png)

如果你的 APM 已經插入，序列埠應該會顯示在 Mission Planner。請確認鮑率設定為 115200。

**還不要點擊"Connect"!你必須為你的飛行器上傳正確的軔體。**

請這麼做，在畫面上選擇一個圖示。選擇藍色的飛機圖示。Mission Planner 將會自動判別你是什麼類型的板子，可以從網路上下載最新的程式並上傳至你的 APM 板。

![http://wiki.ardupilot-mega.googlecode.com/git/images/firmware.png](http://wiki.ardupilot-mega.googlecode.com/git/images/firmware.png)

註: 如果你想要下載之前舊的韌體版本，請在 firmware 的畫面按下 Control-O 就會在右下角開啟一個下拉選單，這樣就可以選取其他版本。這些數字是指 Git 版本控制的某個雜湊數，但如果你按下其中任何一個它，將會上傳每一種機型 ICON 的版本號碼所以你可以看到它們所對應的代碼版本。

一旦你已經安裝了 Mission Planner，如果有可用的升級它會顯示通知並且自動更新。不必再執行安裝程序！

_(註:如果你想要使用 Arduino 燒錄你的 APM ，你仍然可以這麼做。祥情請見[這裡](http://code.google.com/p/ardupilot-mega/wiki/Code))_