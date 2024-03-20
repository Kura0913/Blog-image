---
title: Unreal Engine創建新專案
date: 2023-08-06 13:11:05
tags: [Unreal Engine]
categories:
- [Unreal Engine, 創建新專案]
keywords: Unreal Engine,UE4,UE5,Unreal Engine 4,Unreal Engine 5,Unreal Engine新專案,創立專案
---


### 開始開發
安裝好Unreal Engine之後，接下來就要開始開發了，本篇會介紹建立專案時，有哪一些設定可以調整，來幫助你在開發的時候，可以更加的舒適、便利，教學開始~

<!-- more -->

### 開啟引擎
首先打開Epic Game Launcher，並到Unreal Engine的介面，對欲用來開發的引擎版本按啟動(若還沒安裝引擎，可以至[本篇](https://kura0913.github.io/2023/07/07/UnrealEngineInstall/))

![](https://github.com/Kura0913/Blog-image/blob/main/CreateNewProject/1.png?raw=true)

### 建立新專案

啟動之後，會跳出選擇或創建專案的視窗，圖中1號紅框處是本機所有不同版本的專案，如果沒有就會是空的，2號紅框處除了第一個是現有專案選項外，其他都是用來創立專案用，根據想開發的內容來選擇對應的起始專案，創立出來的專案也會提供相關的基礎模型、示範功能等等內容，對於新手開發者來說是相當有幫助的

![](https://github.com/Kura0913/Blog-image/blob/main/CreateNewProject/2.png?raw=true)

以Games作為示範，點選Games之後，中間還有其他更細的分類，就依自己想開發的遊戲類型作選擇，如果你夠老練可以選擇Blank，Blank不會提供任何的範例

![](https://github.com/Kura0913/Blog-image/blob/main/CreateNewProject/3.png?raw=true)

這邊就選擇Third Person作為專案，接下來看到右邊有好幾個選項，會一一介紹對應的功能：

* **1.Blueprint or C++:**
這邊是用來選擇預設的開發模式，Blueprint是將程式碼模塊化，這些模塊也是透過C++設計出來的功能，透過拉線連接模塊來設計功能；C++就是直接用程式碼來進行開發，你可以透過程式碼來設計角色、物件的功能，甚至是製作專屬的Blueprint模塊，C++模式同時也能使用Blueprint模式，遇到比較簡單的設計可以用Blueprint偷懶一下。這邊建議剛接觸Unreal Engine的新手先選用Blueprint，使用一段時間對於Blueprint模塊較為熟悉後，再轉到C++開發，會發現有很多內建Function名稱與模塊是對應的，學習起來比較輕鬆。
* **2.Target Platform:**
依據最終想匯出的目標平台做選擇
* **3.Quality Present:**
設定專案開發時的測試影像品質，預設是Maximum，如果想要使用自訂的設定，可以選擇Scalable
* **4.Starter Content:**
如果想要使用所有Unreal Engine內建提供的物件，可以把這個選項打勾，物件相關的檔案就會在創建專案時順便匯入
* **5.Raytracing:**
選擇是否啟用光線追蹤的功能

![](https://github.com/Kura0913/Blog-image/blob/main/CreateNewProject/4.png?raw=true)

最後設定好專案的儲存路徑及專案名稱，點選Create

![](https://github.com/Kura0913/Blog-image/blob/main/CreateNewProject/5.png?raw=true)

創建完成之後，會自動開啟專案，可以按"Alt+p"執行看看專案是否正常

![](https://github.com/Kura0913/Blog-image/blob/main/CreateNewProject/6.png?raw=true)
![](https://github.com/Kura0913/Blog-image/blob/main/CreateNewProject/7.png?raw=true)

成功執行代表專案建立成功，可以開始開發了~

