## 自動追縱攝影機 ##

![http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/Aerial_Photo_eg2.jpg](http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/Aerial_Photo_eg2.jpg)

你有沒有想過把你的 APM 設置得像上面這樣？在下面的文章，你會發現做其他的作法，並且是簡單又容易的作法。視訊上的圖片仍然是由飛機上的 ArduPilot Mega 平台自動產生。這將一體適用於其他系統和設置(直升機及範例訊)當然反之亦然-有很多 RC 空中攝影論壇和各種網站，你也可在上面發表你對於 APM 的設置意見。

目前，軟體提供了這些功能:

  * **相機追蹤拍攝**: 使用 RC 訊號手動觸發相機快門(**註:**目前在 ArduCopter 還無法運作，但在 ArduPlane 可部分運行，請見這裡的說明: [thread](http://www.diydrones.com/forum/topics/automated-parachute-drop) 及 [issue 492](http://code.google.com/p/arducopter/issues/detail?id=492))
  * **穩定**: 當載體旋轉時，保持相機在水平位置
  * **位置追蹤拍攝****: 保持相機聚焦在某一個 3D 拍攝點(在地面上或者在空中)**


### 相機的選擇 ###

剛開始時任何小及便宜的數位相機都是不錯的選擇(也許將來進階也可以繼續使用)。請避免使用光學防震的相機，社群似乎認為它無法處理的螺旋槳振動或視訊搖晃(被稱為"果凍"效果)的問題。重量也很重要。大多數的飛機大約可以負荷 120 克左右的重量。使用 200 到 300 克的相機會使得飛行及搜尋 COG 變得困難。在你飛行前也許要再買一個不要太重的木質底座。

### 相機的角度 ###

剛開始可以使用垂直向下的角度。飛行模擬的視角通常辨認度較垂直好。裝載由垂直角算來約 40 度可獲得主要的地面圖片但這個角度是一個斜視圖。超過直角約 70 度將會給你比較多天空的視圖(由[Draganfly](http://www.draganfly.com/news/2008/08/23/rc-aerial-photography-get-great-pictures-tutorial/)提供)。

### 快門觸發的選擇 ###

快門觸發有相當多的選擇。有些選擇需要某些品牌的鏡頭，價位較高適合攝影的愛好者。如果你想要搜尋一些選項請見[Blip](http://blip.com.au/CategoryPhotography.aspx) 或 [rc-airplane-world](http://www.rc-airplane-world.com/rc-aerial-photography.html)。要找 4 英鎊打死的相機可以到[這裡](http://diydrones.com/photo/albums/ebay-keychain-camera/)

### 伺服機的建置 ###

簡介：
請選用9克伺服機。
請預先確認伺服機轉臂的全轉矩。當全轉矩時快門必須還能操作。
使用熱溶膠在保麗龍(EPO)的機體畫上一個小圈黏上伺服機的轉臂(大約 2 mm 要比轉臂大一點)，這樣可以負擔一些推力而不會傷到視訊裝置。
再使用熱溶膠在9克伺服機的一邊黏上視訊裝置，這樣在全轉矩快門才能正常操作。
註：如果將伺服機設置的太遠，表示熱溶膠的黏接點會容易掉落，您將會無法拍照，除非你重新連接它。

<img src='http://api.ning.com:80/files/1uBgrRWLYI4bNNxPMU4dNWbCazbTF2EnsMhP**txDbSYkbT-d4bDQTh*0uB2KTmRNa5DwoOD34z9LrhofZwQTQ__/IMG_1719.JPG' height='300' width='400'>

伺服機要安置的地方要離快門近一點這樣當視訊裝置旋轉時還是可以按到它。上圖的伺服機就有與快門按鈕正確對齊。只要對齊好了就可以將它黏上去。<br>
<br>
<img src='http://api.ning.com:80/files/EF7KMD3yuSlJfCGBp-fmmnglt1Zx2jVS*8zpo9jWebXDDmm2J2gd8my54qCtpIML7bQsr9ldZPPT0Ue5mrVZaQ__/Sky_camera_nose3.jpg' height='300' width='400'>
<img src='http://api.ning.com:80/files/dypNMQUvb83iuWORczE98BW6Q*VLxv3ebvVfNonmIeHmzQmEmRI5z8GNYsWvN1RYxaZuOrglXDiK3PZPjJb2qQ__/Sky_camera_nose1.jpg' height='300' width='400'>

當按下快門按鈕時，伺服機轉臂必須輕微移動。伺服機可以很簡單卸除相機而不需要發泡塑料。第一次發泡塑料鬆開快門按鈕會發生了什麼事，它吸收了 0.5mm 的多餘動作讓允許你發生一些誤差或過度的旋轉。<br>
圖1 你可以看到 Brett Glossop 的相機設置，選擇放置發泡材料的是快門按鈕而不是轉臂。圖2 你可以看到 Brett 的安裝包含了膠水和發泡材料座。<br>
<br>
<h3>相機的底座建置</h3>

相機需要安裝牢固，但它卻也要抑制馬達的振動。要同時實現這兩個目標是很困難的。飛行論譠已經有試過許多相機底座的安裝方式包括：軟硬泡棉、合成橡膠管(將相機安裝在管邊)、手術管、橡膠帶、尼龍螺栓和魔術貼。直升機最常使用橡膠管。我們這裡沒有具體的建議，因為最好或最簡單仍有待決定，並且也取決於機身。即便如此，魔術貼加橡皮筋(額外的安全)可以迅速的設置，這樣也可以給你一個還不錯的相片。<br>
<br>
泡棉保護/安裝是沒有經過考驗，但是卻最具通用性。可以在 Tim 的<a href='http://www.rcgroups.com/forums/showpost.php?p=16196982&postcount=26'>T-copter 網頁</a>找到應用。這是在機體及相機底座間反覆黏上一層軟泡棉。您也許可以嘗試用這個類型的泡棉。如果你有使用，請在這個<a href='http://www.diydrones.com/forum/topics/photos-with-apm-issues-tweaks'>討論串</a>放上一些你所建置的圖片。<br>
<br>
<h3>相機設置</h3>

依據下面幾點你將會有數組相機的選項，使您的照片更清晰。<br>
<ul><li>曝光 - 控制快門開啟的時間。多一點的時間 = 多一點的模糊，所以曝光時間愈短愈好。<br>
</li><li>焦距 - 設定為手動及無限遠。這個方式可以讓你保持在永遠對焦的狀態，只要你的飛機的高度超過 25 米。<br>
</li><li>ISO - 數字越大，光敏感度越高。在晴天 ISO100 應該都還不錯，陰天可以調到 ISO600，黃昏可以用 ISO1600。當然所有的相機都不盡相同，所以可以多多嘗試，得到正確的數值。</li></ul>

<h3>連結攝影伺服機</h3>

將攝影機的 roll、pitch、yaw 伺服機連接至 APM 的伺服機輸出端(我們待會將會在軟體中的設置程序中，設置通道與伺服機的對應)。<br>
<br>
<ul><li>For APM 1: ch5, ch6, ch7 and/or ch8<br>
</li><li>For APM 2: ch5, ch6, ch7, ch8, ch9, ch10 and/or ch11</li></ul>

<b>警告</b>: 如果相機的伺服機是接在裝有 APM 電源模組 APM2.5 上的 ch9、ch10、ch11，或者移除 JP1 的雙電源上，伺服機就是使用 PWM 輸出端的電源。APM 電源模組的目的不是提供電源給伺服機，否則你可能會遇到的 APM 掉電，導致飛機墜毀。<br>
<br>
你可以依你喜歡的任何順序連接。如果你沒有或不想使用就不用連接。<br>
您還可以連接一台伺服 開啟/關閉 相機或 部署/收回 相機及用伺服機觸發相機。<br>
<br>
然後開啟你的 APM 並將它連接至 Mission Planner 。<br>
在設置視窗中，分配 RC5_FUNCTION、RC6_FUNCTION、RC7_FUNCTION 及 RC8_FUNCTION 每個標籤的功能。<br>
<br>
<br>
<img src='http://wiki.ardupilot-mega.googlecode.com/git/images/Standard_Params_RC5_manual.png' />


然後使用你的 RC 發射器來移動一下伺服機並且校驗相機的雲台。<br>
<br>
<br>
<h3>校驗</h3>

將 RC 發射器的操控桿移到極端的位置，相機會相對應移動。測量相機的最大和最小偏轉角（極端）。<br>
把量測的數值乘以100並將它們各自移到RC5_ANGLE_MIN, RC5_ANGLE_MAX、RC6_ANGLE_MIN、RC6_ANGLE_MAX、RC7_ANGLE_MIN、RC7_ANGLE_MAX、RC8_ANGLE_MIN、RC8_ANGLE_MAX。<br>
<br>
例如，如果您的安裝的 pitch 伺服連接到通道6，要將相機從 -50 移動到 -5 度，您的 roll 伺服連接通道7，從 -35 旋轉到 35 度那麼你應該做的：<br>
<table><thead><th> RC6_ANGLE_MIN </th><th> -5000  </th></thead><tbody>
<tr><td> RC6_ANGLE_MAX </td><td> -500   </td></tr>
<tr><td> RC7_ANGLE_MIN </td><td> -3500  </td></tr>
<tr><td> RC7_ANGLE_MAX </td><td>  3500  </td></tr></tbody></table>


新的代碼假設偏航零與的機身偏航零相匹配*非*45度角在此頁面頂部左側的圖片。<br>
<br>
新的代碼假設傾斜零與的機身傾斜零相匹配*非*45度角在此頁面頂部右側的圖片。<br>
<br>
<br>
<h3>設置</h3>


在設置畫面，分配RC5_FUNCTION、RC6_FUNCTION、RC7_FUNCTION 及 RC8_FUNCTION 的功能。<br>
<br>
<img src='http://wiki.ardupilot-mega.googlecode.com/git/images/Standard_Params_RC6_pitch.png' />


所以如果你的雲台的 pitch 是 channel 6，roll 是 channel 7，相機快門是 channel 8，你應該可以照這樣設定：<br>
<table><thead><th> RC6_FUNCTION </th><th> <i>mount_pitch</i>    </th></thead><tbody>
<tr><td> RC7_FUNCTION </td><td> <i>mount_roll</i>     </td></tr>
<tr><td> RC8_FUNCTION </td><td> <i>camera_trigger</i> </td></tr></tbody></table>

如果舵機的回應是你想要的，只要修正並且使用使用相對應的 RC5_INVERT、RC6_INVERT、RC7_INVERT 及 RC8_INVERT 標籤。<br>
<br>
<img src='http://wiki.ardupilot-mega.googlecode.com/git/images/Paramameter_List_RC7_rev.png' />


<h3>飛行</h3>

使用上述例子的配置，在飛行期間你可以使用 RC 發射器的 Ch6 及 Ch7 手動控制相機。程式碼就會自動的穩住相機。<br>
<br>
使用 Mission Planner 的地圖 (需要版本 1.0.83 或者最新版的)來傳達攝影位置。<br>
只要對著地圖上的航點點擊滑鼠右鍵並從選單中選擇「Point camera here」即可。如果你這麼做將會無法使用發射機控制拍攝位置，它只受 mission planner 的控制。如果要相機重新跟隨 RC 發射器的動作你就需要重置 APM(所有 airplane/quadcopter/helicopter 的電源週期)。<br>
<br>
<img src='http://wiki.ardupilot-mega.googlecode.com/git/images/Standard_Params_Mnt_mode.png' />

你可以使用 MNT_STAB_PITCH、MNT_STAB_ROLL、MNT_STAB_YAW 這3個參數來開啟及關閉每個軸的穩定性。<br>
<hr />

<h2>ArduPlane 及 ArduCopter 軟體/設置說明</h2>

<img src='http://api.ning.com:80/files/Dkny0E7F9OlMPEAEa8Ar4lpbCBr8TB2FMyfCLSXlkCN11H8BN1I4DlUcM1QCg*lFdI7UPMvMjtpOUMY5TK-5Ng__/CameraConfig.jpg' />

取得並且運作:<br>
<br>
<ul><li>由我們的 git 程式庫取得 APM_Camera<br>
</li><li>只要在 ArduBoat, ArduCopter, ArduPlane or ArduRover 的子資料夾簡單發出「上傳」的指令行就可編譯和下載。<br>
</li><li>使用 Mission Planner 如何設定及連結攝影伺服機。<br>
</li><li>使用 Mission Planner 在飛行中控制攝影點(需要透過無線模組使用 MavLink connection)。</li></ul>

您需要編譯的代碼的唯一原因是因為我們不提供預編譯的二進制文件。但是你將*不*需要改變任何一行代碼。<br>
<br>
新的代碼會假設偏航零與機身偏航零互相配合，此頁面頂端左側的圖*不是<b>45º角</b>

新的代碼會假設傾斜零與機身傾斜零互相配合，此頁面頂端右側的圖*不是<b>45º角</b>


<h3>取得代碼</h3>

<ul><li>For ArduPlane: 只要使用 mission planner 中最新版本的 ArduPlane 2.40 或者更新的版本。<br>
</li><li>For ArduCopter: 只要使用 mission planner 中最新版本的 ArduCopter 2.70 或者更新的版本。<br>
</li><li>For ArduRover and ArduBoat:<br>
<pre><code>git clone https://code.google.com/p/ardupilot-mega/<br>
</code></pre></li></ul>

<h3>編譯程式</h3>

<ul><li>For ArduPlane: 你可以直接跳到"連接伺服機"，這裡不需要編譯。<br>
</li><li>For ArduCopter: 你要確認你有安裝編譯程式所需要的軟體。只要依循 <a href='http://code.google.com/p/ardupilot-mega/wiki/BuildingWithMake'>這個指示</a>。然後只要在命令列原行:</li></ul>

<pre><code>cd ArduCopter<br>
make upload<br>
</code></pre>

你可以用 ArduBoat 取代 ArduCopter 或 ArduRover。<br>
如果有上傳失敗的問題請確認設定為再重新上傳一次。