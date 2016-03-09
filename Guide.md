**更新 1/13: APM 代碼不再保存在 Google Code 的 Git 程式庫。現在它已經移到 [GitHub](https://github.com/diydrones)。**

## APM的代碼庫的貢獻者導引 ##

**如何成為貢獻者**: 祥情請見 [這裡](http://diydrones.com/profiles/blogs/how-to-contribute-to-the)。簡短的版本：我們一直在尋找新的團隊成員，但要避免破壞現有的工作或不穩定的代碼，我們必須逐步的把人引導進來。對於新加入的人，您需要提交訪問 SVN 程式庫，這可以由現有的團隊成員之一授予。在一般情況下，最好是提出(或更好，原創)特定功能的增加或錯誤修復，並證明你的代碼能夠適當的到做到這一點。如果這正好與該項目的方向，你會被添加到開發人員郵件列表和訪問 SVN的權限。

**一旦你有 SVN commit 的權限:** 當你擁有一個 SVN提交權限，你可以檢查到資源庫中的代碼(任何人都可以檢查代碼，但只有經過批准的開發人員可以提交更改的代碼)。這裡使用的工具：

  * **SVN client**: 在 Windows，我們建議使用[Tortoise SVN](http://tortoisesvn.tigris.org/)，整合進Windows桌面。所有的命令都是通過右擊任何桌面上的文件夾。對於初學者來說，你可以到版本庫瀏覽器並探索的程式庫的資料夾。當你找到一個你想要修改的程式，Check Out 該資料夾到您的本地硬碟​​。當您完成編輯代碼，將其提交(Commit)回來，瀏灠您所做的更改。

  * **文字編輯器**: 雖然 Arduino 的IDE有一個內置的文字編輯器，它缺點是line endings。我們的 SVN 設置要求參與者使用一個更好的文字編輯器，正確處理line endings。在 Windows，我們建議使用[Notepad++](http://notepad-plus-plus.org/)

**提交(Commit)代碼的規則**: 除非你非常確信你正在做什麼，和你的變化是非常輕微的，你或許應該為[ardupilot-mega GIT 程式庫](http://code.google.com/p/ardupilot-mega/source/clones)[建立 Clone](http://code.google.com/p/ardupilot-mega/wiki/GitCLI)並且在commit 至主程式庫前請求進階開發人員審核你的程式。這樣，你不會取下來大家都在工作的主要代碼，並且可以確定現有程式是很正確的。

**程式語言**: 我們僅支援 C 及 C++。以經驗法則而言，Arduino 編譯器無法理解的代碼是不能被提交的。