== 使用Git 擴展 ==

對於 Windows用戶，使用Git的最佳途徑之一就是透過 Git 的擴展工具，其中最常見的 Git 命令添加到右鍵單擊的 Windows 功能選單。

你可以在[這裡](http://code.google.com/p/gitextensions/)下載 Git 擴展工具。安裝完成就會出現在 Windows 的功能選單，如下圖所示：

![http://wiki.ardupilot-mega.googlecode.com/git/images/gitextensions.png](http://wiki.ardupilot-mega.googlecode.com/git/images/gitextensions.png)


### 由 Git 庫取得新的程式碼 ###

你最主要會從 Google Code Git 程式庫更新最新的代碼，要做到這點就是選擇選單中的「PULL」。

當你首次使用你必須告訴它程式庫在哪，選擇「Manage Remotes」輸入你想要取得的程式庫位址，APM的如圖所示。

![http://wiki.ardupilot-mega.googlecode.com/git/images/gitextensions2.png](http://wiki.ardupilot-mega.googlecode.com/git/images/gitextensions2.png)

一旦設定完成，你可以從這個畫面取得新的代碼，請確認你的設定是否如下圖所示：

![http://wiki.ardupilot-mega.googlecode.com/git/images/gitextensions3.png](http://wiki.ardupilot-mega.googlecode.com/git/images/gitextensions3.png)


### 提交程式碼 ###

如果你有權限提交代碼至程式庫，請從右鍵功能選單中選擇「Commit」:

![http://wiki.ardupilot-mega.googlecode.com/git/images/gitextensions7.png](http://wiki.ardupilot-mega.googlecode.com/git/images/gitextensions7.png)

在下一個畫面你必須先「Stage」檔案(如果有多個，請點擊多個箭頭的圖示，將所有的檔案設定為審議階段)。

![http://wiki.ardupilot-mega.googlecode.com/git/images/gitextensions4.png](http://wiki.ardupilot-mega.googlecode.com/git/images/gitextensions4.png)

然後寫下 commit 的訊息後點擊「Commit & push」:

![http://wiki.ardupilot-mega.googlecode.com/git/images/gitextensions5.png](http://wiki.ardupilot-mega.googlecode.com/git/images/gitextensions5.png)

最後，在此視窗的頂部選擇你想 push 的 branch ：

![http://wiki.ardupilot-mega.googlecode.com/git/images/gitextensions6.png](http://wiki.ardupilot-mega.googlecode.com/git/images/gitextensions6.png)