## 最簡單的燒錄 Atmega328p (PPM 編碼器/失效保護) 的方法 ##


## 你需要 ##

唯一需要的硬件是一個 AVR ISP MKII 燒錄器, 廠家編號是 ATAVRISP2。你可以在[DigiKey](http://search.digikey.com/scripts/DkSearch/dksus.dll?Detail&name=ATAVRISP2-ND), [Mouser](http://mouser.com/ProductDetail/Atmel/ATAVRISP2/?qs=2mdvTlUeTfBRoycsKqwYpg%3d%3d) 或者 [Farnell](http://uk.farnell.com/atmel/atavrisp2/programmer-avr-mcu-isp/dp/1135517?Ntt=ATAVRISP2)買到:

![http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/d972wmb_7f27p3nhb_b.jpg](http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/d972wmb_7f27p3nhb_b.jpg)

軟件包括:
  1. 從[這裡](http://www.atmel.com/forms/software_download.asp?family_id=607&fn=dl_AvrStudio4Setup.exe)下載並安裝 AVRStudio 4.xx (必須註冊)。 鏈接在[這裡](http://www.atmel.com/dyn/products/tools_card.asp?tool_id=2725)。安裝過程中確保選上了 "Install Jungo Drivers", AVR燒錄器需要該驅動。
  1. 從[這裡](http://sourceforge.net/projects/winavr/files/)下載並安裝 WINAVR, 這允許你用 C++ 語言編寫 AVR 設備的程序 (順便說一句，這實際上就是 Arduino 的核心), 編譯 PPM 編碼器源代碼，用AVR ISP燒錄器上傳固件。下載最新的".exe"版本。
  1. 像往常一樣用你的電調或者遙控設備為板子供電。可以隨便插到哪個通道上。
  1. 將 AVR 燒錄器連接到 APM 板子 的Atmega 328 SPI 插頭上，如圖所示(你可以將插針焊到板子上，或者插到燒錄器的插頭上，然後壓在 APM 的接口上):

http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/IMG_4840.JPG

Ardupilot 板 ISP 連接器圖解 :

![http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPPM/Programming_the_Atmega328p.jpg](http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPPM/Programming_the_Atmega328p.jpg)


## 自動過程 ##


從[這裡](http://ardupilot-mega.googlecode.com/files/PPM_encoder.zip)下載 PPM 編碼器文件。解壓到桌面上。如果你用 64位 windows 系統, 你需要修改 "firmware\_arduino\_328\_16mhz.bat" 文件，把路徑改為 "Program Files (x86)"。例如: "C:\Program Files (x86)\Atmel\AVR Tools\STK500\Stk500.exe"。如果你用普通的 32位系統，就不用修改了。

**可以在下載的文件中使用 ArduPPM 版本取代 firmware.hex 檔案。可使使用下載檔案的 checksum 檢查 SHA1 是否和原來的 SHA1 相同。你可以在下載的文件中點擊檔取得 SHA1 。**

http://code.google.com/p/ardupilot-mega/downloads/list

現在點擊批處理文件。它會在一個 DOS 窗口中運行。按任意鍵，可以看到下面的結果：

![http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/batch.png](http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/batch.png)

它將報告燒錄成功，然後就搞定了!

閱讀 ArduPPM 手冊和檢查藍色狀態指示燈看看解碼是正確的。有很好的做法就是使用 Mission Planner 做深層的檢查 - 原始的感應器資料 - 無線電子視窗或起飛前使用 CLI 無線電測試。