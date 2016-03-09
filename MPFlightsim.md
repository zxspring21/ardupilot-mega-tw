## 與 PC 飛行模擬器交互 ##

http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/planner7.PNG

任務規劃器還可以把你的 APM 板子的數據發送給飛行模擬程序，模擬鼠標或搖桿的輸入。這讓你可以在地面精確地模擬 UAV 任務，測試航點和配置，不用擔心會炸機。

"硬件仿真"模擬器的完整說明在[這裡](Sim.md), 本文介紹如何讓任務規劃器充當板子和模擬器之間的橋樑。

任務規劃器支持兩種飛行模擬器，[Xplane](Xplane.md) 和 [FlightGear](FlightGear.md)。選擇你使用的一種。

如果你用的是 Xplane, 你需要修改一些 APM 配置項。在 APM\_Config.h 文件中加上以下代碼 (註釋掉其他已有地面站(GCS)和 GPS 配置):

```
#define ENABLE_HIL ENABLED
#define GCS_PROTOCOL GCS_PROTOCOL_XPLANE
#define GCS_PORT 0
#define GPS_PROTOCOL GPS_PROTOCOL_IMU
#define AIRSPEED_CRUISE 25 // or whatever works best for your Xplane selection
#define AIRSPEED_SENSOR ENABLED
```

打開飛行模擬器，按照[詳細說明](Sim.md)修改相關設置。 在 Xplane 裡選擇飛機時，我們推薦 默認的那架 (PT-60):

http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/pt60.PNG

現在單擊 Connect。假設你的遙控發射器和接收機都已打開並已經連上了 APM, 你就可以用遙控發射器控制模擬器裡的飛機了。如果某個控制反向了，單擊任務規劃器對話框中適當的反向復選框。

你可以用這個程序測試所有的 APM 飛行模式, 包括增穩模式、返航模式和自駕模式。