## 盤旋模式 ##

Ardupilot 使用簡單的矢量場導航策略來保持圍繞某一地點盤旋。用戶可以在頭文件中自定義盤旋半徑。飛機處於該模式時也可以人工微調。

![http://api.ning.com/files/lPtcJ8AiWjopWlqtnnYqnJUhR3iCQqQ4cjmFbx5Nr8khjtV3gGCbyWoPybr8cxgQHRSGKLsM5JFjhvk62EurxeUzIjI3kU6L/Loiter.png](http://api.ning.com/files/lPtcJ8AiWjopWlqtnnYqnJUhR3iCQqQ4cjmFbx5Nr8khjtV3gGCbyWoPybr8cxgQHRSGKLsM5JFjhvk62EurxeUzIjI3kU6L/Loiter.png)

## 細節 ##

盤旋半徑可由地面控制站、Waypoint\_writer固件及其他工具設置。該值應調整為比飛機安全轉彎半徑略大。默認的半徑是40米。Ardupilot 在執行返航命令，到達出發點後將自動盤旋。如果你想讓 Ardupilot 在某一點上空盤旋，使用任務腳本。

## 矢量場 ##

矢量場是一個複雜的話題。基本上我們用它來根據接近半徑的程度來調整方向。如果 Ardupilot 處於半徑上, 方向將與路徑偏移90°。接近或原理將得到一個較小的偏移角度。
代碼為:
```
if(LOITER){ 
	if (wp_distance <= loiter_radius){
		nav_bearing -= 90;//degrees
		
	}else if (wp_distance < (loiter_radius * 2)){
		power = -((wp_distance - (loiter_radius * 2)) / loiter_radius);
		power = constrain(power, 0, 1);
		nav_bearing -= power * 9000;
	}else{
		// deal with crosswinds in between waypoints
		update_crosstrack();
	}
}
			

```