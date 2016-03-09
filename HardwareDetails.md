## ArduPilot Mega 硬件 ##

![http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/IMU1.jpg](http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/IMU1.jpg)

ArduPilot Mega 是一個 Arduino Mega 兼容的自動駕駛儀。它包括兩個板子:

  1. 一片主板，包括 Atmega1280 或 Atmega2560 處理器, 以及一個用來充當遙控接口的 Atmega328 協處理器。詳細說明在[這裡](Hardware.md)。
  1. 一個 "蓋板" 或第二板，蓋在主板上面。包括從陀螺儀和加速度計到氣壓和電壓傳感器的一系列傳感器。它充當一個慣性測量單元(IMU)。詳細說明在[這裡](IMUHardware.md)。