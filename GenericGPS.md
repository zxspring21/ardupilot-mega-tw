# 配置其他 GPS 模塊 #
如果你有你的 GPS 模塊的配置程序，或者知道使用終端的配置命令，你可以通過 APM IMU 板將 GPS 模塊與電腦相連 (假設你已經把 GPS 模塊和 IMU 板通過合適的連接器連接起來了)。

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
上傳該程序，將 APM+shield 連到電腦上，用你的終端程序或者 GPS 工具連接到 USB 串口上，波特率為 38400。如果 GPS 模塊的波特率為 9600 並工作在 NMEA (ASCII) 模式，數據將正確地從電腦傳入/傳出。如果工作速率不同，更改代碼中的 Serial1.begin 行，設置正確地速率。（譯注: 代碼中沒有Serial1.begin行，原文的代碼應該不完整）