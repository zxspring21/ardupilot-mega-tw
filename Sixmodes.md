== 設定RC發射器的6種模式 ==


如果你想要有六種模式，你也許需要依照下面的方法設定，這通常要在你的發射器上混合一個雙動撥動開關和一個3動撥動開關，設定開關由(es)到(ideally)產生 PWM 脈衝寬度為 1165、1425 及 1815 微秒(uSec)或 1165、1295、1425、1555、1685 以及 1815 毫秒(ms)。(如果你有的話也可以使用類比撥動，但它很難真正地把它轉換成6個不同的位置)。

你怎麼能知道什麼是PWM脈衝寬度？使用 [CLI](http://code.google.com/p/ardupilot-mega/wiki/CLI) 去執行 [無線電測試](http://code.google.com/p/ardupilot-mega/wiki/RCinput)。

這裡有些使用者提供各種RC系統的教學(或使用雙動開關加入某些模式到RC)：
  * [JR XG8 DMSS](http://www.diydrones.com/forum/topics/how-to-set-up-6-apm-flight-modes-on-1-channel-of-jr-xg8-rc)
  * [JR9303](http://diydrones.com/profiles/blogs/how-to-program-6-flight-modes)
  * [JR X2720](http://diydrones.com/forum/topics/six-flight-modes-can-be-done)
  * [Futaba 9C Super](http://diydrones.com/profiles/blogs/6-positions-for-futaba-9c-super)
  * [Futaba T8FG](http://diydrones.com/profiles/blogs/acmapm-futaba-t8fg-super-mode)
  * [Futaba T7CP](http://diydrones.com/profiles/blogs/configure-6-flight-modes-for)
  * [Futaba T6EX](http://diydrones.com/profiles/blogs/four-modes-switch-for-futaba)
  * [Futaba 12fg](http://diydrones.com/profiles/blog/show?id=705844%3ABlogPost%3A371155)
  * [Futaba 9ZAP/ZHP](http://diydrones.com/profiles/blogs/flight-mode-switching-on-a)
  * [Futaba T10CAG](http://www.diydrones.com/profiles/blogs/getting-six-fly-modes-on-futaba-t10cag-transmitter)
  * [Futaba T14](http://diydrones.com/profiles/blogs/futaba-t14-mz-mode-configuration-for-all-6-modes)
  * [Graupner MX-16](http://diydrones.com/profiles/blogs/six-modes-with-graupner-mx-16)
  * [Turnigy 9x](http://diydrones.com/profiles/blogs/configuring-turnigy-9x-with-arducopter)
  * [Turnigy 9x with ER9x firmware](http://diydrones.com/profiles/blogs/mode-switch-setup-for-turnigy)
  * [Hitech Aurora 9](http://www.diydrones.com/forum/topics/quad-goes-to-full-throttle?commentId=705844%3AComment%3A374944)
  * [Spektrum DX6i](http://www.diydrones.com/profiles/blogs/5-flying-modes-with-a-spektrum)
  * [Spektrum DX8](http://diydrones.com/profiles/blogs/spectrum-dx8-2-switches-1-tx-channel-6-flight-modes?)
  * [Spektrum DX7](http://diydrones.com/profiles/blog/show?id=705844%3ABlogPost%3A637661)
  * [Spektrum DX7s](http://diydrones.com/profiles/blogs/getting-6-modes-out-of-channel-5-on-a-spektrum-dx7s)

Or [建立你的六動開關](http://diydrones.com/profiles/blogs/6-position-mode-switch-for-apm)!