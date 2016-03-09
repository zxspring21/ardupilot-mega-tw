==使用Mission Planner可以反轉伺服機的方向及設定normal/elevon模式 ==

你可以反轉任何的伺服機來改變行進的方向這項功能可在RC設定的畫面中調整，如下圖所示:

http://wiki.ardupilot-mega.googlecode.com/git/images/mpreverse.PNG

畫面下方的核取方塊可以選擇elevon mode或反轉通道:

![http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/mavelevon.png](http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/mavelevon.png)


---


## Mission Planner 中有 Elevon 混合設定的小技巧 ##

![http://wiki.ardupilot-mega.googlecode.com/git/images/elevon.jpg](http://wiki.ardupilot-mega.googlecode.com/git/images/elevon.jpg)

在飛機的 elevons 上設置可能會需要些嘗試及錯誤，但這邊有些基本的設定：

  1. 首先，在手動模式下設置發射器的 elevon 的混控。這會決定 elevon 是由哪一個通道控制!**一般來說左翼的 ailerons 是 CH1 而右翼的是 CH2，如上圖所示。**
  1. 繼續在手動模式下，請檢查看看如果你有反轉任何發射器的通道，請確認控制舵面移動方式 pitch 及 roll 應該會一起作動。
  1. 現在它們應該可以在手動模式下運作，將 Mission Planner 與 APM 板連接。透過一般的安裝過程。當你在校驗 RC 輸入時，**不要只隨意的上下左右移動 elevator 及 aileron 遙桿。要確實的將它們移動到每個遙桿的極限值\*不然校準將會錯誤而且伺服機也會轉動太多。這是因為你的 RC 發射器已經切換到 elevon 模式，當遙桿在極限值時(例如最左及最上) elevator 及 airelon 輸入就會加入。
  1. 繼續在 MP RC 設置畫面，切到穩定模式。動一下飛機測試一下，並觀察控制面的變化。當你讓機鼻向下，2個 elevons 應該會向上，反之亦然。roll也是一樣；當你橫滾飛機時，elevons 應該會移動到可以讓飛機回復水平的方向。在這個畫面你也許會為了正確的移動方向而勾選某些選項反轉舵面。但記住一次只變動一項!
  1. 如果你無法找到合適的組合，嘗試更換伺服機的電纜，使得右邊是輸出 1 而左邊是輸出 2。這是最後的手段，因為你必須從這份清單的頂部，重新開始安裝。

---**

### MAVLink運作介紹 ###


要設定反轉及混合功能需使用EEPROM首先需關閉dip開關。把SWITCH\_ENABLE的選項設為0，SWITCH\_ENABLE如果為1(預設)dip開關就會操控你的混合及反轉通道的選項。

下一步你需要選擇是否使用反轉混合功能，如果獨立副翼及反轉器使用「normal」的規畫你應該要將ELEVON\_MIXING設定為0(預設)，如果你已經開啟反轉功能你應該要設定為1。

### EEPROM的無副翼設定 ###

沒有副翼的設定(也就是說要將ELEVON\_MIXING設為0)，你會有3個參數可以控制陀機反轉，每個通道皆可設定反轉。

下列有3個參數值：

| RC1\_REV | aileron reversal | set to -1 for reversal | defaults to 1 (meaning no reversal) |
|:---------|:-----------------|:-----------------------|:------------------------------------|
| RC2\_REV | elevator reversal | set to -1 for reversal | defaults to 1 (meaning no reversal) |
| RC4\_REV | rudder reversal  | set to -1 for reversal | defaults to 1 (meaning no reversal) |

### EEPROM的副翼混合設定 ###

副翼的基礎設定定(這裡可將ELEVON\_MIXING設為1)，你有3個不同的EEPROM參數可以設定:

| ELEVON\_REVERSE | reverse the sense of the elevon mixing | set to 1 to reverse, defaults to 0 |
|:----------------|:---------------------------------------|:-----------------------------------|
| ELEVON\_CH1\_REVERSE | reverse channel 1 elevon               | set to 1 to reverse, defaults to 0 |
| ELEVON\_CH2\_REVERSE | reverse channel 2 elevon               | set to 1 to reverse, defaults to 0 |

請確認在地面時就已經設定好這些參數，也要記得將你的RC發射器設定成副翼混合模式。

### 注意事項 ###

  * 每當你改變firmware，EEPROM的設置將恢復為預設值，如果新的firmware格式與EEPROM不相容，請使用APM Mission Planner或地面控制站來保存您的設置，**並仔細檢查firmware的異動狀況**。

  * **每次飛行前請在地面試驗**，以確保通道混合和反轉功能都是正確的。仔細檢查，不僅是你的發射器控制正常的，更要確認在穩定模式時APM可以確實的反應飛機上狀態的轉變。