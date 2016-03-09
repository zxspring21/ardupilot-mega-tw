# 重刷或更新 MediaTek GPS 固件 #
這個過程十分簡單，只需要將 GPS 模塊與電腦相連，再運行一個桌面程序。

## 步驟1: 連接 GPS ##

要連接 GPS, 你需要一條 FTDI 數據線和將其連接到 GPS 的接線。你可以用 DIY Drones 的 GPS-to-FTDI 線或者自己做一條。

下面的步驟說明了如何自己做一條連線。如果你用做好的線，直接跳到步驟 2。

你需要至少 8 針排針，4 根母頭-母頭杜邦線或者 2 根母頭-母頭舵機線。

將 4 針排針焊接到 MediaTek 模塊的底部焊盤上，如下圖所示:

http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/IMG_4843.JPG

將一些獨立的插針插到 FTDI 線的插頭上，然後用杜邦線將 GPS 模塊與 FTDI 線相連，如下圖所示 (GPS GND->FTDI 黑線, GPS 5V->FTDI 紅線, GPS Out->FTDI 黃線, GPS in -> FTDI 橙線).

http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/IMG_4842.JPG

## 步驟2: 上傳新固件 ##
在[這裡](http://code.google.com/p/ardupilot/downloads/detail?name=MTK_DIYdrones.zip&can=2&q=)下載固件更新工具。解壓縮文件，遵照 MediaTek\_Programming.pdf 文件中的說明。

最新的固件版本為 v1.6 可以在[這裡](http://api.ning.com/files/taDZ5KJK**s3X*OdmnVy2mgVbaAZX0TpLaZYkQVvQi2GMhS-gID*N6S6rC5svYewSZfjdABxz3GnRehzr4OQmA__/AXN1.30_2389_3329_384.1151100.1_v16.bin)下載。 如果出於某些原因(例如當你使用不支持1.6版固件的 ArduIMU時)，你想使用原來的 1.4 版固件，它包含在上面固件更新工具的連接裡。

MediaTek 1.6 版協議說明在[這裡](http://api.ning.com/files/SESMnS0zwc0m0TFQCS8CVetPAiRGMczDWuIzq3vcAM1t2*Y64HogW6zW-qoYU-lcMr0VEGGKAGocldXgkQjQtw__/CustomizeFunctionSpecificationv16.doc)。