== APM 軟體安裝 ==

### Step One: 安裝APM 2 USB驅動程式 ###

如果你之前從未使用過Arduino，當你電腦首次插入APM時你會需要安裝驅程式，將APM2插入就會顯示下列訊息：

![http://wiki.ardupilot-mega.googlecode.com/git/images/driver3.png](http://wiki.ardupilot-mega.googlecode.com/git/images/driver3.png)

你可以從[這裡](http://code.google.com/p/ardupilot-mega/downloads/detail?name=Arduino%20MEGA%202560.inf&can=2&q=)下裡驅動程式

現在到windows的控制台/硬體和音效/裝置管理員，你就可以在「其他裝置」中看到"Arduino Mega 2560"，點擊滑鼠右鍵選擇更新驅動程式軟體，進去後選擇「瀏覽電腦上的驅動程式軟體」。

![http://wiki.ardupilot-mega.googlecode.com/git/images/driver5.png](http://wiki.ardupilot-mega.googlecode.com/git/images/driver5.png)

找到你剛才下載驅動程式即可。

![http://wiki.ardupilot-mega.googlecode.com/git/images/driver2.png](http://wiki.ardupilot-mega.googlecode.com/git/images/driver2.png)

如果出現以下的畫面請直接選擇安裝驅動程式。

![http://wiki.ardupilot-mega.googlecode.com/git/images/driver1.png](http://wiki.ardupilot-mega.googlecode.com/git/images/driver1.png)

一旦你安裝成功就會看到APM2出現在下列這個畫面(序列埠的號碼取決於你的Windows安裝了多少個序列埠裝置，所以你的序列埠號碼也許會和畫面中的不同)：

![http://wiki.ardupilot-mega.googlecode.com/git/images/driver4.png](http://wiki.ardupilot-mega.googlecode.com/git/images/driver4.png)


(請注意，如果你也使用Xbee無線模組做為和Mission planner通訊的模組，Windows也會為模組指定不同的序列埠，當然你也可以在控制台看到這些裝置。)


### Step Two: 下載 Mission Planner ###

![http://wiki.ardupilot-mega.googlecode.com/git/images/firmware.png](http://wiki.ardupilot-mega.googlecode.com/git/images/firmware.png)

現在可以下載Mission Planner，這個軟體會幫你載入代碼至你的APM2。

你可以在[這裡](http://code.google.com/p/ardupilot-mega-tw/downloads/list)下載最新的Mission Planner，解壓縮後請執行ArdupilotMegaPlanner.exe。

這套軟體只能跑在已經裝有Framework 3.5以上的Windowes電腦，如果你是使用Windows Vista and Windows 7則已經預載，但如果是使用Windows XP請到[這裡](http://www.microsoft.com/net/download.aspx)下載安裝。

如果你已經將你的APM接上序列埠的號碼會顯示在Mission Planner的右上角，請確認鮑率為115200。

**還不要點擊“Connect”!!請先將韌體程式載入你的APM。**

請照下列方法操作，選擇一個下列其中一個圖示，如果是飛機請選擇ArduPlane(版本號碼)。如果你只想要連接你的APM至Xplane模擬飛行器，請在左下角plane HIL點擊右鍵載入韌體。Mission Planner會自動辨識飛控板的類型並由網路下載最新版本至你的APM飛控板。

![http://wiki.ardupilot-mega.googlecode.com/git/images/firmware.png](http://wiki.ardupilot-mega.googlecode.com/git/images/firmware.png)

(備註：如果你想要使用Arduino燒錄APM程式請參考[這裡](http://code.google.com/p/ardupilot-mega/wiki/Code))