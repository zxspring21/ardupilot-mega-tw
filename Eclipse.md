= 使用 Eclipse 作為開發 ArduPilot Mega 的工具 =

## 總覽 ##
[Eclipse](http://www.eclipse.org) 是一種為多種語言 IDE 開發工具。使用 Eclipse CDT 並安裝 Git 插件，就可以開發 ArduPilot Mega。

在這裡的介紹是基於最新的 Eclipse Indigo (3.7.2)。

## 目前狀態 ##
The make-based build system for APM 的建置有支援 Windows、MacOS 及 linux systems。但是你仍然需要安裝 Arduino IDE 因為建置流程還是會使用到它的部份工具。

APM make-based build system 的祥細說明請見 BuildingWithMake。

ardupilot-mega 程式碼目錄中有 README.txt 的建置說明。Eclipse 的說明也許也可以運作，但是會更複雜。

## 安裝 Eclipse 及其他工具 ##

下載及安裝 C/C++ 開發工具的 Eclipse IDE。安裝現有的 Eclipse，CDT 是必需的；如果它尚未安裝，請使用 Eclipse 內部程式安裝器(Help/Install New Software)。如果你只打算使用 Eclipse 開發 APM，請避免被引導安裝所有的插件。

## 建立及移入 Workspace ##

開啟 Preferences 頁面，並選擇 **C/C++/File Types**，如果在清單中沒有`*.pde`的選項，請使用\*New...**按鈕來加入`*.pde` 格式到`C++ Source File`的型態。文件關聯不匯入偏好設定已經是 Eclipse 長久以來的錯誤。**

Arduino 的 .pde 檔案在 Eclipse 的程式碼分析功能中無法正確運作。當編輯 Arduino 代碼時為避免有數百個 "undeclared" 和 "unused" 的錯誤，請關閉這些錯誤提示的功能。請這麼做: 在 **Window** 選單下面選擇 **Preferences**，展開 **C/C++** 的頁面，選擇 **Code Analysis\*然後將\*Syntax and Semantic Errors\*的勾選拿掉。**

現在你可以為 ardupilot-mega 的程式碼建立一個專案。在  **File** 選單中選擇 **Import...** 的選項，點開 **C/C++**，選擇 **Existing Code as Makefile Project**，按下 **Next**。請確認你所複制的 ardupilot-mega 代碼資料夾已經在 **Existing Code Location** 的裡面，然後按下 **Finish**。

為了要為你的飛行器建置 APM 程式碼，請選擇電路板，你會需要編輯建置設定。在 Project Explorer 上使用右鍵點擊你的專案(可能稱作 ardupilot-mega)。選擇 **C/C++ Build** 並且透過 ardupilot-mega 後加入飛行器目錄來修改 Build Directory。例如，變更 `${workspace_loc:/ardupilot-mega}` 為 `${workspace_loc:/ardupilot-mega/ArduPlane}`。現在按下 **Behavior** 頁面。下一步到 **Build (Incremental Build)**，用你建置的目標取代 "all" ，如果你有一個最近的APM板也許會是 "apm2" 。其他建置目標可以也放在這裡包含了 SIL (Software in the Loop) 及各種多旋翼框架。您可以看看飛行器目錄中的 Makefile 文件，看看有什麼其他的目標可用。

## 建置 ##
請確認您有 C/C++ 的視角選項(視角控制項在這個頁面的右上方)。

在 Project Explorer 選取你的專案(一般來說會在視窗的左側)，然後按下工具列上錘子圖示的按鈕。

可以在視窗底部的 Console tab 中監控建置的進度。雙擊一個警告及錯誤就會開啟一個已經選擇相關原始碼的文字編輯頁面。問題包含了警告及錯誤，都會在 Problems tab 中標示出來，也會將側邊的文字編輯器叫出來。

Tasks tab 可以方便標記出 FIXME、TODO 及 XXX。

更多使用 IDE 開發 C/C++ 的祥細說明請參考 Eclipse 及 CDT 文件。

## 有用的插件 ##
AVR Eclipse 插件，可能是 APM 編程中最常用的。以目前的版本而言，它加入了一個 AVR Device Explorer 頁面到視窗的底部的地方，這個可以幫助找到 AVR 寄存器的名稱。

EGit 插件允許我們在 Eclipse 內部做版本控管，也許可以幫你更新、比對及 commit 程式而不用離開 IDE。