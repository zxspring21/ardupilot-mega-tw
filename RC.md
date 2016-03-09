## 連接遙控設備 ##

你需要什麼:

  * 一個至少5通道的遙控設備。強烈建議7通道或更多通道。
  * 每個通道一條雙母頭舵機線。我們使用[這些短線](http://store.diydrones.com/product_p/pr-0003-03-5cm.htm)，方便布線
  * 一個電源。對於電動飛機，通常是電子調速器（ESC）。對於汽油/甲醇飛機，遙控設備需要獨立的電池。ArduPilot Mega通常從遙控設備取電 (APM內建一個穩壓器，所以你也可以直接使用電池，而不是從遙控設備/ESC取電。參見[相關說明](Hardware.md)）

如果你只使用 APM1 本身(未連接 RC 或 伺服機)，你可以只用USB 電纜供電。但是一旦你連接 RC 設備，你就應該要接上 ESC/電池來供電。USB 及 ESC/電池同時接在板子上也沒有關係。


**連接說明**

現在的ArduPilot Mega與最初版本相比有所改進。一個區別是現在的通道標記為1-8，而以前的版本使用0-7。下圖顯示了1.0版和1.4版的區別:

![http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/IMG_4936.jpg](http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/IMG_4936.jpg)

下面的給出兩種板子的連接說明。

![http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/ArduPilot_RC_Diagram.jpg](http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/ArduPilot_RC_Diagram.jpg)

![http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/ArduPilot_RC_Diagram2.jpg](http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/ArduPilot_RC_Diagram2.jpg)

用雙母頭舵機線將接收機與ArduPilot Mega (APM) 相連。每個想用APM控制的通道都要連接到APM板的一個輸入端上。

典型的通道設置如下表所示:
| **遙控通道** | **功能** | **APM 連接端 (v1.0)** | **APM 連接端 (v1.4)** |
|:---------|:-------|:-------------------|:-------------------|
| 1        | 橫滾 (Roll) | 0                  | 1                  |
| 2        | 俯仰 (Pitch) | 1                  | 2                  |
| 3        | 油門 (Throttle) | 2                  | 3                  |
| 4        | 偏航 (Yaw) | 3                  | 4                  |
| 5        | 自駕控制 (Autopilot control) | 7                  | 8                  |

**譯注**：不同遙控設備通道功能分配不盡相同，務必參考遙控器說明，APM 的輸入端應連接到對應功能的接收通道上。

**注:** APM支持升降副翼(副翼/升降組合，用于飛翼)。將它們連接到接收機的前兩個通道上。[下一節](Reversing.md)我們將說明如何使用撥動開關設置升降副翼混控。

APM軟件目前不支持 V 尾。你可以用一個硬件混控器混控方向和升降通道。


---


當你沿著彎排針看，可以發現信號線引腳離板子邊緣最遠，而地線引腳與邊緣最近。通常信號線是白色或黃色的，地線是黑色的。

將你的舵機和其他相讓APM控制的設備插到相應的輸出連接器上。在下圖中，我連接了5個通道和2個舵機。

http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/IMG_4808.JPG

前4個通道由APM的多路復用器控制。為了使用這個特性，你應該將APM的最後一個輸入通道（1.0版標記7，1.4板標記8）連接到接受上你想用來控制自駕儀模式的通道上。

當你將APM安裝到飛機上時，將其面向正確的方向是非常重要的。GPS 連接器應該面向前方，舵機線朝向後方，如圖所示 (註：IMU板的底部有一個小箭頭指向前方，以免在飛場忘了怎麼安):

![http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/imudirection.jpg](http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/imudirection.jpg)

### 安裝到飛機上 ###

當你把 APM 放到飛機上，很重要的一點是確認它有紮實的安裝而且在飛行中不會亂動。儘可能保持水平，這會影響到飛機飛行的方位。理想的情況下，如果可以請儘量靠近重心的位置(這樣振動會是最少的)，並且在堅固的平台上黏上泡棉雙面膠。

在3D Robotics Electronics Chassis裡的EasyStar有一個(加上GPS模組)[安裝攝像機](https://store.diydrones.com/Easy_Star_Electronics_Chassis_No_Pan_Tilt_p/ez-chassis.htm)的範例或 [未安裝](https://store.diydrones.com/Easy_Star_Electronics_Chassis_No_Pan_Tilt_p/ez-chassis.htm)。類似的機箱也可參考[HobbyKing Bixler](http://www.hobbyking.com/hobbyking/store/__16544__Hobbyking_Bixler_EPO_1400mm_ARF_.html)。

**機箱：**

![http://wiki.ardupilot-mega.googlecode.com/git/images/EasyStarwithChassis.jpg](http://wiki.ardupilot-mega.googlecode.com/git/images/EasyStarwithChassis.jpg)


**有安裝設備：**

![http://wiki.ardupilot-mega.googlecode.com/git/images/photo2.jpg](http://wiki.ardupilot-mega.googlecode.com/git/images/photo2.jpg)


### (可選)失效保護功能 ###

當最後一個通道的脈衝寬度超過1750毫秒時，多路復用器將切換到手動控制模式，最前的4個通道由遙控設備控制，而不是自駕儀控制。這意味著即使APM程序崩潰，你也總是可以切回手動控制。如果你使用其他模式選擇通道並將最後一個通道留空，你也可以不使用這個特性。在此情況下，你也可以擁有手動控制模式，但它就取決於軟件設計。自駕儀頭文件中有一個參數，可以用來告訴自駕儀你使用哪個通道來選擇飛行模式。這裡是關於APM失效保護功能的[進一步說明](Failsafe.md)。

此外，你也可以設置系統來提供失控保護功能。第一種方法是使用一個可以設置無線信號丟失時舵機默認值的接收機，例如Spektrum的接收機。這種情況下設置接收機，使得模式選擇通道默認值為當你選擇RTL（或自動）模式的輸出值。如果你的接收機只能設置失控時的油門通道，將其設置為1000毫秒以下，並且在頭文件中使能油門失效保護。