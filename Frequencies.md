== 挑選頻率的技巧 ==

![http://wiki.ardupilot-mega.googlecode.com/git/images/3DRadio/3DR-radio-kit-dip-small.jpg](http://wiki.ardupilot-mega.googlecode.com/git/images/3DRadio/3DR-radio-kit-dip-small.jpg)

無線是一個黑色的藝術，並有一系列令人眼花繚亂的標準和選擇。這裡有一些簡單的指導方針，可以幫助你明智地選擇:

**RC和業餘 UAV 設備通常運作在這些頻率範圍:**
  1. 35 MHz (older analog RC gear in Europe)
  1. 72 MHz (older analog RC gear in the US)
  1. 433 MHz (RC and telemetry, in Europe)
  1. 900-915 MHz (video and telemetry, in the US)
  1. 1.3 GHz (video)
  1. 2.4 GHz (digital RC gear, video and telemetry)
  1. 5.8 GHz (video)

  * 讓發射器及接收器在相同的頻率範圍是個\*壞主意**，所以你要甚選你的設備來避免這點。即使他們使用不同的頻率，請試著讓發射器(telemetry, video)及接收器(RC, GPS)的頻率盡可能的遠離。你唯一要考慮的是板上的兩種無線電如果它們是數位擴頻無線電就會共享相同的頻率，例如 2.4 GHz 的範圍內。
  * 一般而言，較低的頻率會有較長的範圍，因為它可以繞過障礙物的能力更好，所以如果 900 MHz 視訊往往會比 2.4 GHz 的視訊有更長的範圍。但是數位傳輸技術，可以彌補這一點，所以它不是一個硬性及快速的法則。例如， 一個高端(high-end)擴頻 2.4 GHz無線視頻設置可以超越一個低端(lower-end) 900 MHz。
  * 某些頻率範圍是比別人更加擁擠。例如，在室內，在城市環境中 2.4 GHz 相當的竸爭從 WiFi 到 Bluetooth t到無線話機。而 900 MHz 則只有某些無線話機使用。
  * 1.3 GHz 的頻率則非常接近 GPS 的衛星發射頻率，它會降低你的 GPS 性能。如果你是使用 1.3 GHz 的發射器，儘量讓它遠離你的 GPS 模組。**

### 下面是一些建議的配置: ###

| | **RC** | **Telemetry** | **Video** |
|:|:-------|:--------------|:----------|
| Configuration 1 (US) | [2.4Ghz](http://store.diydrones.com/product_p/rc-spektrum-dx7-01.htm) | [915 Mhz](http://store.diydrones.com/3DR_RadioTelemetry_Kit_915_Mhz_p/kt-telemetry-3dr915.htm) | [5.8 Ghz](http://store.diydrones.com/5_8Ghz_500mW_Wireless_Video_Transmitter_Receiver_p/wi-ts352.htm) |
| Configuration 2 (Europe) | [2.4Ghz](http://store.diydrones.com/product_p/rc-spektrum-dx7-01.htm) | [433Mhz](http://store.diydrones.com/3DR_RadioTelemetry_Kit_433Mhz_p/kt-telemetry-3dr433.htm) | [5.8 Ghz](http://store.diydrones.com/5_8Ghz_500mW_Wireless_Video_Transmitter_Receiver_p/wi-ts352.htm) |
| Configuration 3 (US) | [2.4Ghz](http://store.diydrones.com/product_p/rc-spektrum-dx7-01.htm) | [915 Mhz](http://store.diydrones.com/3DR_RadioTelemetry_Kit_915_Mhz_p/kt-telemetry-3dr915.htm) | 1.3 Ghz   |
| Configuration 4 (Europe) | [2.4Ghz](http://store.diydrones.com/product_p/rc-spektrum-dx7-01.htm) | [433Mhz](http://store.diydrones.com/3DR_RadioTelemetry_Kit_433Mhz_p/kt-telemetry-3dr433.htm) | 1.3 Ghz   |