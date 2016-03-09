# APM 的失效保護(FailSafe)功能 #

APM 提供有限的失效保護功能，主要設計來達到兩種目的:

  1. 檢測是否完全喪失 RC 信號(前提是 RC 接收器能夠產生一個可預測的信號喪失狀態)及初始自動模式反饋的定義，例如回到起飛位置。有些 RC 設備可以做到，但有些則不行(如果你的設備有提供這項功能，請參考下列的祥細說明)。
  1. 檢測遙測模組是否喪失信號超過 20 秒，切換至(RTL)模式，(就是所謂的地面站失效保護(GCS Failsafe))。

這裡是失效保護\*做不到的事**:**

  1. 如果一個或一個以上的個別 RC 通道失效或未連接。
  1. 如果你飛的太遠或撞擊到地面。
  1. 自動駕駛儀硬體失效，例如電壓過低或空中重置。
  1. 如果 APM 軟體未正確開啟。
  1. 其他飛行器的問題，例如馬達故障或電池沒電(如果有正確安裝電壓/電流感應器，後者可以透過主程式碼設置)。
  1. 不然就是設置或飛行的錯誤。


---

# Arduplane 失效保護文件(APM 2.x) #


## 油門失效保護(FailSafe) ##

**如何運作。**你的 RC 發射器輸出的 PWM 訊號會經由接收器傳至 APM。每個發射器上的通道都有 PWM 的範圍通常介於 1100 - 1900，中立點為 1500。當你在 the Mission Planner 中校驗無線電時，你所有的數值都會是 1500。移動遙桿時、旋鈕及開關時就可以設置每個通道的 PWM 範圍。APM 會監控油門通道，如果低於 THR\_FS\_VALUE(預設為 950)它會進入失效保護模式。

RC 發射器通常每個通道的預設範圍為 -100% 至 100%，然而大多數的發射器都會允許你調整到 -150% 及 150% 。預設的設置中，會把你的油門設為 -100% 轉換成數值就會接近 1100 而 -150% 數值就會接近 900。我們要實現的是讓你的接收器知道油門可以低至 -150% 的，但保持 APM 控制範圍在 -100% 到 100% 之間。意謂著在飛行時，我們的油門值的範圍是 1100 - 1900。但如果我們超出 RC 範圍，如果接收器設置正確的話，將可以拉到最低的油門值約為 900。這個值將會低於 THR\_FS\_VALUE 並且會觸發 APM 進入失效保護模式。

首先當 APM 量測到信號直過低超過 1.5 秒就會進入短暫的失效保護(FS\_SHORT\_ACTN，0=關閉，1=開啟)。預設的短暫失效保護為繞圈模式。如果信號丟失超過 20 秒 APM 將會進入長失效保護(FS\_LONG\_ACTN，0=關閉，1=開啟)。預設的長失效保護為 RTL(回到出發地)。

```

         Ext. Range       Normal Range       Ext. Range
    |-----------------|-----------------|-----------------|
  -150%             -100%              100%              150%
   
    |_________________|
             |
          Failsafe

```


**設置**

  1. 將 THR\_FS\_Value 設為 1(0=關閉，1=開啟)開啟油門的失效保護。
  1. 首先開啟你的發射器並且將油門行程延長至 -100%，我們要擴展的油門行程要超過它的最低數值。
  1. 完成後綁定你的接收器。這個步驟會讓你的接收器知道油門通道的最低數值。
  1. 接下來恢復你在發射器所做的第一步，以限定油門在原來的範圍。
  1. 使用 Mission Planner 做無線電校驗。
  1. 完成無線電校驗後，降下發射器上的油門並且讀取已經輸出到 Mission Planner 通道上的 PWM 數值。
  1. 關閉發射器。你應該會看到數值會有顯著的下降。這個數值就是在飛行中 RC 連結丢失時會傳送到 APM 的 PWM 數值。
  1. 請確認 THR\_FS\_VALUE 是個適當數值，它會觸發 APM 的失效保護功能。
  1. 請確認 FS\_SHORT\_ACTN 及 FS\_LONG\_ACTN 皆為開啟的狀態(設為 1)。
  1. 將 RC 發射器開啟與 Mission Planner 連接。確認 HUD 的右下角你是在自動模式中"飛行"(手動、穩定、FBW都是可以的)。
  1. 關閉發射器。 1.5 秒後飛行模式會切至繞圈模式。20 秒後飛行模式會切至 RTL。如果你有看到這個狀狀，你的失效保護功能就已經設置正確。



**發射器教程:**

[Spektrum Setup](http://diydrones.com/profiles/blogs/spektrum-dx8-and-ar8000-failsafe-setup)


---

## 地面站失效保護 ##

**如何運作。** 當你是使用地面站的遙測模組飛行，如果丟失遙測訊號 APM 可以使用程式觸發進入失效保護模式。假如發生 APM 中斷接收 MAVlink (遙測通訊協定)的活動訊號超過 20 秒，地面站失效保護(FS\_GCS\_ENABL，0=關閉，1=開啟)將會觸發 APM 進入長失效保護並且將飛行模式變更為 RTL。

**設置**

  1. 將 FS\_GCS\_ENABL 設為 1 ，開啟功能。
  1. 使用遙測模組連接 Mission Planner。確認 HUD 的右下角你是在自動模式中"飛行"(手動、穩定、FBW都是可以的)。
  1. 拔下其中一個遙測無線電。幾分鐘後關閉你的 APM。(記的 APM 不會馬上進入失效保護直到 MAVlink 閒置超過 20 秒)。
  1. 將 APM 接上 Mission Planner 並且下載 logs。驗証 APM 的 log 是否在 MAVlink 閒置超過 20 秒後進入 RTL 。



---


## 程式碼 ##

**Short Failsafe.** `events.pde line 4`
```
static void failsafe_short_on_event()
{
	// This is how to handle a short loss of control signal failsafe.
	failsafe = FAILSAFE_SHORT;
	ch3_failsafe_timer = millis();
    gcs_send_text_P(SEVERITY_LOW, PSTR("Failsafe - Short event on"));
	switch(control_mode)
	{
		case MANUAL:
		case STABILIZE:
		case FLY_BY_WIRE_A: // middle position
		case FLY_BY_WIRE_B: // middle position
			set_mode(CIRCLE);
			break;

		case AUTO:
		case GUIDED:
		case LOITER:
			if(g.short_fs_action == 1) {
				set_mode(RTL);
			}
			break;

		case CIRCLE:
		case RTL:
		default:
			break;
	}
    gcs_send_text_fmt(PSTR("flight mode = %u"), (unsigned)control_mode);
}
```



**Long Failsafe.** `events.pde line 35`
```

static void failsafe_long_on_event()
{
	// This is how to handle a long loss of control signal failsafe.
	gcs_send_text_P(SEVERITY_LOW, PSTR("Failsafe - Long event on"));
	APM_RC.clearOverride();		//  If the GCS is locked up we allow control to revert to RC
	switch(control_mode)
	{
		case MANUAL:
		case STABILIZE:
		case FLY_BY_WIRE_A: // middle position
		case FLY_BY_WIRE_B: // middle position
		case CIRCLE:
			set_mode(RTL);
			break;

		case AUTO:
		case GUIDED:
		case LOITER:
			if(g.long_fs_action == 1) {
				set_mode(RTL);
			}
			break;

		case RTL:
		default:
			break;
	}
}
```