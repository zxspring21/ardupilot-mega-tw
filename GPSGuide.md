== GPS 選擇指南 ==

硬件安裝說明在[這裡](Assembly.md).

```
//  *解釋*           
//     Diydrones是一個開源站點，不同人使用不同的設備。
//     因為可以使用不同的 GPS 模塊，所以需要告知 APM 你使用哪一種。
//                          
//  *說明*
//     查看下面的 GPS 模塊列表, 查找你的模塊，按一下方式定義
//     例子" #define GPS_PROTOCOL GPS_PROTOCOL_UBLOX " 請注意只修改
//     "GPS_PROTOCOL_UBLOX "部分，並且你的設置應該完全相同
//                           
//  *可用選項*
//     GPS_PROTOCOL_NONE        沒有安裝GPS
//     GPS_PROTOCOL_IMU         X-Plane 接口 或 ArduPilot IMU.
//     GPS_PROTOCOL_MTK         MediaTek GPS.
//     GPS_PROTOCOL_MTK16       MediaTek GPS 1.6版固件
//     GPS_PROTOCOL_UBLOX       UBLOX GPS
//     GPS_PROTOCOL_SIRF        SiRF-based GPS，二進制模式. 未測試
//  ******************
//  *SELECTED OPPTION*
     #define GPS_PROTOCOL GPS_PROTOCOL_UBLOX
//  ******************
```