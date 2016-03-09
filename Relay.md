## 使用板上繼電開關 ##

你可以使用板上的繼電開關來控制消耗大於數字引腳能夠提供的電流的設備。

繼電器工作的方式是它切換中間的公共引腳與兩側的引腳的連接狀態(狀態 1 或 狀態 2)。因此，假如你想觸發一個電磁閥，你需要將閥門的 V+ 腳練到中間的引腳上，將狀態 1 連到 APM 的 V+，狀態 2 連到地。在狀態 1，電子閥將打開；狀態 2 閥門將關閉。

![http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/relay.jpg](http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/relay.jpg)

這是演示從一個位置切換到另一個位置的代碼.

```
{
	pinMode(RELAY_PIN,OUTPUT);
	
	while(1){
		delay(3000);
	
		Serial.println("Relay Position A");
		PORTL |= B00000100;
		delay(3000);
	
		Serial.println("Relay Position B");
		PORTL ^= B00000100;		
	}
}
```