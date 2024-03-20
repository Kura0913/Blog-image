---
title: Airsim更換Actor
date: 2023-07-17 20:09:40
tags: [Unreal Engine, Airsim]
categories: [Unreal Engine, Airsim更換Actor]
keywords: Unreal Engine,UE4,UE5,Unreal Engine 4,Unreal Engine 5,AirSim,airsim,Airsim,AirSim
---
使用過AirSim之後，你是否感受到它的強大了呢?AirSim可以提供相當多元的輔助，在深度學習、機器學習方面尤其明顯。AirSim提供的功能固然好用，但是有時還是會有需要自己新增一些功能到Actor上面或是更換成自己設計的Actor，但是卻找不到從哪邊下手更改，因此本篇將會教你如何將自己設計的Actor與AirSim連接，以及更改AirSim提供的Actor，教學開始~

<!-- more -->

**以下教學使用UE5作為示範**

### 前置準備
很簡單，請先準備好一個已經安裝好AirSim Plugin的專案，還沒安裝的朋友，可以參考[此篇](https://kura0913.github.io/2023/07/08/InstallAirSimPlugin/)，這邊就不贅述

### 找到Plugin資料夾


首先，要找到名為Plugin的資料夾，預設情況下是不會出現的，先打開Content Browser，右上角有個"Settings"，點開後會看到"Show Plugin Content"選項

![](https://github.com/Kura0913/Blog-image/blob/main/AirsimChangeCharacter/findPlugin_1.png?raw=true)

把他勾起來就可以看到"Plugin"的資料夾囉

![](https://github.com/Kura0913/Blog-image/blob/main/AirsimChangeCharacter/findPlugin_2.png?raw=true)

### 為AirSim的Actor增加功能

打開"Plugin/AirSim Content/Blueprints"，這邊會看到一些Blueprint檔案，這些就是AirSim在模擬的時候會調用的檔案，我們用"BP_FlyingPawn"示範，對要編輯的檔案點右鍵，"Duplicate"

![](https://github.com/Kura0913/Blog-image/blob/main/AirsimChangeCharacter/EditAirSimActor_1.png?raw=true)

重新命名完之後按存檔，打開剛剛複製的檔案，在這邊就可以加上自己想要的功能囉!

![](https://github.com/Kura0913/Blog-image/blob/main/AirsimChangeCharacter/EditAirSimActor_2.png?raw=true)


或許你會疑問，為甚麼要特別複製?不能直接對原本的檔案做修改嗎?
**答案是可以的**，但為了確保在自製的過程中不會出差錯，這邊建議還是預留一份原檔在專案內，不然到時候出問題無法復原又要到別的地方翻檔案來補，顯得更麻煩

### 更換AirSim的Actor

設計好自己專屬的Actor之後，接下來就是用AirSim來控制它，這邊就要去修改AirSim的設定檔，預設路徑為:C:\Users\user_name\Documents\AirSim，裡面會有一個"setting.json"的檔案，打開它，內容預設應該是如下:

```
{
  "SeeDocsAt": "https://github.com/Microsoft/AirSim/blob/master/docs/settings.md",
  "SettingsVersion": 1.2,
  "SimMode": ""
}

```

我們可以在這個檔案裏面加入設定去更改AirSim執行時要使用的AirSim載具、相機大小、物理特性等等，以及本篇的核心，**更換成自製的載具**

我們需要將設定改成：
```
{
  "SeeDocsAt": "https://github.com/Microsoft/AirSim/blob/master/docs/settings.md",
  "SettingsVersion": 1.2,
  "SimMode": "Multirotor",
  "PawnPaths": {
    "BareboneCar": {"PawnBP": "Class'/AirSim/VehicleAdv/Vehicle/VehicleAdvPawn.VehicleAdvPawn_C'"},
    "DefaultCar": {"PawnBP": "Class'/AirSim/VehicleAdv/SUV/SuvCarPawn.SuvCarPawn_C'"},
    "DefaultQuadrotor": {"PawnBP": "Class'/AirSim/Blueprints/BP_FlyingPawn.BP_FlyingPawn_C'"},
    "DefaultComputerVision": {"PawnBP": "Class'/AirSim/Blueprints/BP_ComputerVisionPawn.BP_ComputerVisionPawn_C'"}
  }
}
```

加上之後，接下來我們要知道你自己設計的Actor的相對路徑，你可以將屬標只在你的Actor上，就會看到它的Path

![](https://github.com/Kura0913/Blog-image/blob/main/AirsimChangeCharacter/ChangeActor_1.png?raw=true)


在更改"setting.json"的時候，我們將SimMode改成"Multirotor"，意思是將模擬的載具設定成四軸無人機(Quadrotor)，因此我們要將對應的PawnPaths換掉，這邊我要換成的物件路徑是:

/AirSim/Blueprints/BP_DroneCharacter.<font color=#FF0000>BP_DroneCharacter_C</font>

其中紅色的部分是在生成的時候，你想讓該物件在地圖上叫甚麼名稱，就改在這邊

將上面的路徑覆蓋掉"DefaultQuadrotor"的路徑變成：
```
{
  "SeeDocsAt": "https://github.com/Microsoft/AirSim/blob/master/docs/settings.md",
  "SettingsVersion": 1.2,
  "SimMode": "Multirotor",
  "PawnPaths": {
    "BareboneCar": {"PawnBP": "Class'/AirSim/VehicleAdv/Vehicle/VehicleAdvPawn.VehicleAdvPawn_C'"},
    "DefaultCar": {"PawnBP": "Class'/AirSim/VehicleAdv/SUV/SuvCarPawn.SuvCarPawn_C'"},
    "DefaultQuadrotor": {"PawnBP": "Class'/AirSim/Blueprints/BP_DroneCharacter.BP_DroneCharacter_C'"},
    "DefaultComputerVision": {"PawnBP": "Class'/AirSim/Blueprints/BP_ComputerVisionPawn.BP_ComputerVisionPawn_C'"}
  }
}
```

改完之後按存檔，接著回到專案直接按"alt+p"開始模擬，模擬時如果想顯示滑鼠可以按"shift+F1"，看到右邊的Item Label，可以看到我們正在操作的是剛剛設定的物件

![](https://github.com/Kura0913/Blog-image/blob/main/AirsimChangeCharacter/ChangeActor_2.png?raw=true)

你也可以點擊該物件右邊的藍字，前往該物件的Blueprint，進一步確認是否為你設定的物件

![](https://github.com/Kura0913/Blog-image/blob/main/AirsimChangeCharacter/ChangeActor_3.png?raw=true)

以上就是這次的教學，如果你對於"setting.json"內部還有哪些設定感興趣，可以參考[此連結](https://github.com/microsoft/AirSim/blob/main/docs/settings.md)

