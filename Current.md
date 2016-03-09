## 使用電流傳感器 ##

![http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/currentsensor.png](http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/currentsensor.png)

如果你增加了電流傳感器，你可以在地面站中實時查看電池的電壓和電流。可以顯示電池效率（瓦特/距離），並且如果輸入了電池容量的話，還能顯示 "剩餘飛行時間" （取決於地面站軟件）。

使用 AttoPilot 90A/50V 電壓/電流傳感器, 可以從[SparkFun](http://www.sparkfun.com/products/9028)買到 (上圖所示）。

傳感器提供電池電壓和電流的比例輸出。輸出值根據3.3V 12位ADC設計。滿量程為 51.8 伏，89.4 安。


如圖所示，將 AttoPilot 傳感器與 APM 相連。 使用第3個和第4個電壓傳感器引腳和相鄰的地腳。(注意如果你使用電流傳感器，就不能用這些引腳來測量電壓了。但是因為電流傳感器對測量剩餘電量更精確，所以你大概不會關注這個問題。）

焊上一個3腳的插針。從下面數第4個引腳是地線（黑線）。上一個引腳是電池電壓 (紅線)。 再上一個引腳是電池電流 (白線)。

![http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/AttoPilot_current.jpg](http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/AttoPilot_current.jpg)