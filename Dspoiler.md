= 差動擾流板 =

## 使用說明 ##

一般的翼型飛機使用2個控制板做為升降舵用於控制 pitch 及 roll。在某些機型，方向舵會被加到控制偏航的翼梢小翼上。利用差動擾流板切割副翼成4個獨立的控制板：一般來說升降舵會保留下來做為 pitch 及 roll，但是偏航控制是利用機翼上其中一側的兩個控制板產生升力，進而控制偏航動作。如果校驗正確，這將確保飛行員在起飛和著陸時可以很平順的使用偏航控制，以及轉向補償(模擬差動副翼)。

| **左偏航是由左機翼的阻力誘發:** | **右偏航是由右機翼的阻力誘發:**|
|:-------------------|:------------------|
| <img src='http://wiki.ardupilot-mega.googlecode.com/git/images/4surfLeftYaw.jpg' width='440px' height='330px'> <table><thead><th> <img src='http://wiki.ardupilot-mega.googlecode.com/git/images/4surfRightYaw.jpg' width='440px' height='330px'></th></thead><tbody></tbody></table>

<h2>設置</h2>

<h3>準備</h3>

如要運用差動擾流板的功能，你的飛機至少需要4個舵面(每個機翼2片)並且使用副翼的設置方式。在兩側的機翼上使用輸出通道 1(roll)及通道 2(pitch)來設置其中一個舵面做為副翼:<br>
<br>
<b>如果你已經完成，請依下列的教學來妥善設置副翼:</b>
<a href='http://code.google.com/p/ardupilot-mega/wiki/APM2RC'>http://code.google.com/p/ardupilot-mega/wiki/APM2RC</a>

<h3>設定</h3>

一旦你成功設置兩個副翼通道，連接額外的 2 個舵面至 AUX 通道(APM2.X 上的5至11)並設置相對應的 <b>RC_FUNCTION</b>:<br>
<br>
<table><thead><th> <b>參數名稱</b> </th><th> <b>參數編號</b> </th><th> <b>定義</b> </th></thead><tbody>
<tr><td> Differential Spoiler 1 </td><td> 16          </td><td> 這邊的設置是將控制副翼同一側的舵面連接至輸出通道 1 (roll 通道) </td></tr>
<tr><td> Differential Spoiler 2 </td><td>17           </td><td> 這邊的設置是將控制副翼同一側的舵面連接至輸出通道 2 (pitch 通道) </td></tr></tbody></table>

目前為止，你應該可以在 MANUAL 模式中使用一般的副翼功能。現在切換到 FBW 模式並使用 RC 遙控器測試 roll、pitch 及 yaw。調整出正確的 <b>RC_REV</b> 直到飛機的動作符合你的預期。<br>
<br>
<b>註:</b> 有些數位伺服機經過編程後有可能機翼上有任一側的伺服機方向是相反的，或者是旋轉的方向會相反。