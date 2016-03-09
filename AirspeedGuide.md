## 空速傳感器指南 ##

硬件安裝說明在[這裡](Airspeed.md).
//  *解釋*    
//     空速傳感器幫助 APM 更精確地計算空速，因此能夠更好地處理風和空速計算
//
//  *說明*
//     因為空速傳感器是一個附件，你需要告知 APM 安上了一個空速傳感器
//     如果你正確安裝了一個空速傳感器，則將"#define AIRSPEED_SENSOR     DISABLED"
//     改為 "#define AIRSPEED_SENSOR     ENABLED"

//  *可用選項*
//     #define AIRSPEED_SENSOR     DISABLED
//     #define AIRSPEED_SENSOR     ENABLED
//  *****************
//  *SELECTED OPPTION*
       #define AIRSPEED_SENSOR     ENABLED
//  *****************         
      ```