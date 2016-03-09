== APM 2.5 板總覽 ==

APM 2.5 在出廠時就已經焊接完成，你只需要使用 Mission Planner 載入你想要的韌體即可。 **先不要急著將它插到你電腦的 USB，我們下個步驟才會這麼做。** 這邊只是單純介紹這塊板子。

http://wiki.ardupilot-mega.googlecode.com/git/images/APM25encl.JPG

打開盒子你會發現與[APM 2.0 板](http://code.google.com/p/ardupilot-mega/wiki/APM2board)的不同:

![http://wiki.ardupilot-mega.googlecode.com/git/images/apm25.3.jpg](http://wiki.ardupilot-mega.googlecode.com/git/images/apm25.3.jpg)

RC 接收器的通道會接在輸入端(Input)，伺服機或 ESC 會接在輸出端(Output)。最高支援8個通道的輸入及輸出，如果需要的話也都還能依下列的說再進行擴展。

APM 2.5 板的供電埠的連接器內含電力模組。雖它可能比較無法相信，但是你也可以使用 ESC 供電給它或者一個外接式的 5v 電源。如果你選擇使用替代的電源，你就會需要使用 JP1 的跳線，以及左側新的二極體標計的地方。如果你想要了解其他的替代電源規劃，請參考附錄[這裡](http://code.google.com/p/ardupilot-mega/wiki/APM25Power)的說明。

連接器的排針，對於大多數人來說應該是正確的。如果你要加入更多的感應器，在上側(A0 to A8)會有 9 個埠可供你使用。