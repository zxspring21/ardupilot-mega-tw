# 用 APM 拍照 #

你是否想用 APM 拍一張類似下面的照片? 在下文中我們將詳細介紹一種辦法，並簡單介紹其他辦法。本文內容包括使用 ArduPilot Mega 和固定翼進行空中靜態照片拍攝。其中一些方法也可以用在其他系統上(例如旋翼機或拍攝視頻)。當然反之亦然——其他網站和論壇上也有很多遙控航拍的建議，可以運用到 APM 之上。

本文和本文提到的方法還處於試驗階段，需要大家協助完成。短的評論可以直接發表在下面的評論中，長篇大論還是建議發表在[論壇](http://www.diydrones.com/forum/topics/photos-with-apm-issues-tweaks)裡。

很抱歉的，本文使用了早期版本的 APM (Beta 1之前)。你可能需要修改一些任務代碼。

![http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/Aerial_Photo_eg2.jpg](http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/Aerial_Photo_eg2.jpg)

## 選擇飛機 ##

可以使用任何有額外動力和升力的飛機。通常中到大型、頭部較大、靜態穩定的飛機可以獲得較好的效果，同時也容易建造。Skywalker 就是滿足以上要求的一個例子。飛翼對拍攝縱向照片較好，同時在有風的天氣中也較好。直升機和[ArduCopter 四旋翼機](http://code.google.com/p/arducopter/)對短距離飛行和小起落場地來說是一個更好的選擇。

## 選擇相機 ##

任何小而便宜的數字相機都是入門（甚至一直使用）的好選擇。不要用帶有光學防抖的相機，大家的結論是它們無法處理螺旋槳的震動，結果就是照片模糊或者視頻搖晃（所謂的"果凍"效應）。重量是一個重要的因素。大多數飛機可以帶動 120 克左右的載荷。使用 200 到 300 克的相機將使飛行和尋找COG變得困難。在買相機之前用一個同等重量的木塊試飛一下，免得花冤枉錢。

## 相機角度 ##

垂直安裝可以獲得一個朝向正下方的視角，這是入門的好選擇。用其他的角度可以獲得更多激動人心的和也易於辨認視角。 與垂直方向偏移40度得到的照片主要是傾斜的地面。偏移70度將得到更多天空風景的照片(來自 [Draganfly](http://www.draganfly.com/news/2008/08/23/rc-aerial-photography-get-great-pictures-tutorial/)).

## 觸發快門 ##

有非常多的方法可以觸發快門。一些方法需要特殊品牌的相機或者很貴的發燒級型號。如果你想研究一下這些方法，參見[Blip](http://blip.com.au/CategoryPhotography.aspx) 或 [rc-airplane-world](http://www.rc-airplane-world.com/rc-aerial-photography.html)。要看一個4英鎊的改裝相機，參見 [這裡](http://diydrones.com/photo/albums/ebay-keychain-camera/)

## 舵機安裝 ##

簡單來說:
用一個9克舵機。預先檢查舵臂的行程。在舵機滿偏時必須完全壓下快門按鈕。在舵機臂上用熱熔膠粘一圈EPO泡沫（比舵機臂寬 2 毫米）。這樣可以保證按下快門時不損壞相機。用熱熔膠將舵機側面粘到相機上，確保舵臂滿偏時能夠按下快門。

注: 舵機安得太遠的話，熱熔膠會裂開，這樣在修復之前就不能再拍照了。

更多地細節和圖片請參見最後一節。

## 相機安裝 ##

相機的安裝既要牢固，又要抑制電機傳來的震動。同時達到兩個目標是很困難的。大家普遍用來將相機安上飛機的方法包括：軟泡沫、硬泡沫、氯丁橡膠管(將相機安在一側), 外科手術導管、橡皮筋、尼龍螺絲(硬連接)和魔術帶。管子主要用在直升機上。我們無法推薦哪種方式最好或者最容易，這取決於你的機身情況。儘管如此，魔術帶加橡皮筋（增加安全性）安裝起來十分快速，同時能夠得到不錯的照片質量。

我們沒有試過這種[軟泡沫支架](http://www.rcgroups.com/forums/showpost.php?p=16196982&postcount=26)，但是它看上去功能最多。它是粘在機身上的一層軟泡沫，然後把相機安在上面。你可能需要試驗泡沫的種類。如果你用了這種支架，請在[這個帖子](http://www.diydrones.com/forum/topics/photos-with-apm-issues-tweaks)裡面貼一些照片。

## 選擇 APM 通道 ##

APM 的 5-8通道都行 - 任你選擇。在這裡的例子中，我們使用第6通道（譯註：作者用的是1.0版，在1.4版中是第7通道），即從第一個開始數第7個插針。

## 測試 ##

1) 首先檢查舵機行程和相機控制時間是很有幫助的。將控制相機的舵機練到某個通道（比如方向舵），將 APM 設置為手動飛行模式(小心螺旋槳，或者乾脆拆掉）。確定合適的脈寬值（舵臂擺動幅度）和時間值。你可能需要一個助手拿著舵機或者塗上膠水。目標是調整到舵臂擺動到最大幅度時剛好能觸發快門。如果用其他的值，在 APM 啟動時舵機擺動可能會損壞粘接。

2) 可以在中等大小的戶外用一個測試任務測試快門觸發。將航點設在比 WP\_RADIUS (航點半徑）更遠的地方。拆掉電機的 2 根電線或者使用 THROTTLE\_OUT 參數，確保螺旋槳不會轉動。沿著航路走，觀察相機快門。這個測試不需要安裝機翼。下面是相機測試任務的頭部，你需要增加一些實際的航點。需要調整"接近快門的 PWM 值"和觸發快門的時間（2000）來獲得穩定的快門觸發。在一個航點上可能會拍 2 張照片，這算不算一個問題取決於你的想法。
```
float mission[][5] = {
// first circuit
{CMD_SERVO,	  CH_6,	1700,	0, 0},  		// BG 舵臂停留在快門上方
{CMD_SERVO, 	  CH_6,	1700,	0, 0},  		// BG 舵臂停留在快門上方
{CMD_LOITER_TIME, 60,	40,	-31.993901,115.993009},	// 在當前位置盤旋，讓舵臂工作 
{CMD_SERVO, 	  CH_6,	1700,	0, 0},
//
{CMD_WAYPOINT, 	  0, 	5, 	-31.994005,115.993164},	// 1 (back right cnr of my block)
{CMD_REPEAT, 	  CH_6_TOGGLE,	2000,	0, 1},		// 按下快門 
//
// repeat cmd_waypoint with cmd_repeat a few times. Repeating circuit in mission code also helps debugging.
```

能夠穩定觸發快門之後就可以飛行了。

如果你只能讓相機聚焦但是不能拍攝，檢查舵機行程是否足夠。如果行程足夠，可能需要將 undo\_event 從默認的 2 增加到 3，4 或者 5，讓快門壓下的時間長一點。增加"接近快門的 PWM 值"也可以增加快門按下的時間，並減小到達航點和拍照之間的延遲。

## 任務代碼示例 ##

為了保證在拍照點飛機會水平飛行，在拍照點正前方增加一個額外的航點。這樣飛機就有希望水平飛過預期的拍照點（而不是傾斜轉向下一個航點）。付上的照片顯示了傾斜時模糊的情況（譯者：不知道照片在哪裡）。

代碼與測試任務基本一樣:
```
float mission[][5] = {
// first circuit
{CMD_SERVO, 	CH_6,	1700, 	0, 0},  		// BG 停留在快門上方
{CMD_SERVO, 	CH_6,	1700, 	0, 0},  		// BG 停留在快門上方
//
{CMD_WAYPOINT, 	0, 	40, 	-32.017783,115.898563},	// 1
{CMD_REPEAT, 	CH_6_TOGGLE, 	2000, 	0, 1},		// 按下快門
// repeat above two commands
```

## APM 代碼示例 ##

除了使用任務文件設置拍照以外，現在還能直接在 Ardupilot Mega 的代碼中設置。完整的代碼在[這裡](http://diydrones.com/profiles/blogs/camera-triggering/)，如果有重大更改的話將更新。目前它不再主代碼中，但是工作得不錯。WP\_activity 程序允許你在經過一個航點時干某些事情(例如拍照)。相機程序控制一個舵機，轉動一個角度（目前為90度），按下快門。因此當你使用這個程序是，記住調整這個轉動角度。
```
void waypoint_check()
{
    if(wp_index > 1 && wp_index <=18){			// 在航路中途執行
        wp_radius = 10;
	if(wp_distance < wp_radius){			// 設置精度半徑，如果太低的話可能會錯過航點，並且不會拍照
	    APM_RC.OutputCh(CH_6,1500+(90*10.31));	// 按下快門 - 順時針旋轉90度
	    delayMicroseconds(5000);			// 延遲
	    APM_RC.OutputCh(CH_6,1500);			// 舵機返回中點
        }
    }
}
```
可以注意到 servo\_cam 裡的 APM\_RC.OutputCh(CH\_6,1500+(**90** x 10.31)，修改 90 可以控制舵機的角度 (從 -90 到 90)。 APM\_RC.OutputCh(CH\_6,1500) 將使舵機臂處於中點，在這個代碼中釋放快門。

在改完這下之後你必須在 ArdupilotMega 程序的 slow\_loop 函數中增加 waypoint\_check() 調用：
```
void slow_loop ()
	//This is the slow (3 113 Hz) loop pieces
	//----------------------------------------
	switch (slow_loopCounter){
		case 0:
			//這裡省略代碼
			break;
		case 1:
			//這裡省略代碼
			break;
		case 2:
			slow_loopCountet: = 0;
			update_events();
			waypoint_check();	//在這裡添加
			break;
```

## 相機設置 ##

根據你的相機型號，有一系列選項可以使你的照片更加清晰。
  * 快門速度 - 控制快門打開的時間。 時間越長 = 越模糊，所以快門速度盡可能高。
  * 焦距 - 設為手動模式，對焦到無窮遠。這樣當你飛機高度超過 25 米時，都能夠對焦。
  * ISO - 數值越高，對光線越敏感。晴天設為 ISO100 就可以了，陰天設為 ISO600，黃昏設為 ISO1600。當然不同的相機數值也不同，嘗試幾次，找出合適的數值。

## 未解決的問題 _需要幫助_ ##

需要改進的方面包括:
  * 模糊的照片 (由於馬達震動或快速側傾)
  * 相機安裝 (安裝既牢固又不傳遞震動)
  * 航點和按下快門之間延遲太大(延遲越小，位置越精確)
  * 當飛機水平時拍照 (即飛機沒有傾斜轉向下一個航點)

請以這個方式幫助我們：簡短評論寫在下面，長篇大論寫在[這個帖子](http://www.diydrones.com/forum/topics/photos-with-apm-issues-tweaks)裡.

## 舵機安裝細節 ##

<img src='http://api.ning.com:80/files/1uBgrRWLYI4bNNxPMU4dNWbCazbTF2EnsMhP**txDbSYkbT-d4bDQTh*0uB2KTmRNa5DwoOD34z9LrhofZwQTQ__/IMG_1719.JPG' height='300' width='400'>

舵機必須安裝在離快門較近的地方，這樣當它轉動時才能按下快門。上圖顯示了正確的舵機和快門按鈕的對齊方法。當你對齊之後，將它粘上。<br>
<br>
<img src='http://api.ning.com:80/files/EF7KMD3yuSlJfCGBp-fmmnglt1Zx2jVS*8zpo9jWebXDDmm2J2gd8my54qCtpIML7bQsr9ldZPPT0Ue5mrVZaQ__/Sky_camera_nose3.jpg' height='300' width='400'>
<img src='http://api.ning.com:80/files/dypNMQUvb83iuWORczE98BW6Q*VLxv3ebvVfNonmIeHmzQmEmRI5z8GNYsWvN1RYxaZuOrglXDiK3PZPjJb2qQ__/Sky_camera_nose1.jpg' height='300' width='400'>

必須使用泡沫來緩衝舵機臂壓下快門按鈕的壓力。不用泡沫的話，舵機很容易把自己從相機上頂下來。泡沫可以先壓下快門按鈕，然後吸收0.5mm額外運動，這就允許存在一點沒對好或者旋轉過度的情況。在左圖中可以看到 Brett Glossop 的相機安裝，他選擇把泡沫放在快門按鈕上，而不是舵機臂上。在右圖中可以看到側面的安裝情況，包括膠水和泡沫安裝。