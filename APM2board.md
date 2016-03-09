== APM 2 板 ==

APM 2 板出廠時已經焊接好，你只需要使用Mission Planner將你所需要的韌體燒錄致板子即可。**還不要把它插入電腦的USB端口。我們會在下一步再做這件事。**這邊僅是一個電路板的介紹。

下列為飛控板硬體簡介：

![http://wiki.ardupilot-mega.googlecode.com/git/images/APM2/APM2_main_components.jpg](http://wiki.ardupilot-mega.googlecode.com/git/images/APM2/APM2_main_components.jpg)

請將你的RC接收器接在板子的Input端並將你的伺服機或電子變速器(ESC)接在Output端。板子共有8個輸入及輸出，僅管可能不需要使用到所有的輸入及輸出但如果你需要的話還是可以依下列的指示安裝。

對於大多數人來說出廠時焊上的連接器對已經足夠，但如果你需要安裝更多的感應器，板子有提供9個埠(A0~A8)供你使用。

這邊的連接器選項提供給額外的感應器及控制器(並非的程式庫皆有支援)：

![http://wiki.ardupilot-mega.googlecode.com/git/images/APM2/APM2_analog_pinout.jpg](http://wiki.ardupilot-mega.googlecode.com/git/images/APM2/APM2_analog_pinout.jpg)<p>

APM2 原理圖及電路板的檔案在<a href='http://stuff.storediydrones.com/APM_v2_Eagle.zip'>這裡</a> (Eagle format)。<br>
<br>
<hr />

<h3>主板供電的替代方法</h3>

<b>電源要求摘要</b>

<i><b>單一電源供電</b></i>

<table><thead><th> Power Options </th><th> Nominal  </th><th> Abs MAX </th><th> JP1 status </th></thead><tbody>
<tr><td> Power on Output PWM connector </td><td> 5.37V +-0.5 </td><td> 6V      </td><td> JP1 connected </td></tr>
<tr><td> Power on Input PWM connector </td><td> 5.00V +-0.5 </td><td> 6V      </td><td> JP1 connected </td></tr></tbody></table>

<i><b>雙電源供電</b></i>

<table><thead><th> Power Options </th><th> Nominal  </th><th> Abs MAX </th><th> JP1 status </th></thead><tbody>
<tr><td> Power on Output PWM connector </td><td> 5.00V +-0.5 </td><td> 6V      </td><td> JP1 open   </td></tr>
<tr><td> Power on Input PWM connector </td><td> 5.00V +-0.5 </td><td> 6V      </td><td> JP1 open   </td></tr>
註: 如果 JP1 開啟，電源必需來自於 Input PWM 及 Output PWM</tbody></table>

板子在出廠時就已經設定電源就是來自你的輸出端。當你在工作台上進行設定及測試時，你可能會通過USB電纜供電板，但是你的飛機上，你的給電方式會需要使用內建的電源系統，通常是透過 ESC 使用鋰電池。在四軸飛行器就要透過你的配電板(PDB)，但是ESC的電壓可會超過5V。<br>
<br>
它也可以有兩個獨立的來源，一個電源輸入端的 RC 系統，另一個電源是輸出端(伺服機或ESC)。透過一個跳線 JP1 做控制(如下所示)。如果跳線是開啟的(出廠預設)，電源來自輸出端。如果跳線的關閉的，板子的電力來源是從輸入端，但是輸出端需要有自己的電力來源。這些設置是如果你想在飛機有兩個獨立的電源，提供給舵機及其他電子設備。APM2 設計的作業電壓為 5.0 +/- 0.5 VDC。<b>警告：不要使用超過 6.0V DC 的輸入電壓，否則會燒壞你的板子。</b>理想的輸入電壓是 5.37v +/-0.0v 但如果是一般的 ESC 可能會無法提供。<br>
<br>
要讓 APM2 正確的作業需要一個乾淨電源，也就是說會需要一個電源過濾器。要知道電壓規格的差異取決於連接器的使用。原因是因為有二極體會防止 USB 的電源倒灌，當連接 USB 時會有電源送至 APM2 的 PWM 輸出埠的連接器，就會可能破壞某些零件。因此當 USB 未通電時，電源會來自於 PWM 的輸出埠當通過二極體時會產生一些壓降，所以需要補償一個高一點的輸入電壓。因此，電力需求如下：需要 5.0VDC +/- 0.5V 輸出至 PWM 輸入埠時，請移除 JP-1 跳線。需要 5.37VDC +/- 0.5V 輸出至 PWM 輸入埠時，請接上 JP-1 跳線。<br>
<br>
<b>警告：不要使用超過 6.0V DC 的輸入電壓，否則會燒壞你的板子。</b>

在某些情況下，為了避免在大電流時會產生壓降將輸入電壓設為略高於中間值(但要小於最高值)，可能是一個好主意。<br>
<br>
APM2 本身會消耗很小的電流(約 200mA)，而一個電源大約可以提供約 300 - 500 mA。不管如何，伺服機或其他耗電設備都可以藉由相同的電源被驅動，你必須顧慮這些裝置的電力需求，並且提供足夠的電力來源以防止重大的錯誤(brown-outs)發生。例如，一個數位伺服機很輕易的就會消耗 1-5 安培，取決於它的尺寸和性能。(註: ESCs 不會消耗 APM 電源)如果遇到假重置或其他奇怪的行為，它是最有可能因為雜訊或電力不足的 APM。與所有的電路板一樣，電子雜訊可能會來自於馬達、伺服機或者其他大電流裝置，都會導致不可預知的行為。建議使用這一類的<a href='http://www.dpcav.com/xcart/Power-Supply-Filter-L-C-Type.html'>電源過濾器</a>或者<a href='http://www.readymaderc.com/store/index.php?main_page=product_info&cPath=11_15&products_id=533'>這種</a>都被用於處理這些狀況。<br>
<br>
太短或太長的電源線，壞掉或老舊的連接器，或 APM 電源電流能力不足，都會在不可預知的狀況下發生故障(brown-out)。這一點尤其是在傳統的直升機的所有舵機一起啟動時可能會在短時間上升到 3-20 Amp。電源必須能夠承受而不會讓電壓下降或電壓突波。<a href='http://www.castlecreations.com/products/ccbec.html'>這個</a>是其中一種優質的開關型 BEC，這個是<a href='http://www.readyheli.com/WRL-HBECM2-Western-Robotics-Hercules-Super-Mini-BEC-G2-_p_36453.html'>另一種</a>，可以根據電流的需求提供不同的解決方案。這些穩壓器的類型很多都是可編程燒錄的，所以使用前請依 APM2 的安全工作範圍將它設定好。線性穩壓器，不建議，因為它們是效率低，容易出現過熱及因為熱而引發的故障。APM2絕對不要直接連接到任何類型的電池。<br>
<br>
電源問題很常見也很令人擔憂，要仔細的檢查。沒有乾淨的電的來源，會讓所有自動駕駛儀或飛行控制器失控，並潛在危險的因子。<br>
<br>
<img src='http://wiki.ardupilot-mega.googlecode.com/git/images/APM2_JP1.jpg' />

<h1>APM1 及 AMP2 的主要差異</h1>

兩者主要的差異在於APM2有個高階的感應IC MPU-6000，它不僅是個感應處理器更有高精度的壓力感測。<br>
<br>
感謝有這個晶片的科技讓我們合併了許多不同功能的IC，包含了USB的介面、PPM 編碼及數位開關，節省了APM1的數位-類比的轉換IC，更少的IC意謂著更小的板子、更便宜的價格及更少的錯誤。<br>
<br>
如果你以前也有APM1你會發現APM2更小更可靠：<br>
<br>
<ul><li>之前外部的感應器如GPS、磁力儀已不需要焊接或電纜<br>
</li><li>沒有CLI(Command Line Interpreter)開關，如有需要使用可直接在軟體中使用(按3次"ENTER")而不是硬體<br>
</li><li>沒有繼電器，因為僅有少數的人使用所以如果你有需要(例如：觸發攝影機、相機)，我們支援一個外部的。<br>
</li><li>沒有DIP開關，所有的DIP功能(通道反轉，設置 elevon模式)現在皆在Mission Planner做設定。<br>
</li><li>沒有內建電源調節器。你必須透過 USB 來啟動板子或者使用飛行器上的 ESC (使用 ArduCopter 的配電板)，接至 APM2 輸出端的電源引腳。<br>
</li><li>沒有內建電壓監視器。監控電流通常比電壓的人多，所以我們建議使用<a href='http://www.sparkfun.com/products/9028'>Sparkfun 電流感應器</a>，只要將它插入任何一個感應器埠即可。</li></ul>

<img src='http://wiki.ardupilot-mega.googlecode.com/git/images/APM2/Atto_APM2_1.jpg' />

<h3>電源保護套件使用說明(將 APM 2.0 板裝上二極管及保險絲元件)</h3>

<a href='http://arducopter.googlecode.com/files/APM2.0PowerFixHow-To.pdf'>http://arducopter.googlecode.com/files/APM2.0PowerFixHow-To.pdf</a>

<h3>電源保護套件原理圖</h3>

<a href='http://arducopter.googlecode.com/files/APM2-mod-schematic.pdf'>http://arducopter.googlecode.com/files/APM2-mod-schematic.pdf</a>