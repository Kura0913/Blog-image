---
title: 架設AirSim環境及安裝AirSim Plugin
date: 2023-07-08 14:19:18
tags: [Unreal Engine, Airsim]
categories: 
- [Unreal Engine, Airsim環境架設]
keywords: Unreal Engine,UE4,UE5,Unreal Engine 4,Unreal Engine 5,AirSim,airsim,Airsim,AirSim 安裝,Airsim 安裝,airsim 安裝,AirSim安裝,Airsim安裝,airsim安裝
---


### 前置作業
在安裝AirSim前，你必須完成Unreal Engine的安裝，安裝方式請看：[Unreal Engine安裝](https://kura0913.github.io/2023/07/07/UnrealEngineInstall/)

<!-- more -->

### 安裝Git
至[Git官網](https://git-scm.com/)下載最新版的Git，並且一定要安裝 Git Bash 功能
(之後會再寫一篇安裝Git與Github連結設定的教學)

### 安裝 Visual Studio 2022
點擊[連結](https://visualstudio.microsoft.com/zh-hant/vs/)下載 Visual Studio 2022，免費版請選擇Community版本

安裝完成後，請安裝下圖中的組態

![](https://github.com/Kura0913/Blog-image/blob/main/InstallAirSimPlugin/VSinstall_1.png?raw=true)
![](https://github.com/Kura0913/Blog-image/blob/main/InstallAirSimPlugin/VSinstall_2.png?raw=true)

安裝完成後，可以點擊修改，檢查組態是否安裝完整，**特別至個別元件檢查是否安裝到"Windows 10 SDK 10.0.19041"**

![](https://github.com/Kura0913/Blog-image/blob/main/InstallAirSimPlugin/VSinstall_3.png?raw=true)
![](https://github.com/Kura0913/Blog-image/blob/main/InstallAirSimPlugin/VSinstall_4.png?raw=true)


### 安裝 AirSim

**接下來的步驟相當繁瑣，請按照步驟安裝，否則可能會安裝失敗**

操作流程可以參考[官方文件](https://microsoft.github.io/AirSim/build_windows/)

根據安裝的引擎版本，請分別至對應的連結：[4.X.X](https://github.com/microsoft/AirSim)、[5.X.X](https://github.com/CodexLabsLLC/Colosseum)

**註：目前得知Unreal Engine 5.0.3無法成功安裝AirSim，UE5版本選擇請選擇5.1以上**

接下來會以UE5的連結做示範，進到頁面後，先點選"Code"，然後複製網址

![](https://github.com/Kura0913/Blog-image/blob/main/InstallAirSimPlugin/AirSimInstall_1.png?raw=true)

接下來到要安裝AirSim環境的資料夾，點選右鍵，Git Bash Here，<font color=#FF0000>**請注意，絕對不可以安裝在C槽，路徑要全英文**</font>

![](https://github.com/Kura0913/Blog-image/blob/main/InstallAirSimPlugin/AirSimInstall_2.png?raw=true)

打上下列指令：
UE5:
```
git clone https://github.com/CodexLabsLLC/Colosseum.git
```

UE4:
```
git clone https://github.com/microsoft/AirSim.git
```
看到下圖代表已經下載完成

![](https://github.com/Kura0913/Blog-image/blob/main/InstallAirSimPlugin/AirSimInstall_3.png?raw=true)

開啟"Developer Command Prompt for VS 2022"，用"cd your_file_path"前往安裝AirSim環境的目錄下

![](https://github.com/Kura0913/Blog-image/blob/main/InstallAirSimPlugin/AirSimInstall_4.png?raw=true)

輸入"build"，等待它安裝，會需要一段時間

![](https://github.com/Kura0913/Blog-image/blob/main/InstallAirSimPlugin/AirSimInstall_5.png?raw=true)

看到顯示下圖字樣，代表建置完成

![](https://github.com/Kura0913/Blog-image/blob/main/InstallAirSimPlugin/AirSimInstall_6.png?raw=true)

接著，可以點擊資料夾目錄下的Unreal，會看到一個名叫"Plugins"的資料夾，在未來如果你的UE5(UE4)專案需要使用到AirSim，將此資料夾複製到該專案裡面，該專案就能使用AirSim Plugin

![](https://github.com/Kura0913/Blog-image/blob/main/InstallAirSimPlugin/AirSimInstall_7.png?raw=true)

接下來要來確認 AirSim 的環境是可以正常運作的，在與"Plugins"資料夾同一個目錄下，點選"Environments"，裡面有一個預設專案"Blocks"，內部已經安裝好了AirSim Plugin

![](https://github.com/Kura0913/Blog-image/blob/main/InstallAirSimPlugin/AirSimInstall_8.png?raw=true)

打開"Block"專案，查看是否有一個名叫"Blocks.sln"的檔案，如果沒有，可以對"Blocks.uproject"按右鍵，選擇"Generate Visual Studio project files"來生成"Blocks.sln"

![](https://github.com/Kura0913/Blog-image/blob/main/InstallAirSimPlugin/AirSimInstall_9.png?raw=true)

接下來，打開"Blocks.sln"，將偵錯模式改成"Development Editor"，再按執行

![](https://github.com/Kura0913/Blog-image/blob/main/InstallAirSimPlugin/AirSimInstall_10.png?raw=true)

你有可能會出現類似以下敘述的錯誤

![](https://github.com/Kura0913/Blog-image/blob/main/InstallAirSimPlugin/issue1.png?raw=true)

代表Visual Studio組件版本無法對上，通常會發生在已經使用一段時間的Visual Studio環境，最快的辦法就是整個Visual Studio重新安裝，可以使用匯出組件功能來保留你的環境

執行成功後，便會開啟專案

![](https://github.com/Kura0913/Blog-image/blob/main/InstallAirSimPlugin/AirSimInstall_11.png?raw=true)

進一步確定是否完整安裝，按下"Alt + p"或是綠色播放鍵，會顯示以下畫面：

![](https://github.com/Kura0913/Blog-image/blob/main/InstallAirSimPlugin/AirSimInstall_12.png?raw=true)

這邊是在詢問要使用哪種交通工具進行模擬，AirSim內建提供了 Car 以及 Multirotor 可以選擇，點選"Yes"會使用 Car 來模擬，點選"No"會使用 Multirotor 來模擬，兩個都選選看是否能正常運作，如果能正常執行沒有報錯的話，代表安裝成功啦~

Multirotor模擬畫面

![](https://github.com/Kura0913/Blog-image/blob/main/InstallAirSimPlugin/AirSimInstall_13.png?raw=true)

Car模擬畫面

![](https://github.com/Kura0913/Blog-image/blob/main/InstallAirSimPlugin/AirSimInstall_14.png?raw=true)
