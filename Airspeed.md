== 使用空速感應器 ==

![http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/BR-0004-03-2T.jpg](http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/BR-0004-03-2T.jpg)

APM 可以使用[空速感應器](http://store.diydrones.com/product_p/br-0004-03.htm) (上圖所示)來更好的控制飛行速度和處理風。這裡說明如何安裝。

在 IMU 板上標注 "Pitot Tube" 的孔上焊三個插針，同時在空速感應器板上的三個孔裡也焊上插針(插針應該朝向感應器一側）。用一條母頭-母頭舵機線連接起來。插針佈置如下圖所示：

這裡會示範如何安裝空速計:

### On APM 1 ###

將三個針腳焊接到 IMU 擴充板上的「Pitot Tube」，並且連接至空速計上的三個孔(這些針腳應該會在感應器上)。使用一個母對母的的轉接器將他們連接起來，如下圖所示。

![http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/pitot.jpg](http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/pitot.jpg)

如何使用母對母連接線連接：

http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/IMG_4859.JPG

另外，你也可以將插針焊在板子背面，安裝比較緊湊一些。下圖是 EasyStar 的一個例子:

http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/IMG_4879.JPG

下圖顯示在飛機上安好的樣子，包括 Xbee 無線模塊:

http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/IMG_4880.JPG


### On APM 2 ###

將空速計直接插入至(如果你尚未有空速計可以先將他們焊接起來)針腳「A0」如下圖所示：

http://wiki.ardupilot-mega.googlecode.com/git/images/IMG_5344.JPG

## 軟體配置 ##

你需要用任務規劃器來啟用啟用皮托管，如下圖所示。你可以在CLI中的 "test" 菜單中使用 "airspeed" 命令來測試是否工作。

備註：零和微小數值（2-3）之間的振盪是正常的。空速隨壓力的平方根變動，所以在零壓差的狀況下變化非常的小，它需要更大的壓力變化才可以模擬出速度。如果你看到的大多是0，1，2，偶爾反彈到3或4，它是正常的。在飛行時你不會看到這樣子的變化。可以做個實驗，你可以用指尖按著皮托管，然後為增加空速請對著它說15米/秒，這將很容易看出壓差的讀值(如果你保持固定的壓力)。

http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/airspeed_enable.PNG

## 安裝皮托管 ##
當你將空速感應器安上飛機時，使用[這個皮托管套件](http://store.diydrones.com/product_p/ac-0001-02.htm)。套件包括兩個管子，一個靜態管（端口封上，一側有小孔）和一個動態管（直通的管子，沒有封住）。兩個管子可以並排放置。在 EasyStar 上, 你需要將它們穿過座艙前的泡沫，這樣它們才能暴露在氣流中。途中我將管子超前伸了很多，以便獲得乾淨的氣流，但是炸雞可能會弄彎管子。如果你經常硬著陸的話，最好還是往後放一點。用皮托膠管連接鋁管的內端。
將皮托管的另一端連接到氣壓感應器的嘴上。動態管在上方，靜態管在下方。

http://wiki.ardupilot-mega.googlecode.com/git/images/pitotinstalled.JPG

如果你的飛機前方有螺旋槳，動態管必須按在一個機翼上，或者至少在機身的下方，以避開螺旋槳氣流。靜態管可以安在任何地方。

## 檢查操作 ##

你可使用 APMPlanner 或者其他地面站讀取空速計數值。敲擊皮托管和觀察回應該的狀況。在靜止空氣中零和小值振盪(2-3)都是正常的。空速隨壓力的平方根變化，使得接近零壓差的變化非常小壓力的變化也很小，而飛行速度，它需要更大的壓力變化，產生類似速度的變化。如果你看到的大多是0、1、2，偶爾反彈到3或4，是正常的。在正常的飛行中你不會看到這種變異。

你也可以在 ArduPlane Mission Planner 的 CLI 終端畫面檢查空速計。直接到 CLI/test 選單然後輸入"airspeed"。祥細資訊在[這裡](http://code.google.com/p/ardupilot-mega/wiki/Test)。


最後，你也可以執行一段 Arduino sketch 程式，它也會測試空速計。程式在[這裡](http://code.google.com/p/ardupilot-mega/downloads/detail?name=Airspeed_test.zip&can=2&q=)。