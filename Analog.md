# 增加其他類比感應器 #

ArduPilotMega 有兩個空閒的端口可以增加類比感應器。如圖所示，它們在 IMU 板的這個地方.

![http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/expansion.png](http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/expansion.png)

數據可以從 Arduino 的 Analog 6 和 Analog7 讀出。下面是一個讀取的例子:

```
int val1 = 0;           // 存儲讀取值的變量
int val2 = 0;

void setup()
{
  Serial.begin(9600);          	// 設置串口
}

void loop()
{
  val1 = analogRead(6);    		// 讀取輸入
  Serial.print("Analog 6: ");
  Serial.print(val1);           // 顯示值
  val2 = analogRead(7);    		// 讀取輸入
  Serial.print("  Analog 7: ");
  Serial.println(val2);         // 顯示值

}

```