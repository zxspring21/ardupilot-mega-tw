== 自動產生航點功能 ==

![http://wiki.ardupilot-mega.googlecode.com/git/images/AutoWPThree.png](http://wiki.ardupilot-mega.googlecode.com/git/images/AutoWPThree.png)

如果你正在進行空中偵查，需要取得大量的圖片以便你之後能夠接合在一起，Mission Planner 有個很方便的功能可以幫助你。我們稱為 AutoWP，它會自動建立航點讓你的 UAV 在某個區域上建立"地毯式搜索"，在既定的航點上觸發你的相機拍照。

要使用這項功能請進入 Flight Planner 畫面並按下滑鼠右鍵，選擇"Draw Polygon"。

![http://wiki.ardupilot-mega.googlecode.com/git/images/AutoWPOne.png](http://wiki.ardupilot-mega.googlecode.com/git/images/AutoWPOne.png)

在你想要拍照的區域規畫一個多邊形，選擇"Auto WP"然後可以使用下列兩種 Grid 或 Grid V2 (第一次啟動會在你的區域的底部，而第二次啟動則會在頂部)

![http://wiki.ardupilot-mega.googlecode.com/git/images/AutoWPTwo.png](http://wiki.ardupilot-mega.googlecode.com/git/images/AutoWPTwo.png)

它會請你選擇一些拍照任務的其他參數，例如什麼樣飛行高度，應該要距離航線、航點多遠。參數的選擇是根據你所使用相機的特點，一般來說，你應該至少要有 20% 的重疊相片，讓拼接軟件的特徵匹配演算法有足夠的共同特點可以運作。

當你完成時，像上圖所示，它會自動建立一個任務。