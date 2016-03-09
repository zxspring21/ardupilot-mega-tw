# 介紹 #

APM 開發組現在使用 git 源代碼管理系統。你需要使用一些命令行來使用 google code 的 git 托管。

# 將程式複製於自己的電腦 #

你需要做的第一件事就是 clone 代碼庫。需要的命令是:

```
  git clone https://code.google.com/p/ardupilot-mega APM
```
這將在當前目錄中創建一個名為「APM」的目錄。克隆需要相當長一段時間，因為它會帶來過代碼樹的歷史和當前的狀態。

# 設置 .netrc #

請注意，我們沒有指定在上述 clone 命令的用戶名。如果你要提交到庫中，這是非常重要的，因為如果你指定一個用戶名，你會發現在每次上傳代碼的時候都要輸入密碼。為了告訴 google code 你的用戶名和密碼，你需要在 home 目錄中創建一個 .netrc 文件。這是目前避免在上傳時輸入密碼的唯一方式。

.netrc 文件應該像這樣:
```
machine code.google.com 
login YOURGOOGLEEMAIL@gmail.com
password YOURGOOGLECODEPASSWORD
```
# 設置你的 git 用戶名 #

在提交任何東西之前，你應該設置你的 git 用戶名和 email, 以便正確地標識你自己。
```
 git config --global user.email YOUREMAILADDRESS
 git config --global user.name "Your Full Name"
```

# 使用分支 #

GIT 允許你在分支之間進行輕易切換，但首先你需要下載他們。
該項目的「master」分支存放穩定的特性和版本，其他一些分支用於開發不適合廣泛發佈的實驗性功能。
按照[如何複制遠程分支](http://stackoverflow.com/questions/67699/how-do-i-clone-all-remote-branches-with-git)的說明下載實驗性分支。

# 用遠端的 Clone 進行編輯 #
## 利用遠端的 Clone 建立本地端的 ##

The preferred way for developers to submit new code is via a remote clone in the ardupilot-mega repository.

一旦建立好你的[遠端 clone](http://code.google.com/p/ardupilot-mega/wiki/GitPatches)，就可以在你的開發腦建立一個本地端 clone。

這是使用我的遠端 "philcole1234-wip"做為範例。請參見網址中遠端 Clone 的"checkout"網頁。使用這個網頁上的密碼就可以建立你的 .netrc 檔案。

你會需要 .netrc ( 在 Windows 是"_netrc")檔案設定如下。_

```
$ git clone https://code.google.com/r/philcole1234-wip
```

這將建立一個類似上述的本地 clone，但這是你的遠程 clone，而不是主要的程式庫。

## 在本地端的 Clone 開發然後再 push 至遠端的 Clone ##

_Content is coming._

## 從主程式庫合併到 Clone 的新內容 ##

當你開發你的代碼 commit 到你的本地庫，並 push 到你的遠程 clone 與他人分享。

遲早你會需要從主程式庫合併到 clone 的其他工作。

當你 push 至主程式庫就會執行合併。

![http://wiki.ardupilot-mega.googlecode.com/git/images/GitInstructions/GitUpdateCloneFromTrunk.png](http://wiki.ardupilot-mega.googlecode.com/git/images/GitInstructions/GitUpdateCloneFromTrunk.png)

首先要做的是添加“遠程”的主程式庫到你的本地庫。

```
$ git remote add apm-master https://code.google.com/p/ardupilot-mega
```

這會告訴你的本地庫遠端庫\*ardupilot-mega\*與另一個別名\*apm-master\*有關聯。


現在，顯示您所配置的主控端：
```
$ git remote -v
apm-master      https://code.google.com/p/ardupilot-mega (fetch)
apm-master      https://code.google.com/p/ardupilot-mega (push)
origin  https://code.google.com/r/philcole1234-wip (fetch)
origin  https://code.google.com/r/philcole1234-wip (push)
```

**origin** 是當你執行\*clone\*命令時建立本地庫的預設的名稱。

使用 **pull** 命令來執行合併。

```
$ git pull apm-master master
From https://code.google.com/p/ardupilot-mega
 * branch            master     -> FETCH_HEAD
Removing Tools/ArdupilotMegaPlanner/defines.h
Removing Tools/ArdupilotMegaPlanner/arducopter-fgmodel.zip
Auto-merging Tools/ArdupilotMegaPlanner/RAW_Sensor.es-ES.resx
Removing Tools/ArdupilotMegaPlanner/MAVLinkTypesenum.cs
Removing Tools/ArdupilotMegaPlanner/GCSViews/test.cs
< The number of lines depends on how much changed since last time>
```

**apm-master\*是當您添加遠端時的別名。**master**指定想要的遠端程式庫的分支。使用Git，主分支是主要的開發主幹。如果您需要其他部份，你可能要知道什麼你想要的。**

當地一個合併完成(您可能需要解決衝突)，那麼你就可以\*push\*到遠端的 clone。

```
$ git push
Counting objects: 2, done.
Delta compression using up to 2 threads.
Compressing objects: 100% (2/2), done.
Writing objects: 100% (2/2), 398 bytes, done.
Total 2 (delta 1), reused 0 (delta 0)
remote: Scanning pack: 100% (2/2), done.
remote: Storing objects: 100% (2/2), done.
remote: Processing commits: 100% (2/2), done.
To https://code.google.com/r/philcole1234-wip
   d44caf3..6a7728e  master -> master
```

**push** 不帶參數使用預設遠端的 **origin** 並且預設分支為 **master**。

現在你的遠端 clone 已經將你所做的工作與 ardupilot-mega 的副本合併。