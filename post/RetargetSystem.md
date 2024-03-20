---
title: UE5 Retarget System
date: 2023-09-23 13:59:48
tags: [Unreal Engine, Retarget System]
categories:
- [Unreal Engine, Retarget System]
keywords: Unreal Engine,UE5,Unreal Engine 5,Retarget,Retarget system,Retarget skeleton
---
當你製作一個遊戲，覺得預設的人物太單調時，肯定會想要幫他換上新的模型，但是匯入新模型會面臨到的問題是：兩個骨架的動畫是無法共用的，而在UE4，只能透過匯入骨架結構相近的模型，用相對"碰運氣"的方式去做骨架的Retarget，而UE5提供了新的Retarget System，可以細部調整骨架對接的方式，讓兩個骨架之間的動畫可以互相通用
<!-- more -->
### 匯入模型
網路上免費的模型資源少之又少，但好險有Adobe的[Mixamo](https://www.mixamo.com/#/?page=1&type=Character)，提供了許多免費的模型與動畫
這邊先下載好一個模型及動畫後，開啟專案，到達要匯入的資料夾後，點選左上角的"import"，將要匯入的FBX檔全部選取

![](https://github.com/Kura0913/Blog-image/blob/main/RetargetSystem/1.png?raw=true)

![](https://github.com/Kura0913/Blog-image/blob/main/RetargetSystem/2.png?raw=true)

接下來會跳出以下視窗，請注意**一定要勾選"Import Animation"動畫才會匯入**，確認完之後選擇"Import All"

![](https://github.com/Kura0913/Blog-image/blob/main/RetargetSystem/3.png?raw=true)

Import後可能會跳以下Log訊息，他的意思是找不到合適的骨架，原因是因為你匯入的骨架一開始並沒有在你的專案中，導致動畫無法有對應的骨架匯入，因此到整個匯入流程結束後，成功匯入的只有骨架而沒有動畫

![](https://github.com/Kura0913/Blog-image/blob/main/RetargetSystem/4.png?raw=true)

而log中有提到已經建立骨架請重新匯入，這次匯入請在Skeleton選擇剛剛匯入的新骨架，勾選"Import Animation"，再次匯入

![](https://github.com/Kura0913/Blog-image/blob/main/RetargetSystem/5.png?raw=true)

匯入完成後就會出現很多動畫檔了，將全部的檔案儲存

![](https://github.com/Kura0913/Blog-image/blob/main/RetargetSystem/6.png?raw=true)

### Retarget System
接下來就要使用Retarget System將兩個不同的骨架動畫做對接
#### Set IK Rig

##### ★
資料夾空白處右鍵：Animation -> IK Rig -> IK Rig，建立完檔案後打開

![](https://github.com/Kura0913/Blog-image/blob/main/RetargetSystem/7.png?raw=true)

右邊欄有個Preview Skeleton，選擇想要對接的骨架

![](https://github.com/Kura0913/Blog-image/blob/main/RetargetSystem/8.png?raw=true)
![](https://github.com/Kura0913/Blog-image/blob/main/RetargetSystem/9.png?raw=true)

選擇完成後，要先設定骨架的Root，在左邊將要作為Root的骨格點右鍵，"Set Retarget Root"

![](https://github.com/Kura0913/Blog-image/blob/main/RetargetSystem/10.png?raw=true)


右邊欄下面有個"IK Retargeting"的分頁，點開後選擇"Add New Chain"

![](https://github.com/Kura0913/Blog-image/blob/main/RetargetSystem/11.png?raw=true)

這時會有以下介面，Chain Name就是這個部位的名稱，Start Bone跟End Bone就是這個部位的開始骨骼及結束骨骼，而Retarget System的對接方式，就是將A骨架中的部位名稱對應到B骨架的部位名稱來執行動畫，因此骨架中的部位切分的越精細，呈現出來的動畫違和感就越少

![](https://github.com/Kura0913/Blog-image/blob/main/RetargetSystem/12.png?raw=true)

這邊就依照自己的規劃去設定部位

![](https://github.com/Kura0913/Blog-image/blob/main/RetargetSystem/13.png?raw=true)

設定完成後儲存，接下來到另一個要對接的骨架，從★開始做一樣的動作，請注意**作為Root的骨格部位請選擇相同部位，骨格名稱不一定會相同，請透過視覺判斷**，而部位的名稱建議設定一樣，到時候在對接的時候才比較好設定

#### IK Retargeter
資料夾空白處右鍵：Animation -> IK Rig -> IK Retargeter，建立完檔案後打開

![](https://github.com/Kura0913/Blog-image/blob/main/RetargetSystem/14.png?raw=true)

右邊可以選擇Source IKRig跟Target IKRig(途中的A和B)，這邊設定時要搞清楚對象，這邊設定的意思是**要將A骨架的動畫檔案輸出成B骨架可使用的動畫檔案**

![](https://github.com/Kura0913/Blog-image/blob/main/RetargetSystem/15.png?raw=true)

右下方有個Chain Mapping的分頁，點開後就開始將對應的部位設定好，如圖所示

![](https://github.com/Kura0913/Blog-image/blob/main/RetargetSystem/16.png?raw=true)

設定完成後存檔，然後點選右下方的Asset Browser分頁，這邊會列出所有A骨架的動畫，選擇想要給B骨架使用的動畫後(可複選)，選擇"Export Select Animations"，選擇要輸出的目標資料夾後，按"Export"

![](https://github.com/Kura0913/Blog-image/blob/main/RetargetSystem/17.png?raw=true)
![](https://github.com/Kura0913/Blog-image/blob/main/RetargetSystem/18.png?raw=true)

在目標資料夾會有新的動畫檔案，這些動畫檔按就是B骨架能夠使用的檔案，透過以上方式，就能讓不同的骨架適用其他骨架的動畫了


文章內容參考自 Youtube:[Animation Retargeting In UE5 | New IK Rig Retargeting System (Tutorial)](https://www.youtube.com/watch?v=N7WdyAeeDrw)