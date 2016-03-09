## 完成ArduPilot Mega的硬件 ##

![http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/KT-APM-01-2.jpg](http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/KT-APM-01-2.jpg)

**你需要：**

  * 一塊 [ArduPilot Mega 主板](http://store.diydrones.com/product_p/br-ardupilot-02.htm)
  * 一把有優質烙鐵頭的烙鐵。我們使用 [Weller WES51](http://www.amazon.com/Weller-WES51-Analog-Soldering-Station/dp/B000BRC2XU)，但是你可以從五金店或音響店買更便宜烙鐵。注意確保烙鐵頭良好。
  * 一些[焊錫](http://www.amazon.com/Super-Solder-Wire-1-0mm-Diameter/dp/B0002KRAB0/ref=pd_bxgy_hi_img_c)

**組裝:**

首先，焊上兩個[3x8 右彎雙向排針](http://store.diydrones.com/product_p/pr-0001-05.htm)。這是用來連接遙控設備的。


http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/IMG_4791.JPG

然後，我們要切割連接 IMU 板的插接件。這是隨板子附帶的插接件

http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/IMG_4792.JPG

將一條公排針插到每個排針母座上，然後剪掉多餘的部分:

http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/IMG_4793.JPG

當你完成之後，每個排針都應該與母座一一對應:

http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/IMG_4797.JPG

現在取下插針，將它們放在ArduPilot Mega板的插孔上，如圖所示:

http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/IMG_4799.JPG

放一個筆記本（寫字用的）在插針之上，然後將板子壓在筆記本上，上下翻轉，這樣你就能焊接板子背面的插針了.

![http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/IMG_4806.jpg](http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/IMG_4806.jpg)

在焊好所有插針之後，將板子翻回來，每個排針之上插上母座:

http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/IMG_4801.JPG

現在小心地把IMU板放在上面，確保所有的母座引腳都與正確的插孔對齊，如圖所示:

http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/IMG_4802.JPG

每排焊上少量引腳，固定所有母座，然後小心地取下 IMU 板. 拿下來之後，焊接剩下的引腳。當你完成焊接之後，將板子翻過來，應該看起來和下圖一樣:

http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/IMG_4803.JPG

現在小心地將IMU板蓋在 ArduPilot Mega 板上。這對板子應該看起來和下圖一樣:

http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/IMG_4807.JPG

最後，如下圖所示連接 GPS 模塊 (圖中為 MediaTek 模塊). 它插在APM板的連接器上，而不是IMU板上那個相似的連接器 (那個標著"非 GPS!"的連接器是一個I2C連接器，用來連接可選的地磁傳感器或其他I2C傳感器)

http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/IMG_4846.JPG

### (選擇性安裝) 氣壓感應器 ###

If you are going to mount your APM board in the open and exposed to the airstream, the wind can distort the altitude sensor readings. So in such cases, it's best to cover the barometric sensor input with a breathable wind shield. Part of a cotton pad (like a makeup removal pad) is perfect (a bit of breathable foam would work, too). Just tape it over the sensor as shown:

http://wiki.ardupilot-mega.googlecode.com/git/images/IMG_5042.JPG

### (選擇性安裝) 加入電子羅盤 ###

移動時， ArduPlane 會由 GPS 模組取得前方的位置。但是在地面上要獲得精確的航向數據你就需要一個 [電子羅盤](http://store.diydrones.com/HMC5883L_Triple_Axis_Magnetometer_p/br-hmc5883-01.htm)。一個電子羅盤也可以改善空中航行。安裝說明在 [這裡](http://code.google.com/p/ardupilot-mega/wiki/Magnetometer)。

### (選擇性安裝) 電壓量測電阻 ###

![http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/resistors.jpg](http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/resistors.jpg)


You'll note that your APM kit came with four resistors, which are optional and are only used if you want APM to measure and report the voltage of your on-board battery. This can be useful if you have telemetry hooked up and you want to see this data in your ground station, as an indicator of how much battery power you have left.

如何使用的介紹在 [這裡](http://code.google.com/p/ardupilot-mega/wiki/Voltage)。

**先不要把 APM 插入你的電腦。在安裝完 Mission Planner 後的下一步我們再來做這個動作。**