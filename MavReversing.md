## 通過 MAVLink 設置舵機逆轉和普通/升降副翼混控 ##

如果你願意，你可以通過 MAVLink 進行所有設置。逆轉任何舵機的最簡單的方式是在 RC 設置屏幕裡點擊舵機旁邊的 "逆轉" 選擇框，如下所示（這將自動屏蔽 DIP 開關）：

http://wiki.ardupilot-mega.googlecode.com/git/images/mpreverse.PNG

要選擇升降副翼模式或者逆轉升降副翼通道，使用底部的升降副翼選擇框:

![http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/mavelevon.png](http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/mavelevon.png)

## 用 MAVLink 設立升降副翼的迷你教程 ##

在用RC發射器正確設置手動控制之後，三個反向開關有八種組合的可能。兩種組合可以在手動模式下產生正確的伺服輸出，但是，只有一個會在手動模式產生正確的舵機輸出，並在自動駕駛儀控制模式（例如穩定模式）下將發射器輸入正確地變換為橫滾/俯仰命令。找到正確的組合需要一點嘗試，下面是一個教程：

  1. 首先，設置在手動模式下，用你的RC發射器裡的 elevon 混控設置。哪個 elevon 插入到哪個通道很重要！我的 Skyfun，左翼副翼應插入通道 1，右翼是CH2
  1. 現在，它在手動模式下正常工作，把你的APM 撥到飛行模式，並通過任務規劃器連接。執行正常的設置過程。
  1. 現在，讓我們通過 MAVLink 設置。轉到配置屏幕，查看 MAVLink 參數。查找 Switch\_Enable 參數，並將其設置為0（禁用 DIP 開關，並通過 MAVLink 設置所有的配置），寫入參數。 （刷新，以確保參數已經記錄）。現在轉到 Elevon 混合，並把它改為 1。寫入參數並刷新，以確保他們記錄
  1. 現在把模式改成穩定模式，移動飛機進行測試。你可能需要扭轉一些東西。 在 Skyfun 上，我需要扭轉 Elevon Ch1（ELEVON\_CH1\_REV = 1）。每次只改變一項設置！
  1. 如果\*橫滾\*運作正常，但\*俯仰\*是相反的，或者反之，嘗試交換舵機線通道。


---


### Details of how this works behind the scenes in MAVLink ###


To setup reversal and mixing using the EEPROM you first need to disable the use of the dip switches. You do that by setting the option SWITCH\_ENABLE to 0. If SWITCH\_ENABLE is 1 (the default) then the dip switches will control your mixing and channel reversal options.

Next you need to choose if you want to use elevon mixing or not. If you have a 'normal' plane with separate ailerons and elevator then you should set ELEVON\_MIXING to 0 (the default). If you have elevons you should set it to 1.

### Non-elevon EEPROM setup ###

For non-elevon setups (ie. setups with ELEVON\_MIXING set to 0), you have 3 parameters that control the servo reversals, one for each channel you can reverse.

The 3 parameters are:

| RC1\_REV | aileron reversal | set to -1 for reversal | defaults to 1 (meaning no reversal) |
|:---------|:-----------------|:-----------------------|:------------------------------------|
| RC2\_REV | elevator reversal | set to -1 for reversal | defaults to 1 (meaning no reversal) |
| RC4\_REV | rudder reversal  | set to -1 for reversal | defaults to 1 (meaning no reversal) |

### Elevon mixing EEPROM setup ###

For elevon based setups (where you have set ELEVON\_MIXING to 1), you have 3 different EEPROM parameters to setup. They are:

| ELEVON\_REVERSE | reverse the sense of the elevon mixing | set to 1 to reverse, defaults to 0 |
|:----------------|:---------------------------------------|:-----------------------------------|
| ELEVON\_CH1\_REVERSE | reverse channel 1 elevon               | set to 1 to reverse, defaults to 0 |
| ELEVON\_CH2\_REVERSE | reverse channel 2 elevon               | set to 1 to reverse, defaults to 0 |

Please make sure that you do careful ground testing after setting these parameters. Also remember that your RC transmitter must be set up to do elevon mixing, too!

### Important notes ###

  * Whenever you change your firmware your EEPROM settings will revert to the defaults if the new firmware has an incompatible EEPROM format. Please use the APM mission planner or your ground control station to save your settings, and **carefully check them after any firmware change**.

  * make sure you **always do ground tests** before every flight to ensure your channel mixing and reversals are all correct. Be careful to check that not only are your transmitter controls correct, but that the APM responds correctly to attitude changes in the plane when in stabilise mode.