#總結如何啟用倒飛

# 介紹 #

APM現在支持倒飛。如果您的版本支持倒飛可以使用 INVERTEDFLT\_CH EEPROM 設定參數。


# 祥細介紹 #

INVERTEDFLT\_CH 允許你設置發射器上的開關來開啟 APM 的倒飛功能。

參數預設值為 0，意思是說未開啟倒飛功能。要開啟它時，請先選擇一個 RC 未被使用的輸入頻道，發射器上雙位置開關的 PWM 值需大於1750，未開啟時這個值會在1750以下。

例如，如果頻道7目前未使用，設置 INVERTEDFLT\_CH 至第7頻道，如果發射器由第7頻道發送 1900 ，APM 將會翻轉飛機並且倒掛，任何模式可以繼續操作，它在飛行但飛機是倒著飛。

## 發射器設置 ##

啟用倒飛模式，APM 只可飛行在穩定的平面。開啟倒飛模式飛機會由一般平飛狀態翻轉180度。

為了得到最有效的倒飛，當倒飛開關啟用時同時也可以反轉發射機的升降舵和方向舵控制，只要是還不錯的發射器應該都有此功能。例如，在Turnigy 9X 發射器使用 ER9X 韌體你可以使用一下的設定：

```
CH01   +100% AIL
CH02   +100% ELE
     * -100% FULL Switch(GEA)
CH03   +100% THR
CH04   +100% RUD
     * -100% FULL Switch(GEA)
CH07   +100% MAX  Switch(GEA)
```

設置升降舵和方向舵的反轉 GEAR 開關被開啟時，順著 CH7 的設置。

## 飛行模式的交互作用 ##

倒飛可用於任何穩定的飛行模式(但不能是手動模式)。這意味著你可以在飛行任務中切換倒飛模式，並且飛機可以繼續執行任務。確保在降落前將倒飛模式關閉。

## 訣竅 ##

這邊有些倒立飛行的訣竅

  * 可以先在模擬器中試試看，並且確認發射器的設置是正確的。
  * 請在倒飛前確保你的高度是否足夠，當你在倒飛時，依據不同的機身在倒轉時會損失不少的高度，所以請儘量保持一定的高度。