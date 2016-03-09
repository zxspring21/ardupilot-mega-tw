# 刷寫 uBlox 模塊 #
當你從 DIY Drones 商店訂購一個 uBlox GPS 模塊時，你應當如下所述，將其設定為為ArduPilot 編程。

![http://wiki.ardupilot-mega.googlecode.com/git/images/ublox.png](http://wiki.ardupilot-mega.googlecode.com/git/images/ublox.png)

如果你忘了這麼做，或者從其他途徑購買，或者其他情況需要重新編程，你可以使用一條 FTDI 數據線完成這項工作。[這裡](http://diydrones.com/profiles/blog/show?id=705844%3ABlogPost%3A148030&commentId=705844%3AComment%3A148074)是一個教程。

## 沒有 FTDI 數據線，但使用 ArduPilot Mega ##

如果你用帶有 IMU 板的 APM，並且沒有 FTDI 數據線, 你可以用 IMU 板內建的 USB 連接與 uBlox模塊通信。

使用下面這個簡單的 Arduino 程序將 USB 插頭上的輸入/輸出轉發給 GPS:
```
void setup()
{
	pinMode(19, INPUT);    //RX1
	pinMode(18,OUTPUT); //TX1
	pinMode(0,INPUT);      //RX0
	pinMode(1,OUTPUT);  //TX0
}
void loop()
{
	digitalWrite(18,digitalRead(0)); // RX0 --> TX1
	digitalWrite(1,digitalRead(19)); // TX0 <-- RX1
}
```
上傳該程序，將 APM+shield 連到電腦上，用你的終端程序或者 GPS 工具連接到 USB 串口上，波特率為 38400。GPS 應該正常工作。一旦配置第一次上傳之後，你要修改程序中的波特率，再上傳一次。重啟 u-center, 然後再操作。

(Thanks to Patrick Lemli for the above)