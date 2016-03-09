
### ArduPilotMega 高級配置指南 ###

APM 代碼中的 APM\_config.h 文件是在編譯和上傳代碼之前告訴自駕儀關於你的硬件配置的地方。你不需要修改任何其他的文件。閱讀本頁，遵循你的所應用的設置的說明。

因為我們在編輯計算機程序，我們需要使用計算機語言，這是通過 APM\_Config.h 文件中的"聲明"實現的。

### 聲明 ###

在 APM 代碼中, "#define" 通常定義了一個硬件配置項。它之後跟著一個計算機可以理解的短語或句子，例如 "#define GPS\_PROTOCOL GPS\_PROTOCOL\_UBLOX"

如果你想根據硬體配置代碼，你需要在 **SELECTED OPTION** 區域增加或修改 "#define" 聲明。你可以從本教程中拷貝並粘貼到代碼中，或者它已經在代碼中，並且用雙斜線("//")"註釋"的話，刪除斜線。

例子:

註釋  (APM 將忽略該聲明):

`// #define`

取消註釋 (APM 將包含該聲明):

`#define`

### 常用配置 ###

點擊需要的一項，拷貝到 APM\_Config.h 文件中

[組合 1:](Combo1.md)
  1. APM
  1. GPS

[組合 2:](Combo2.md)

  1. APM
  1. GPS
  1. 空速計

[組合 3:](Combo3.md)

  1. APM
  1. GPS
  1. 空速計
  1. Xbee

[組合 4:](Combo4.md)

  1. APM
  1. GPS
  1. 空速計
  1. Xbee
  1. 電壓監視器

[組合 5:](Combo5.md)

  1. APM
  1. GPS
  1. 空速計
  1. Xbee
  1. 電壓監視器
  1. 磁場儀