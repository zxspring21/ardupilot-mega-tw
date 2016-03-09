**更新 1/13: APM 代碼不再保存在 Google Code 的 Git 程式庫。現在它已經移到 [GitHub](https://github.com/diydrones)。**

## 使用 Git ##

Git是一個分佈式版本控制系統，使我們能夠創造一個更有效的開發程序，既提高了程式碼的審批程序，使開發者更容易作出貢獻與建議。

[這裡](http://nvie.com/posts/a-successful-git-branching-model/)有篇很好的文章，說明分佈式的版本控制發展工程。

Google Code 上所有的 DIY Drones 源碼庫都已經從 SVN 遷移到 Git 上了。本文簡單介紹如何在 Windows 下使用 Git。


---

## 安裝 GIT ##
**步驟 1**: 下載 [MySysGit](http://code.google.com/p/msysgit/)。它會安裝一些程序，其中一個是 GitGUI。把圖標拖到桌面上。

**步驟 2**: Google Code 有點笨，不像其他 Git 庫那樣使用 SSH，所以我們不得不用一個傻瓜步驟讓 Windows 記住 Git 用戶名和密碼。

在根目錄建立一個文件夾 C:/HOME，在文件夾下建立一個文本文件叫 `_netrc` (沒有後綴)。所以文件名就是 `C:/HOME/_netrc`

在文件中輸入以下內容 (可以從[這裡](https://code.google.com/hosting/settings)得到 Google Code 密碼):

```
machine code.google.com
login (your Gmail login, which is usually your email address)
password (your Gmail password)
```

然後右鍵單擊我的電腦，告訴 Windows 該文件的路徑:

![http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/gitsetup.png](http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/gitsetup.png)


---

## 在你的電腦建立 ArduPilot-mega 程式庫的 Clone ##
**步驟 3**: 打開 GitGUI，選擇 Clone Existing Repository

http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/GIT.PNG

**步驟 4**: 輸入需要簽出的庫的 URL, 指定一個文件夾。單擊 "Clone".

http://wiki.ardupilot-mega.googlecode.com/git/images/GIT2.PNG


---

## 切換到另一個分支 ##
**步驟 5**: You may actually want to work in one of the branches. In the Branch menu, select "Create New Branch" and pick the branch you want to work with:

http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/GIT0.PNG


---

## 修改、分期和提交更改 ##
**步驟 6**: 編輯並保存要修改的文件。我們推薦 [Notepad++](http://notepad-plus-plus.org/) 編輯器.

**步驟 7**: 完成之後，單擊 Rescan，檢測更改.

http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/GIT4.PNG

**步驟 8**: 現在單擊 Stage Changed，輸入一段提交說明:

http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/GIT6.PNG

**步驟 9**: 現在單擊 Push。這將把文件上傳到 Google Code 庫. 完工了!

http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/GIT5.PNG


---

### 更新到最新代碼 ###

在 GitGUI 上需要兩部: Fetch 然後 Merge ([TortoiseGit](http://code.google.com/p/ardupilot-mega/wiki/GitTortoise) 裡比較簡單, 只要一個 Pull 命令就行了):

**首先 Fetch:**

![http://wiki.ardupilot-mega.googlecode.com/git/images/gitguifetch.png](http://wiki.ardupilot-mega.googlecode.com/git/images/gitguifetch.png)

**然後 Merge:**
(記住選擇 "tracking branch")

![http://wiki.ardupilot-mega.googlecode.com/git/images/gitguimerge.png](http://wiki.ardupilot-mega.googlecode.com/git/images/gitguimerge.png)

註: 如果在合併步驟遇到衝突，你可以使用 mergetool 解決衝突，或者你可以簡單地扔掉在這個分支上所有衝突的變更，Rest GitGUI。
http://wiki.ardupilot-mega.googlecode.com/git/images/GitInstructions/GitGuiReset.PNG