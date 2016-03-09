#summary 原始GPS數據

本測試顯示 GPS 模塊的原始輸出數據。

如果你在常規 GPS 測試中遇到問題，本測試可能對調試有所幫助。

**對多數用戶\*不推薦**, 僅用於底層 GPS 調試。

如果你希望以 ASCII 方式顯示數據, 在 Test 標籤頁中修改這行:

```
          Serial.print(incoming,BYTE); // will output Byte values  
```
to this...
```
          Serial.print(incoming,ASCII); // will output ASCII values  
```