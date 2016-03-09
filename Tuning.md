## 根據飛機進行調整 ##

使用默認的PID設置，APM就可以直接飛大多數飛機。但是要想飛得很好，導航準確，風中也有可靠的性能，你還是需要調整一下自家儀。

調整PID的最簡單的方法是使用 Mission Planner 的 PID 設置界面：

http://wiki.ardupilot-mega.googlecode.com/git/images/APpids.JPG

更多的進階參數(大多數人不需要)在 Advanced Params 畫面。你也可以從 Adv Parameters List 畫面載入及儲存設置檔案(到你的 PC)。設置檔案已經版本化 -- 如果參數版本號碼不正確表示 ArduPlane 較舊的參數檔案被省略。

在左側的列表是完整的參數集。在畫面的右側有些(並非全部)更常見的修改參數。你也可以使用這一側的參數做出一樣的變化。只要你按下 "write params" 就會更新板子上的參數，會對目前的飛行造成許多立即性的影響(如果有的話)，並且會寫入 EEPROM 所以他們存在於電源的週期。

請你備註這些參數都是 PID (Proportional, Integral, Differential) 的設定值。

如果你對 PID 調試不是很熟悉，最簡單的 PID 控制是只調整 P 值(I 及 D 為 0 ，當 I 為 0 時 INT\_MAX 無法使用)這樣會對首次設置會有所幫助。

依照 "P" 的數字可以校正當前錯誤比。數字 1 會以 1:1 反應，小於 1 則會有較柔和的反應，大於 1 則會過驅動反應，0 則不會有任何反應。

在[這裡](ConfigFiles.md)我們已經提供了一些常用的飛機的配置文件。但是如果你用的飛機沒有在列表中，下面是推薦的調整過程的簡要說明:

下面是我們推薦的調整步驟:
  1. 用手動模式飛行，確保所有部件連接無誤。
  1. 在地面上檢查增穩模式。如果你左右傾斜飛機，你可以看到副翼（或3通機的方向舵）相應轉動，以使機器恢復水平。如果你前後傾斜飛機，你可以看到升降舵相應轉動進行修正。如果你用的是4通飛機，那麼方向舵將與副翼同方向反應。如果不正確的話，改變 REVERSE\_ROLL,  REVERSE\_PITCH 和 REVERSE\_RUDDER 進行相應調整。

Unknown end tag for &lt;/p&gt;


  1. 以增穩模式飛行，檢查在飛機傾斜時，飛控是否真的將飛機恢復到水平飛行狀態。如果飛機前後或左右搖擺，減少 P 增益 (見下文)。

Unknown end tag for &lt;/p&gt;


  1. 以線控模式 (A 或 B)飛行, 檢查俯仰和側傾。飛機應當保持設置的高度。發射器搖桿位置直接設置傾斜角度。以水平直線飛行開始，然後將搖桿移到一端，飛機應該側傾45度，完成這次轉彎。 如果不穩定，減小 5-1 ("#define SERVO\_ROLL\_P .006"); 如果太慢，則增加該值。在俯仰方向（上和下）重複以上操作。如果還不太正常，查看設置中的 HEAD\_MAX, PITCH\_MAX 和 PITCH\_MIN。如果你將操縱桿移到最右邊，飛機應該側傾（並保持） HEAD\_MAX 角度。飛機是否如此？如果確實如此，慢慢增加側傾舵機 P 增益。如果它左右搖晃則減小該增益。類似的調整俯仰。調整的目的是讓飛機乾脆地響應俯仰和側傾的輸入。一直如此調整，不要擔心其他增益，直至你輕彈搖桿並保持，飛機像手動飛行模式一樣快速響應。通常只需要調整 P 增益，但有些飛機需要 I 增益來保持傾斜角度。
  1. If things still aren't quite right in FBW, look at your settings for LIM\_ROLL\_CD, LIM\_PITCH\_MAX and LIM\_PITCH\_MIN (the units of all of them are in hundredths of a degree). If you move the stick to the extreme right the plane should go into a bank of angle LIM\_ROLL\_CD (and stay there). Does it do this? If it gets there slowly increase the roll servo P gain. If it oscillates in roll decrease the servo gain. Work on pitch in a similar manner. The goal is for the plane to respond in pitch and roll in a crisp manner to your stick inputs. Work on this without worrying about the other gains until when you flick the stick and hold it to the side the plane will respond crisply and as quickly as in manual flight. You will likely only need the P gain, but some airframes will need I gain to hold the desired bank angle well without steady state error.
  1. 現在, 仍然在線操縱模式，放開操縱桿，觀察飛機是否保持高度。 如果飛機下降，增加 6-5 ("#define PITCH\_COMP .10")。 你應該能夠以 HEAD\_MAX 角度傾斜轉彎，而不增加也不降低高度。

Unknown end tag for &lt;/p&gt;


  1. 現在嘗試返航模式。飛機應該飛回到你這裡。如果它飛走了，將 7-1 ("#define NAV\_ROLL\_P .6") 增加 25%。如果它還不回來，增加 7-2 ("#define NAV\_ROLL\_I .0")。 反之，如果飛機回來了，但一直搖擺，減少 7-1。如果還不夠，增加 4-4 ("#define XTRACK\_GAIN 00").

Unknown end tag for &lt;/p&gt;


  1. 最後，值得注意的是如果你大幅度改變巡航速度，你可能需要重新調整增益。因此如果你在1/3油門測試，但是希望全油門飛行，你可能發現問題又出現了。最好是在你通常飛行的油門設定下進行測試。

Unknown end tag for &lt;/p&gt;



## 調整導航的特別建議 ##

假設你的飛機穩定良好，但似乎在航點之間或返航時「蛇」行，或者更差勁的順風飛行，根本不能到達航點。怎麼辦呢？

上面的指導應該可以幫助你，但這裡有一些特別提示:

  1. 測試的最好方法是用四航點框。這個框應該足夠大，以便飛機能夠顯示它的模式，但是也別太大，以便在出問題的時候還能手動控制飛回來。
  1. 開始時將 NAV\_ROLL I 、D 項和偏航矩增益(Crosstrack Gain)都設為 0，以便一次調整一項。
  1. 第一個要檢查的是 SERVO\_ROLL\_P。你完成了 45 度線控 (FBW) 測試嗎? 你飛機導航不好可能的原因是舵機權力（authority）不夠，需要調高一些。 唯一能夠確定的方法就是 FBW 測試.
  1. 如果你已經調好了 SERVO\_ROLL\_P, 在四航點航線上檢查 NAV\_ROLL\_P。如果飛機缺少導航權力, 增加一點; 如果飛機蛇形，減少一點。
  1. 上述應該可以讓你的飛機不錯地跟蹤航點。跟蹤航線最後要做的事就是調整偏航矩增益（Crosstrack gain）。它的作用是把飛機拉回到航點之間的連線上，而不是直接朝下一個航點飛行。下面的圖展示了偏航矩修正的作用:

![http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/crosstrack2.png](http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/crosstrack2.png)

當增益為 0 時，飛機按紅線飛行。當增益調高 (默認值 100)，飛機回接近藍線飛行。如果飛機跟蹤航線時擺動，把 XTRACK\_GAIN 從默認值 100 減小一點。飛機越快，這個值應該越小。要完全忽略航線，僅僅朝下一個航點直線飛行，把該值減小到 0，這時剩下的蛇行僅由 Nav\_Roll 和 Roll 影響。

一個偏航矩調整的交互指南在[這裡](CrossTrack.md).

## 關於 PID 循環的更多知識 ##

PID 可以看作是根據「過去，現在，未來」的數據來控制。

比例增益（P）是最簡單的控制方式，它是「目前」的偏差。自動駕駛儀要 10 度的仰角，但現在只有 5 度，那麼誤差就是 5：改變一些升降舵。 （改變量由誤差量決定，並根據 P 進行縮放）。過去的數據（「I」）考慮到最近發生的誤差。如果比例增益不能驅動控制面消除誤差，那麼「I」的增益會嘗試這樣做。
未來（「D」）根據目前誤差（不是用水晶球）推斷未來一段時期誤差。我們選擇控制輸入，試圖阻止預測（未來）的變化。

運用於飛機控制面，或油門的最終控制是這三個計算的和。

調整P，PI 或 PID 值，可以改善消除預期姿態（仰角，速度，朝向，等等）和實際姿態之間的觀測誤差的速度，並消除過分的振蕩。

幸運的是，默認PID值對直飛、轉彎，操作油門和導航還幹得不錯，因此，如果在除手動外的第一種模式（穩定），你看到瘋狂的反應，它可能不是微調P（或I或D）值就能解決得了的。

查看的PID的最好的辦法是在模擬器上設置。在穩定模式下直線水平飛行，然後將飛機機頭抬起再釋放搖桿。升降舵的 PID 設置裡的 P 項將決定升降舵反應的質量和強度。它可能是強烈但過沖；或過慢，也許是「永遠達不到」。 「I」值可以加快仰角恢復水平的速度。最後，在「D」項將對控制所固有的延遲做出反應，並進一步提高了反應。但是，如果「D」太大，仰角上會出現振蕩，並越來越大。這就是為什麼不建議在空中挑選隨機數調整「D」值。

## 一點理論知識 ##
_(Doug Weibel提供)_

APM 基於級聯的 PID 控制器。導航控制循環根據飛機當前方向和目標點計算預期的傾斜角度。導航增益會影響這個角度的計算。例如，如果我們偏離航線 10 度，則某個側傾導航 P 增益將產生一個 5 度的側傾角，而如果將該增益翻倍，那麼將產生 10 度側傾角。第二個控制循環控制舵機減小預期的側傾角和實際的側傾角之間的誤差。我之所以推薦在線控飛行模式下調整這些增益，是因為在該模式下，你可以通過操縱桿的位置直接輸入預期的傾角，而與不受底層的導航控制循環影響。

由於串聯控制循環的性質，增益和最終結果之間存在一個數學關係。但是使用這個串聯控制的目的是讓它更加直觀和易於理解。先調整正確的舵機增益，使系統能夠得到期望的側傾角和俯仰角，然後再調整導航增益，使系統的導航性能最優化。以這個順序調整更簡單也更有效。