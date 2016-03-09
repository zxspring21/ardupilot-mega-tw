## 任務規劃 ##

http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/missionplanner2.PNG

**說明**

你可以輸入航點和其他命令（參見下面的完整列表）。在每行的下拉菜單中，選擇需要的命令。列的標題將自動改變，提示需要的數據。經度和緯度可以通過在地圖上點擊來輸入。高度是相對於你的起飛地點的相對值，也就是說，如果你設為100m，它就在你上方100m處飛行。

你可以直接點擊地圖上 Home 的 lat 或 lon 就可以設定定的位置。或者，如果地圖還尚未載入你飛行的地點，你可以直接使用 "Zoom To" 的按鈕搜尋它，也可以在搜尋的框框輸入你的位置，如下所示:

http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/zoom.PNG

注意，如果選上了「絕對高度(Absolute Alt)」復選框，高度值將使用\*海拔高度**，而不是相對於起飛位置的高度。如果沒選上，ALT就是相對高度。**

**Default Alt** 是輸入新的航點時的默認高度。如果你選擇了"Hold Default ALT"，那麼它也是返航模式時的高度；否則飛機將保持切換到返航模式時的高度。

**Verify height** 意味著任務規劃器將使用 Google Earth 地理數據，根據每個航點下地面高度調整飛行高度。因此如果你的航點在山上，選擇該選項時，任務規劃器將根據山的高度增加飛行高度設置。這是一個保證不撞山的好辦法!

當你完成任務設計後，點擊「Write」按鈕，它將發送給 APM 並保存在存儲器中。如果你想確認它是否是你所需要的，點擊 「Read」按鈕。

你可以將任務保存到本地硬碟中。點擊右鍵選擇「Save WP File」按鈕儲存航點，讀取航點則點擊「Load WP File」按鈕。

![http://wiki.ardupilot-mega.googlecode.com/git/images/savewps.png](http://wiki.ardupilot-mega.googlecode.com/git/images/savewps.png)

## 自動排列 ##

你也可以用 Mission Planner 為你建立一個有用的地圖任務，飛機只會來回飛行如"割草機"的方式收集一個區塊的照片。

可以這麼做，在右鍵選單中選擇 Polygon 並在你想要拍攝的地方畫出一個箱型區塊。然後選擇 Auto WP，Grid。依循提示訊息選擇高度及區域。Mission Planner 將會產生像這樣的任務：

![http://wiki.ardupilot-mega.googlecode.com/git/images/grid.jpg](http://wiki.ardupilot-mega.googlecode.com/git/images/grid.jpg)

### 基本航點命令 ###

任務文件看起來有點嚇人，但卻是自駕儀的一種強大的腳本語言。(記住地面站很快將為你處理這一切，很快你就不需要看到這些東西了!)。

你可以加上任意數量的命令，從預定義類型到自定義類型。下面是一些常用的命令:

  * {NAV\_WAYPOINT n/a, 高度, 緯度, 經度}
  * {NAV\_TAKEOFF 仰角, 目標高度}
  * {NAV\_LAND\_WP n/a, 高度, 緯度, 經度}
  * {DO\_JUMP 航點, n/a, 重複的次數, n/a} 到達某一航點並且在那裡回復任務。設定任何大於 1 的重複次數讓任務多次原行。或都設為 -1 為一直不停的重複。可以一直重複任務。
(**Note: DO\_xxx 命令目前需要一個假航點放置之後的命令**<br>
eg:</li></ul>

WAYPOINT_1<br>
DO\_SET\_HOME<br>
WAYPOINT_2<br>

家位置會被設為 WAYPOINT_1 但如果沒有 WAYPOINT_2 則沒有作用。)<br>
<br>
<br>
注意在上面的截圖中，我設計了一個任務，開始時自動起飛至 20 米高度，然後沿3個 100m 高的航點飛行，接著是一個設置降落模式的航點。最後自動降落至 0 米高度，結束任務。<br>
<br>
關於自動起飛和降落，可以參閱<a href='AutoLand.md'>這裡</a>。<br>
<br>
<b>MAVLink 命令語法的詳細手冊在<a href='MAVLink.md'>附錄</a>中。</b>

<h3>提示</h3>

<ul><li>預取: 你可以緩存地圖數據，以便在外場飛行時不需要連接到互聯網。單擊「預取」按鈕，按住 Alt，畫一個框，就可以下載選擇區域內的地圖圖像。<br>
</li><li>網格: 這允許你繪製一個區域（用右鍵），並自動創建航點，覆蓋選擇的區域。<br>
</li><li>把起始地點設置到當前地點也很容易，只要點擊輸入起始地點位置上的「起始地點」標籤，就會自動將起始地點設為當前坐標。<br>
</li><li>點擊右鍵選擇 Measure Distance 就可以量測兩個航點間的距離。