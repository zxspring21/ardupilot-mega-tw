## 原廠 ArduPilot 地面站 ##

![http://wiki.ardupilot-mega.googlecode.com/git/images/gcs.png](http://wiki.ardupilot-mega.googlecode.com/git/images/gcs.png)

## 特性 ##

本地面站只支持 Windows 系統，包括一下特性:

  * 移動 3D 地圖
  * 語音報告任務事件，因此你可以一直盯著飛機
  * 任務自動保存為 KML 格式, 可以在 Google Earth 上重放

## 軟件安裝 ##

你需要:

  * [地面站程序](http://code.google.com/p/ardupilotgcs/downloads/list)。下載zip文件，解壓到桌面上。
  * [LabView 運行時引擎](http://joule.ni.com/nidu/cds/view/p/id/1383/lang/en)和 [串口驅動](http://joule.ni.com/nidu/cds/view/p/id/2185/lang/en)。
  * 你還要安裝 [Google Earth](http://earth.google.com/intl/en/download-earth.html)。

按順序下載並安裝以上文件。然後可以運行`GroundControlStation.exe`。

## 配置APM ##

首先, 你必須配置 APM 軟件，讓它輸出正確的遙測數據流。在 `APM_Config.h` 文件中，增加下面的代碼行，選擇正確的地面站格式:

```
// GCS_PROTOCOL
#define GCS_PROTOCOL			GCS_PROTOCOL_LEGACY
```

你還需要告知 APM 用哪個串口發送數據。

如果你想通過 USB 線觀察數據，則選擇端口0，增加以下代碼行:

```
// GCS_PORT
#define GCS_PORT 0
```

如果你想觀察空中飛行時的數據（常用情況），你需要通過[無線模塊](Wireless.md)發送數據。無線模塊的端口為3:

```
// GCS_PORT
#define GCS_PORT 3
```


---


## 運行地面站 ##

確保地面端的 Xbee 和 USB 適配器連好並插上了電腦。在地面站的設置（Setup）頁中, 選擇正確的串口和速率。如果你用 APM 端口0和 USB傳輸線，選擇 115,200。如果你用 Xbee 和遙測端口（APM 端口 3），選擇 57,600。

如果你不清楚 USB 傳輸線 或 Xbee 對應的串口，在 Windows 設備管理器中查看。

http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/LegacyGCS.PNG

如果 APM 處於飛行模式 （滑動開關朝向 GPS 插頭）, 你可以在地面站看見實時數據。在 GPS 鎖定之前不會得到 GPS 數據。

如果打開揚聲器，可以聽到 APM 狀態的語音報告。這在飛場是飛場方便的，你可以一直盯著飛機！

**注:** 如果你在歐洲，使用逗號而不是小數點，那麼需要修改 Windows 設置。在控制面板中，打開區域和語言選項，單擊個性化。在數字格式中，單擊用小數點替換逗號。單擊"應用"，然後重啟電腦。（譯註：這段與當前Windows版本不符，不過反正也沒人在歐洲，不管了）

更多的軟件說明文檔在[這裡](http://code.google.com/p/ardupilotgcs/wiki/Overview?tm=6)。