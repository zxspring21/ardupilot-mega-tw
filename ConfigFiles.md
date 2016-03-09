==常用機體的配置文件==

這是一個用戶提供常用飛機的配置文件列表。

請使用下圖圈起來的按鈕下載檔案到電腦中資料夾並使用 Mission Planner 的 Configuration 頁面載入到你的 APM。

http://wiki.ardupilot-mega.googlecode.com/git/images/ConfigFile.JPG


記得你仍然要設定行器及飛行前的檢查請在[這裡](http://code.google.com/p/ardupilot-mega/wiki/StartingArduPilotMega)確認正確的舵機方向。雖然這些 PID 設置的配置文件是很好的出發點，但所有飛機和RC系統是不同的，所以你還是要檢查，並有可能需要調整設置。

要提交自己的配置文件請在[這裡](http://diydrones.com/profiles/blogs/new-configuration-file)列出，並張貼的意見。


---


### HobbyKing Bixler v1 或 v2 ###
(v2 has a slightly bigger wing and sturdier fuselage)

![http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/BIXLERMODE2165423.jpg](http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/BIXLERMODE2165423.jpg)

Bixler 1:In ARF form from HobbyKing's [US warehouse](http://www.hobbyking.com/hobbyking/store/uh_viewItem.asp?idProduct=18083) or [rest of world](http://www.hobbyking.com/hobbyking/store/uh_viewItem.asp?idProduct=16544).

Bixler 2 kit: [USA Warehouse](http://www.hobbyking.com/hobbyking/store/__31048__Hobbyking_Bixler_2_EPO_1500mm_w_Optional_Flaps_KIT_US_Warehouse_.html) 及 [rest of world](http://www.hobbyking.com/hobbyking/store/__27169__Hobbyking_Bixler_2_EPO_1500mm_w_Optional_Flaps_KIT_.html)

**[參數設置檔](http://code.google.com/p/ardupilot-mega/downloads/detail?name=bixler.param&can=2&q=)**

### Bixler 設置技巧: ###

1) 過重的 Bixler 飛行時需要更快的速度，如果速度太慢則又會導傾斜而失速，所以盡可能讓重量降低!在穩定模式中要離開失速的狀態有時會非常的棘手。

2) 使用一些 pitch 來設置手動水平 - 花些時間來設置它，請多飛行幾次因為你要使用最低的油門讓飛機保持非常穩定的巡航速度。這會需要一點時間才能為穩定的巡航飛行調整出升降與油門的完美結合。巡航油門的位置約莫是 50% 的油門(但這要取決於你自已)。

3) 在 Stabilize 模式中執行測試飛行並且找出最低油門設置/速度而且一樣要保持穩定的狀態。有足夠的練習你就會知道什麼時候快要失速。要從失速中回復，請隨時準備好由穩定模式快速切換至手動模式(使機翼水平，並慢慢拉回)。測試時請飛行到足夠的高度才有能看到飛機在每個模式需要多快的速度。另外，當航向順風時請確保有足夠的油門可以保持速度。

4) 在穩定模式中轉向只能使用 rudder。 APM 會讓飛機在轉向時保持水平(當然需要適當的速度)。

5) 請確認全自動飛行模式下的目標油門為 10% 以上，任務巡航的油門設置是使用上述方法計算出的。

6) 如果在自動模式中設置了一個目標速度，請確認飛機的速度及有效負載是足夠的。

7) 這個配置文件的 aileron 和 rudder 已加上 50%(Rudder Mix)，這不是必要的除非你的 ailerons 上下移動的幅度非常的小。



---


### Skywalker ###

![http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/SKYWALKER.jpg](http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/SKYWALKER.jpg)

由[論壇](http://www.fpvflying.com/products/Skywalker-platform-for-UAV-FPV.html) 或 [fibreglass](http://www.hobbyking.com/hobbyking/store/uh_viewItem.asp?idProduct=15236)提供。

**[Configuration file](http://code.google.com/p/ardupilot-mega/downloads/detail?name=skywalker.param&can=2&q=)**


---


### HobbyKing Skyfun ###
![http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/skyfun.jpg](http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/skyfun.jpg)

Available [here](http://www.hobbyking.com/hobbyking/store/uh_viewItem.asp?idProduct=9614)

這個EEPROM 的設置檔案是 elevon 模式設定(set via MAVLink)。DIP 開關請略過

**[Configuration file](http://code.google.com/p/ardupilot-mega/downloads/detail?name=skyfun.param&can=2&q=)**


---


### Multiplex EasyStar ###

![http://wiki.ardupilot-mega.googlecode.com/git/images/easystar.jpg](http://wiki.ardupilot-mega.googlecode.com/git/images/easystar.jpg)

Available [here](http://www3.towerhobbies.com/cgi-bin/wti0001p?&I=LXFRU7&P=ML)

This configuration file is for a EasyStar with motor upgraded to brushless but rudder left stock.

**[Configuration file](http://code.google.com/p/ardupilot-mega/downloads/detail?name=easystar.param&can=2&q=)**


---


### Borojet Maja ###

![http://wiki.ardupilot-mega.googlecode.com/git/images/maja.jpg](http://wiki.ardupilot-mega.googlecode.com/git/images/maja.jpg)

Available [here](http://www.borjet.de/xtc/product_info.php?language=en&info=p31_MAJA-Traegersystem.html).

**[Configuration file](http://code.google.com/p/ardupilot-mega/downloads/detail?name=maja.param&can=2&q=)**


---


### TELINK Toro900 flying wing ###

![http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/toto900.png](http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/toto900.png)

Available [here](http://www.telink.eu/en-detail-100207-toro-900-tuning-professional-arf.html)

