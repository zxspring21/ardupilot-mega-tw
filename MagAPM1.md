== 幫 APM 1 裝上磁力儀 ==

飛的的方位及機體的朝向(不見得會一樣)對於導航及穩定飛行時的移動是非常重要的資訊。

沒有磁力儀，飛機的方位就無法成功的被 GPS 定位系統及慣性感應器所計算: 感應器的漂移補償是參考 GPS 的地面航向，應該解決當前機鼻的朝向(假設無風或相反的舵面)。

使用磁力儀，我們就不再依靠 GPS 地面航向來糾正感應器的漂移，飛機的方向會變得更準確。如果在飛行時遇到側風，無論是手動或在全自動駕駛控制下， 磁力計將會為感應器的漂移提供更準確的修正。

目前 ArduPlane 的導航在側風時偏航一個筆直的地面軌跡還尚未完成。因為長時間操作時會混淆感應器的漂移校正，所以在飛行時無磁力計就會少一個潛在的問題。

## 連接 DIYDrones 磁力儀 ##

![http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/BR-HMC5843-01-2.jpg](http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/BR-HMC5843-01-2.jpg)

### 方法一: 使用電纜線 ###

你可以將[HMC5843 磁力計](http://store.diydrones.com/product_p/br-hmc5843-01.htm)裝到 APM IMU 板的 I2C 感應器的通訊埠，看起來有點像 GPS 連接器但是"它不是 GPS"。只有一個原因可以這麼做就是你準備以菊花鏈的方式將其他 I2C 感應器連接到你的板子。

有個方法可以修改這個[GPS 電纜線](http://store.diydrones.com/product_p/ca-0001-04.htm)，剪開其中一端的連接器，將線焊到磁力儀右邊的 pad 點。你只能使用六線電纜的其中四條；剩下的可以剪掉。將連接器插入擴充板，在它的下面你應該會看到 "SCL", "SDA", "+5V", "GND" 字樣對應的四條線。磁力計應該也會有相對應的四個腳位，如下圖所示

![http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/magnetometercable.jpg](http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/magnetometercable.jpg)

這裡有安裝完成的圖片(我們建議先將電纜線穿過孔洞再焊接加強固定力):

http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/IMG_4888.JPG

安裝好的照片如下:

http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/IMG_4891.JPG

在接上磁力計前請確認跳線是在 5V 的位置:

![http://wiki.ardupilot-mega.googlecode.com/git/images/Magneto/Mag_HMC5843_jumper.jpg](http://wiki.ardupilot-mega.googlecode.com/git/images/Magneto/Mag_HMC5843_jumper.jpg)

### 方法二: 安裝於板子上 ###

如果你不想使用任何的 4-pin I2C 連接器，你可以真接將磁力計直接裝在擴充板上面。請再次確認電壓跳線是放在 5V 的位置，如上圖所示。

你可以使用 4 pin 的排針。請小心對準磁強計和擴充板的邊緣。這邊用的精準一點你之後會比較省事。

先將磁力計的多餘的地方折斷:

![http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/BR-HMC5843-01-3.jpg](http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/BR-HMC5843-01-3.jpg)

現在，可以焊接 4 Pin 排針(example of the header shown on the table next to the board)。較好的焊接方法是將排針穿過板子並且長Pin向下。

http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/IMG_4889.JPG

最後，將磁力計的\*元件端\*朝向擴充板，如下圖所示:

http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/IMG_4890.JPG

進入 APM 的代碼開啟磁力計的功能，在 Setup Mode 的[CLI](http://code.google.com/p/ardupilot-mega/wiki/CLI)模式下輸入"compass on"， 如下圖所示:

http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/Compasssetting.JPG

進入 CLI 模式的 Test 選單輸入 Compass，你就可以做磁力計的測試。

或者你可以從 APM 程式庫的 APM\_Compass 範例資料夾中載入並執行 APM\_Compass\_test。只需使用 Arduino IDE 的 Serial Monitor(38,400 baud)就可以看到這些資料。

範例資料會如下列所示(只要一移動板就會有數據變化):

```
Heading:23.04  (174,-74,4096)     offsets(-87.00,37.00,-2048.00)
Heading:22.82  (145,-61,4096)     offsets(-87.00,37.00,-2048.00)
Heading:9.62  (177,-30,4096)     offsets(-88.50,37.00,-2048.00)
Heading:7.50  (167,-22,4096)     offsets(-88.50,37.00,-2048.00)
Heading:31.54  (145,-89,4096)     offsets(-88.50,44.50,-2048.00)
Heading:28.94  (132,-73,4096)     offsets(-88.50,44.50,-2048.00)
Heading:15.85  (162,-46,4096)     offsets(-88.50,44.50,-2048.00)
Heading:22.88  (173,-73,4096)     offsets(-88.50,44.50,-2048.00)
Heading:-0.38  (152,1,4096)     offsets(-88.50,44.00,-2048.00)
Heading:15.84  (148,-42,4096)     offsets(-88.50,44.00,-2048.00)
Heading:10.28  (171,-31,4096)     offsets(-88.50,44.00,-2048.00)
Heading:24.47  (145,-66,4096)     offsets(-88.50,44.00,-2048.00)
Heading:40.25  (163,-138,4096)     offsets(-88.50,68.50,-2048.00)
Heading:34.28  (157,-107,4096)     offsets(-88.50,68.50,-2048.00)
Heading:26.72  (147,-74,4096)     offsets(-88.50,68.50,-2048.00)
Heading:51.87  (84,-107,4096)     offsets(-88.50,68.50,-2048.00)
Heading:49.44  (89,-104,4096)     offsets(-88.50,68.50,-2048.00)
```

另外，你可以在 APM 的 CLI 模式下測試感應器，只要在 "test" 選單中輸入 "compass"即可。