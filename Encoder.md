= 獨立的 PPM 編碼器 =

PPM 編碼器最多可以將 8 個 PWM (pulse width modulated)訊號編碼成 1 個 PPM (pulse pause modulated)訊號。
這樣你就可以使用任何 R/C 接收器以及支援 PPM 的微處理器(例如：[http://pixhawk.ethz.ch/px4/modules/px4fmu PX4FMU)。
設計是基於 ATMEGA328P 以及一個外部 16Mhz 的共振器。

3DR PPM 編碼器 (v2) 現在所使用的是 ArduPPM 的韌體，替代之前的 Paparazzi PPM 編碼器韌體。新的 ArduPPM 韌體已經從新設計，以提高性能及穩定性，並且更符合我們現在及未來的需求。

## 設置說明 ##

**[設置說明書](http://ardupilot-mega.googlecode.com/files/PPM%20Encoder%203DR%20Manual%20v2.3.16.pdf)會教你 PPM 編碼器如何焊接及接線，並且說明安全回復模式的差異。**

## 重新燒錄 Atmega328p PPM 編碼器 ##

**註**: PPM 編碼器上已經預先燒好 PPM 編碼器韌體，大多數的使用者應該不需要修改它。

然而，有些使用者可能想要知道變更 PPM 編碼器解譯 RC 訊號的方式或者也有可能會想要更新為最新版本。
有些少數的使用者回報說有接收器與舊版本相容性的問題(在 ArduPPM 之前)。大多數的品牌，ArduPPM 皆有支援。

ArduPPM 是新一代韌體的正式名稱。它是完全從頭開始以可靠度為最高指導原則的設計。
編碼器韌體的正式發佈在 Downloads 頁面的 ArduPPM\_Vx.x.xx\_ATMega328p.hex。
官方原始碼在 Git 程式儲庫中 :
http://code.google.com/p/ardupilot-mega/source/browse/#git/Tools/ArduPPM/ATMega328p。
獨立的 PPM 編碼器需使用 the ATMega328p 的版本。

準備燒錄，連接 PPM 編碼器到一台 AVR 燒錄器，例如 AVRISP mkII:

![http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPPM/reprogramming_the_standalone_ppm_encoder.jpg](http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPPM/reprogramming_the_standalone_ppm_encoder.jpg)

燒錄時，請確認 PPM 編碼器有接上 5V 的電源。

### 如何在 Windows 環境中重燒韌體 ###

下載並安裝最新版本的 [WinAVR](http://sourceforge.net/projects/winavr/)。

Plug in the AVRISP mkII and Install the drivers for AVRISP mkII as follows:

開啟裝置管理員找到 AVRISP mkII，選擇"更新驅動程式..."

![http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPPM/windows_install_avrispmkii_driver_1.png](http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPPM/windows_install_avrispmkii_driver_1.png)

選擇 "Browse my Computer for driver software"

![http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPPM/windows_install_avrispmkii_driver_2.png](http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPPM/windows_install_avrispmkii_driver_2.png)

到 WinAVR 的資料夾安裝(例如 C:\WinAVR-20100110\)

![http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPPM/windows_install_avrispmkii_driver_3.png](http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPPM/windows_install_avrispmkii_driver_3.png)

![http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPPM/windows_install_avrispmkii_driver_4.png](http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPPM/windows_install_avrispmkii_driver_4.png)

選擇 "Install this driver software anyway"

![http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPPM/windows_install_avrispmkii_driver_5.png](http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPPM/windows_install_avrispmkii_driver_5.png)

安裝成功的畫面如下:

![http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPPM/windows_install_avrispmkii_driver_6.png](http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPPM/windows_install_avrispmkii_driver_6.png)

開啟命令列: 按下 "開始\執行" 輸 cmd 並按下 enter。

![http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPPM/windows_start_cmd.png](http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPPM/windows_start_cmd.png)

使用 cd 命令變更資料夾到你放置 Hex 檔案的地方: 例如 cd Downloads\ 如果它放在 Downloads 資料夾

然後輸入命令: avrdude -P usb -c avrispmkii -p atmega328p -U flash:w:ArduPPM\_Vx.x.x\_PPM\_Encoder.hex (x.x.x 可以替代成你的版本序號)

![http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPPM/windows_cmd_avrdude_1.png](http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPPM/windows_cmd_avrdude_1.png)

如果安完成，就會出現下列這個畫面:

![http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPPM/windows_cmd_avrdude_2.png](http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPPM/windows_cmd_avrdude_2.png)

### 如何在 Mac OS X 環境中重燒韌體 ###

待辦事項: add content on how to flash the hex file here

### 如何在 Linux 環境中重燒韌體 ###

安裝 avrdude:

For Ubuntu:
```
sudo apt-get install avrdude
```

AVRISP mkII 程序指令:
```
avrdude -p atmega328p -P usb -c avrispmkii -U flash:w:ArduPPM_Vx.x.x_ATMega328p.hex
```

應該會輸出:

```
avrdude: AVR device initialized and ready to accept instructions

Reading | ################################################## | 100% 0.00s

avrdude: Device signature = 0x1e950f
avrdude: NOTE: FLASH memory has been specified, an erase cycle will be performed
         To disable this feature, specify the -D option.
avrdude: erasing chip
avrdude: reading input file "ArduPPM_V2.3.0_ATMega328p.hex"
avrdude: input file ArduPPM_V2.3.0_ATMega328p.hex auto detected as Intel Hex
avrdude: writing flash (1952 bytes):

Writing | ################################################## | 100% 0.61s

avrdude: 1952 bytes of flash written
avrdude: verifying flash memory against ArduPPM_V2.3.0_ATMega328p.hex:
avrdude: load data flash data from input file ArduPPM_V2.3.0_ATMega328p.hex:
avrdude: input file ArduPPM_V2.3.0_ATMega328p.hex auto detected as Intel Hex
avrdude: input file ArduPPM_V2.3.0_ATMega328p.hex contains 1952 bytes
avrdude: reading on-chip flash data:

Reading | ################################################## | 100% 0.56s

avrdude: verifying ...
avrdude: 1952 bytes of flash verified

avrdude: safemode: Fuses OK

avrdude done.  Thank you.
```


如果有出現錯誤，可以這樣試試。

## 重新編譯的選項 ##

預設狀況下負脈衝的 PPM 已經編碼過。為了要變成正脈衝的 PPM，要將 Tools/ArduPPM/Libraries/PPM\_Encoder.h 的第 158 行註釋掉，由:

```
// #define _POSITIVE_PPM_FRAME_	// Switch to positive pulse PPM
```
變更為
```
#define _POSITIVE_PPM_FRAME_	// Switch to positive pulse PPM
```

### 使用 Linux 重新編譯 ###

這些指令已經在 Ubuntu 中測試過:

```
sudo apt-get install build-essential git-core gcc-avr avrdude
git clone http://code.google.com/p/ardupilot-mega
cd ardupilot-mega/Tools/ArduPPM/
```

現在可以編輯 ATMega328p/Encoder-PPM.c 或 Libraries/PPM\_Encoder.h

```
cd ATMega328p/
make clean
make
```

並且你應該有客制化的 hex-file 可用於這個程序:

```
avrdude -p atmega328p -P usb -c avrispmkii -U flash:w:Encoder-PPM.hex
```