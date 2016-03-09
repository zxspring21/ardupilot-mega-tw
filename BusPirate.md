# 使用 AVRDUDE 和 Bus Pirate 燒錄 Atmega328p (PPM 編碼器/失效保護) #

[Bus Pirate](http://dangerousprototypes.com/docs/Bus_Pirate) 是一個多功能的、低成本的多協議黑客工具。在它眾多的功能之中，它可以與 AVRDUDE 一起燒錄 ATMega328p (以及很多其他 AVR 設備)。

## 獲取部件 ##

你可以從下列地方買到 Bus Pirate:

  * [Adafruit](http://www.adafruit.com/index.php?main_page=product_info&cPath=8&products_id=237)
  * [SeeedStudio](http://www.seeedstudio.com/depot/bus-pirate-v3-assembled-p-609.html?cPath=61_68)
  * [SparkFun](http://www.sparkfun.com/commerce/product_info.php?products_id=9544)

### Mac OSX 上的 AVRDUDE ###

獲取 Mac OSX 上的最新 AVRDUDE 軟件的方法是使用 [MacPorts](http://macports.com)。在安裝 MacPorts 之後, 安裝 AVRDUDE 非常簡單:

```
# sudo port install avrdude
```

確保 `/opt/local/bin` 在可執行文件查找路徑(path變量)中。

### Linux上的 AVRDUDE ###

多數 Linux 發行版都有 AVRDUDE 的安裝包。查看你的發行版的關於尋找和安裝包的文檔。

### Windows 上的 AVRDUDE ###

獲取Windows 上的 AVRDUDE 的最簡單的方法是安裝 [WinAVR](http://winavr.sourceforge.net/)。
_Some more detail here would be nice_

### Arduino 中的 AVRDUDE ###

Arduino 環境用一個私有的 AVRDUDE 來編程。你可以在 Arduino 的安裝目錄中找到 AVRDUDE 和相關配置文件。如果你要這麼幹的話，你要再命令行中用 -C 選項提供配置文件的路徑。

## 設置 Bus Pirate ##

讓 Bus Pirate 與 AVRDUDE 一起工作有兩種方式。第一種是使用'原生'模式，第二種是往 Bus Pirate 裡上傳一個新固件，讓它模擬 Atmel STK500。(注意如果你用 Bus Pirate 模擬 STK500  的話，還可以不用 AVRDUDE，而改用!AVRStudio)。

兩種方式唯一的差別是你需要告訴 AVRDUDE 它正與誰交互 (目前作者發現 Bus Pirate v3 和 v5.4固件上的'原生'模式無法工作，儘管在 AVRDUDE svn 的 r946上修正了這個問題)。

### 安裝 STK500 模擬器固件 ###

如果你想用 Bus Pirate 模擬 STK500, 參考 [Bus Pirate wiki](http://dangerousprototypes.com/docs/STK500_v2_AVR_programmer_clone) 中的說明。

### 連接 Bus Pirate 與 ArduPilot Mega ###

![http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/BusPirate.jpg](http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/BusPirate.jpg)

在上圖中，我們用 [SparkFun 的 Bus Pirate 數據線](http://www.sparkfun.com/commerce/product_info.php?products_id=9556)連接 Bus Pirate。 [SeeedStudio 數據線](http://www.seeedstudio.com/depot/preorder-bus-pirate-probe-kit-p-526.html)上顏色標記相同。

|Bus Pirate 引腳| AVR ISP 引腳 # |
|:------------|:-------------|
| MISO        | 1 (方焊盤)      |
| 3v3         | 2            |
| CLK         | 3            |
| MOSI        | 4            |
| CS          | 5            |
| GND         | 6            |

## 燒錄 ATMega328 ##

從[這裡](http://code.google.com/p/ardupilot-mega/downloads/detail?name=PPM_encoder.zip&can=2&q=)下載 PPM 編碼器文件。解壓縮文件，找到裡面包含的 `firmware.hex` 文件。

連上 Bus Pirate，檢查一切工作正常。你要確定 Bus Pirate 使用的串口號，方法和確定 Arduino 用的一樣。注意如果你使用 Bus Pirate 的'原生'模式, 使用 `-c buspirate`。

```
# avrdude -p m328p -c stk500 -P <serial port>

avrdude: AVR device initialized and ready to accept instructions

Reading | ################################################## | 100% 0.09s

avrdude: Device signature = 0x1e950f
avrdude: current erase-rewrite cycle count is 775041024 (if being tracked)

avrdude: safemode: Fuses OK

avrdude done.  Thank you.
```

在以上過程正確工作之後，就可以燒錄新的固件了:

```
# avrdude -p m328p -c stk500 -P <serial port> -U firmware.hex

avrdude: AVR device initialized and ready to accept instructions

Reading | ################################################## | 100% 0.09s

avrdude: Device signature = 0x1e950f
avrdude: NOTE: FLASH memory has been specified, an erase cycle will be performed
         To disable this feature, specify the -D option.
avrdude: current erase-rewrite cycle count is 775041024 (if being tracked)
avrdude: erasing chip
avrdude: reading input file "/Users/msmith/Downloads/PPM_encoder/firmware.hex"
avrdude: input file /Users/msmith/Downloads/PPM_encoder/firmware.hex auto detected as Intel Hex
avrdude: writing flash (2736 bytes):

Writing | ################################################## | 100% 0.90s

avrdude: 2736 bytes of flash written
avrdude: verifying flash memory against /Users/msmith/Downloads/PPM_encoder/firmware.hex:
avrdude: load data flash data from input file /Users/msmith/Downloads/PPM_encoder/firmware.hex:
avrdude: input file /Users/msmith/Downloads/PPM_encoder/firmware.hex auto detected as Intel Hex
avrdude: input file /Users/msmith/Downloads/PPM_encoder/firmware.hex contains 2736 bytes
avrdude: reading on-chip flash data:

Reading | ################################################## | 100% 0.71s

avrdude: verifying ...
avrdude: 2736 bytes of flash verified

avrdude: safemode: Fuses OK

avrdude done.  Thank you.
```

拆下 Bus Pirate，恢復它的原始固件(如果需要的話)。重新組裝 ArduPilot Mega，檢查編碼器是否正常工作。