**電池監視配置**

硬件安裝指南在[這裡](Voltage.md)


## 配置 ##

## 1.1 BATTERY\_EVENT 開/關 ##
```
//            *解釋* 
//                  電壓傳感器用來精確監視飛行時的電池狀態。
//
//            *說明*
//                  在安裝好硬件之後，需要告知 APM 你的設置。
//                  In your Config.h file you need to Enable your voltage monitoring, to do
//                  this you need to change the statement from 
//                  BATTERY_EVENT "DISABLED" to "ENABLED"
//
//            *AVAILABLE OPTIONS*
//                 BATTERY_EVENT DISABLED
//                 BATTERY_EVENT ENABLED
//
//       *****************
//         *SELECTED OPTION*
     #define BATTERY_EVENT ENABLED
 //       *****************
```

## 1.2 BATTERY\_SELECTION ##

```
 //                    *EXPLAINED*
//                                Because everyone uses different batteries you need to tell the APM what sort of batteries 
//                                you use, unfortunately there are too many types of batteries and we cannot #define all of
//                                them so we only have a selection between most common used ones.
//
//                      *INSTURUCTIONS*
//                            The most commonly used batteries is a 3cell(3S) or a 4cell(4S) to find out what you have look
//                             On the label or spec sheet of your battery you will see a descriptions that looks something
//                             like this 」20-30C DISCHARGE 5000mah 4 cell 14.8V」 that means that you have a 4 cell(4S) 
//                             battery and you need to tell the APM that. Here is how change the statement form
//                            BATTERY_TYPE    0  (default/3S) to BATTERY_TYPE  1  (4S)
//
//      **************
//    *SELECTED OPTION*
     #define BATTERY_TYPE  1
//    ***************
```

## 1.3 LOW\_VOLTAGE\_SETTING ##

```
//                        *EXPLAINED*
//                             Exactely as the title suggests ,pick a voltage that 
//                             you consider as a low voltage.
//                        
//                        *INSTRUCTIONS*
//                             Change statement from #define LOW_VOLTAGE 11.4
//                             to any voltage you consider as low for your battery type.
//
//    *****************
//    *SELECTED OPTION*
     #define LOW_VOLTAGE  11.4                         
//    *****************
//
```

### 1.4 INPUT\_VOLTAGE ###

```
                             *EXPLAINED*
                                 In order to insure more accurate voltage readings you 
//                               can measure the Voltage on the 5V rail on your APM oilpan
//                               and #define it here.
//
//                            *INSTRUCTIONS*
//                               NOTE:you need a multimeter for this.
//                               Take the multimeter and measure the voltage 
//                               with the negative probe on the bottom row of the servo
//                               connectors on APM board and with the positive probe on
//                               the 5V rail on oilpan and insert the reading here.
//                               NOTE:if you have no multimeter insert 5V (defualt)
//    *******************
//    *SELECTED OPTION*
     #define INPUT_VOLTAGE 5.0
//    *******************
```

### 1.5 VOLT\_DIV\_RATIO ###

```
                        (under constuction)
                       //#define VOLT_DIV_RATIO      3.0 
```


