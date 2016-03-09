## ArduPilot Mega IMU 板硬件 ##


![http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/APM-IMU.png](http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/APM-IMU.png)

兩個擴展端口連接到 ATmega1280 的 PF6 和 PF7 引腳。在 Arduino 中它們是 Analog 5 和 6。

_注: ArduPlane 或 ArduCopter 軟體已不使用這些滑塊開關，如果需要的話，可以透過程式為用戶創建。_

### 特性 ###

  * 兩個3.3V穩壓器。(一個專門用於模擬傳感器)
  * 一個繼電器，用來控制相機、燈光繼電器或其他載荷
  * 12位模/數轉換器，提供更高的陀螺/加速度/空速信號解析度
  * 內嵌16MB數據記錄器（黑盒）
  * 雙列直插撥動開關，控制舵機反向或用戶自定義功能
  * 內嵌FTDI控制器，原生支持USB
  * 專用調製解調器/屏幕顯示（OSD）端口
  * I2C端口，帶有菊鏈環輸入板，支持自建的傳感器陣列
  * 兩個用戶可編程的按鍵 (一個輕觸式，一個滑動式)
  * 10位模擬擴展端口
  * 重啟按鈕
  * 可選的直插電阻分壓器（易於焊接）
  * 大量狀態指示LED
  * 新的抗震動的Invensense陀螺儀（三軸）
  * Analog Devices 的 ADX330加速度計.
  * 空速傳感器端口（可選，單獨焊接）
  * 博世的絕對壓力傳感器和溫度傳感器，精確計算高度（是的，你也可以把板子當作一個天氣記錄器！）


### PCB 文件 ###

IMU 板的 Eagle 文件:
  * [Schematic and Board files](http://stuff.storediydrones.com/ArduPilotMegaShield_H_v11_filterjumpers-listing.rar)

IMU 板的 pdf 文件:

  * [電路圖](http://api.ning.com/files/nfmYLuaRC5oDAQoRvwY5vV1rR2Jhh7JTPs--BEVI2oGa1S6rhK-EwvG2DYIwBcjBk6EU940BlUYu1Rf9NhTmuw__/ArduPilotMegaShield_F_v141_schema.pdf)
  * [PCB板](http://api.ning.com/files/bbEDt9VgZxxCPPFEYEuPdce-ZkJVz3ZsiHg0rBaw6f3I8CGpN2iQfD5b41dp27M0n7esr60GxvpsPnIBjMStvg__/ArduPilotMegaShield_F_v141_board.pdf)


## 針腳定義 ##

說明所有針腳排列和功能的文件在[這裡](https://spreadsheets0.google.com/ccc?key=t2UjzAY9aBvnXBuw2AFgAnQ&authkey=CKzJv_IP&hl=en#gid=0)