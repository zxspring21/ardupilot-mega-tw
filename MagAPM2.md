## 使用外接式的磁力儀 ##

![http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/BR-HMC5843-01-2.jpg](http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/BR-HMC5843-01-2.jpg)

> 如果你有因磁場干擾而影響到 APM 2.5 板上內建的指南針的問題，你也許可以考慮使用外部的磁力儀，可以讓你遠離馬達之類的磁場干擾。下列說明如何使用：

### 步驟說明 ###

**1)** 買一塊[HMC5883L 磁力儀擴充板](http://store.diydrones.com/HMC5883L_Triple_Axis_Magnetometer_p/br-hmc5883-01.htm)。請確認 3DR 板是設定成 3.3 volts (APM 2.5 的 I2C port 是使用 3.3 volts，而非 5 volts)。 你將會需要修改一 3DR 板因為 3DR 出貨時跳線是設定 5 volt，如下圖所示。

![http://wiki.ardupilot-mega.googlecode.com/git/images/Magneto/Mag_HMC5843_jumper.jpg](http://wiki.ardupilot-mega.googlecode.com/git/images/Magneto/Mag_HMC5843_jumper.jpg)

**2)** 請見下圖，切斷 APM 2.5 板上中間的跳線。這樣會關閉 SDA 至板子內部的磁力儀。

![http://wiki.ardupilot-mega.googlecode.com/git/images/APMCompassModification.jpg](http://wiki.ardupilot-mega.googlecode.com/git/images/APMCompassModification.jpg)

**3)** APM 2.5 的 I2C 連接器需使用 4 pin 的 DF13 連接器，像[這個](http://store.diydrones.com/DF13_4_Position_Connector_10_cm_p/ca-0001-16-02.htm)一樣。切掉其中一頭的四線電纜。

**4)** 連接 DF13 的 4 線電纜到電子羅盤。請注意線不是一對一直接安裝。DF13 連接器的 Pin 1 不會剛好接到電子羅盤擴充板的 pin 1。標準的 3DR 電纜線有一條紅線及3條點線。請換成相對應的電線顏色。焊接說明如下:
  * **紅線** 在連接器最外側的那條(+3.3v)請接到電子羅盤擴充板上的 VCC (或 +3.3v)，(位置可以參考板子上的標記)。這條線是最接近 APM 2.5 板內部的一條線。
  * **紅線的旁邊那條** (SCL) 這條連接到電子羅盤的 SCL 點。
  * **紅線的下下條線** (SDA) 這條連接到電子羅盤的 SDA 點。
  * **連接器上最旁邊的黑線** (ground) 這條連接到電子羅盤的 ground 點。這條線最接近 APM 2.5 的板邊。

**5)** 電子羅盤請安裝在四軸飛行器的頂板。可以使用雙面膠黏上去。在下圖中，板子的腳位請朝向前方安裝。請注意你板子安裝的方向 – 你會需要使用這個方向來修正軟體，會在下一步驟中所解釋。

![http://wiki.ardupilot-mega.googlecode.com/git/images/Quad_Top_View.jpg](http://wiki.ardupilot-mega.googlecode.com/git/images/Quad_Top_View.jpg)

**6)** 程式修正，為你的電子羅盤編譯並載入軟體。這個步驟你必須要下載 Arduino IDE 編輯軟體才能完成。在“APM\_Config.h”內，你要找出下列的指令:

`//#define MAG_ORIENTATION     AP_COMPASS_COMPOENTS_DOWN_PINS_FORWARD `

For the orientation shown in the picture above，例如，請依下列的語法加入命令:

`#define MAG_ORIENTATION     AP_COMPASS_COMPONENTS_UP_PINS_FORWARD`

在 “AP\_Compass\_HMC5843.h” 類別庫中你可以找到 MAG\_ORIENTATION 旗標所有可能方位的清單，包含了 3DR 及 Sparkfun 板子的方位。

**7)** 如果你是一次從 IDE 載入這個軟體，請確認是否註釋掉下列的命令:

`#define CONFIG_APM_HARDWARE    APM_HARDWARE_APM2`

**8)** 儲存，編譯並上傳修正好的軟體

**9)** 測試電子羅盤，希望這個穩定的電子羅盤對你的飛行帶來幫助!


_(This entry contributed by Lloyd DeForrest)_