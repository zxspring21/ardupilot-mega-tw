## 飛行模式 ##

你可以設置你的遙控系統，使用模式選擇通道從3個模式或6個模式中選擇一種模式（不同的模式描述在[這裡](FlightModes.md)）。如果你的發射器有一個三段開關的話，選擇3種模式是很容易的。在首次飛行前，你必須使用 [CLI](CLI.md) 設置飛行模式，否則所有的模式都被設為手動飛行。

在 CLI 中，選擇 Setup，然後選擇 Modes。將你的遙控觸發開關移動到你要設置的位置，然後左右移動副翼搖桿，選擇相應的模式。然後把開關移動到其他位置，設置相應的模式。設完之後，按回車鍵保存並退出。

下面是一個例子:

![http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/modes_cn.png](http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/modes_cn.png)

如果你想有6種模式，你可能要設置你的遙控發射器。通常可以用一個二段開關和一個三段開關的混控來完成上述功能。設置你的遙控開關，產生以下脈寬的脈衝：1165, 1295, 1425, 1555, 1685, 和 1815 毫秒。(你也可以用一個模擬旋鈕來產生相應脈衝，但是要每次都恰好擰到6個位置中的某一個太難了)。

我怎麼知道脈衝的脈寬是多少？使用 [CLI](CLI.md)，運行 [遙控測試](RCinput.md)。

下面是在不同遙控系統上的一些設置教程：
  * [JR9303](http://diydrones.com/profiles/blogs/how-to-program-6-flight-modes)
  * [JR X2720](http://diydrones.com/forum/topics/six-flight-modes-can-be-done)
  * [Futaba T8FG](http://diydrones.com/profiles/blogs/acmapm-futaba-t8fg-super-mode)
  * [Futaba T6EX](http://diydrones.com/profiles/blogs/four-modes-switch-for-futaba)
  * [Futaba 12fg](http://diydrones.com/profiles/blog/show?id=705844%3ABlogPost%3A371155)
  * [Futaba 9ZAP/ZHP](http://diydrones.com/profiles/blogs/flight-mode-switching-on-a)
  * [Turnigy 9x](http://diydrones.com/profiles/blogs/mode-switch-setup-for-turnigy-1)
  * [Turnigy 9x with ER9x firmware](http://diydrones.com/profiles/blogs/mode-switch-setup-for-turnigy)
  * [Hitech Aurora 9](http://www.diydrones.com/forum/topics/quad-goes-to-full-throttle?commentId=705844%3AComment%3A374944)
  * [Spektrum DX6i](http://www.diydrones.com/profiles/blogs/5-flying-modes-with-a-spektrum)
  * [Spektrum DX8](http://diydrones.com/profiles/blogs/setting-up-the-spektrum-dx-8)

或者[build your own six-position switch](http://diydrones.com/profiles/blogs/6-position-mode-switch-for-apm)!