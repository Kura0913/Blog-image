---
title: Unreal Engine設定及除錯
date: 2023-07-20 20:09:05
tags: [Unreal Engine]
categories: 
- [Unreal Engine, Unreal Engine 設定相關]
keywords: Unreal Engine,UE4,UE5,Unreal Engine 4,Unreal Engine 5,Unreal Engine Settings
---

哈囉，這篇文章會為各位帶來一些Unreal Engine的設定，這些都是我在開發的過程中，有遇到需要調整的項目，之後如果有遇到新的問題，也會持續更新在這篇文章，那麼話不多說，馬上開始!!

<!-- more -->


### Visual Studio版本更改

有些人使用的Visual Studio版本或許不是2022的版本，或是使用其他的編譯器，但又不想重新下載，其實是有解決辦法的，點擊左上角
Edit->Editor Preferences->General->Source code， 會看到"Source Code Editor"，點開來改成自己想使用的編譯器就行了

![](https://github.com/Kura0913/Blog-image/blob/main/UnrealEngineSetting/Setting_1.png?raw=true)

### 解決切換畫面後，畫面卡頓問題

在模擬的時候常常會畫面切來切去，但只要一點到Unreal以外的視窗，模擬的畫面就會非常卡頓，這時可以透過更改設定來解決，
Edit->Editor Preferences->General->Performance，把"Use Less CPU when in Background"取消掉，就可以解決這個問題

![](https://github.com/Kura0913/Blog-image/blob/main/UnrealEngineSetting/Setting_2.png?raw=true)

### 打包地圖缺失

打包地圖的時候，可能會遇到地圖只打包了你正在使用的地圖，或是預設地圖，此時就要透過設定來修改打包的目標，**建議每次的打包，都要執行接下來的設定**
Edit->Project Settings->Project->Maps & Modes，下方有個"Default Maps"的設定，建議將Editor Startup Map和Game Default Map都換成執行檔開啟執行時，第一張要執行的地圖

![](https://github.com/Kura0913/Blog-image/blob/main/UnrealEngineSetting/Setting_3.png?raw=true)

接著，到Project->Packaging->Packaging->Advanced，有一個"List of maps to include in a packaged build"的選項，點擊"加號"之後，到專案的資料夾下找出想打包的地圖，有幾張就加幾張

![](https://github.com/Kura0913/Blog-image/blob/main/UnrealEngineSetting/Setting_4.png?raw=true)

這樣打包時就會把在List裡的地圖通通打包進去囉
