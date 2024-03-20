---
title: Unreal Engine 調整Material的顏色
date: 2023-07-11 20:45:49
tags: [Unreal Engine]
categories:
- [Unreal Engine, Material]
keywords: Unreal Engine Material,調整Material的顏色,Material 顏色,Unreal Material 顏色,Unreal 顏色,Material
---
### 沒有適合的Material?
在建立Level的時候，會調用到很多Static Mesh、Actor來裝飾地圖，而在建立地圖的途中，可能會遇到

疑?怎麼沒有我要的模型?或是模型是對了，但是顏色卻不是你想要的，這時可以選擇重新做一個Texture，優點當然是可以為物件做一個全新的顏色設計，而且精細度可以依個人需要去做調整。

但是，如果沒有3D建模的專業的人怎麼辦?(欸嘿!就是我!)這時候就適合使用接下來要教學的方法，這個方法只會調整Texture的顏色，本來設計好的紋路是不會去動到的，那麼話不多說，開始本篇的教學~

<!-- more -->

### 基於原本的Texture，調整Material顏色教學

首先，我們先找到想要調整的Material，這邊以圖中的"MI_jcGrdLineA"做示範，點擊兩下打開

![](https://github.com/Kura0913/Blog-image/blob/main/UnrealEngineMaterialColor/MaterialColor1.png?raw=true)

如果打開是以下畫面的話就參考接下來的步驟，如果是Blueprint畫面，則可以直接跳至★

![](https://github.com/Kura0913/Blog-image/blob/main/UnrealEngineMaterialColor/MaterialColor2.png?raw=true)

接下來，右邊欄有一個"BaceColor"，是這個Material檔案套用的Texture，點擊檔名下方的"前往資料夾"，就會跳到存放Texture的地方

![](https://github.com/Kura0913/Blog-image/blob/main/UnrealEngineMaterialColor/MaterialColor3.png?raw=true)

這邊先把Texture的路徑記下來，然後回到"MI_jcGrdLineA"，右邊欄有一個"Parent"，接下來自己製作Material的時候，要基於這個"Parent"的設計結構，最後顯示出來的紋路才會跟原本的一樣，因此我們一樣點選檔名下方的"前往資料夾"，並打開該檔案，應該會看到Blueprint畫面，如果不是，就基於上述方法繼續往上找"Parent"，直到打開的頁面為Blueprint為止，這邊的"Parent"的檔名為"MM_opacity"


#### ★
打開後，整個Blueprint就是模板，等等要基於此模板來設計，全選之後先放著

![](https://github.com/Kura0913/Blog-image/blob/main/UnrealEngineMaterialColor/MaterialColor4.png?raw=true)

到要存放新的Material的資料夾點擊右鍵，選擇"Material"

![](https://github.com/Kura0913/Blog-image/blob/main/UnrealEngineMaterialColor/MaterialColor5.png?raw=true)

取好名字後打開，會看到以下畫面

![](https://github.com/Kura0913/Blog-image/blob/main/UnrealEngineMaterialColor/MaterialColor6.png?raw=true)

回到"MM_opacity"(your Parent file)，把剛剛框起來部分複製，然後貼到剛剛自己建立的Material貼上，貼上後你會發現線全部斷掉了，這是正常的，請依據"MM_opacity"(your Parent file)的設計連上

![](https://github.com/Kura0913/Blog-image/blob/main/UnrealEngineMaterialColor/MaterialColor7.png?raw=true)

按住鍵盤第一排的3，在空白處點左鍵，對出現的方塊點右鍵，選擇圖中紅色框框中的選項，並為他取一個你認得出來的名字，這邊取名為"Tint_colour"

![](https://github.com/Kura0913/Blog-image/blob/main/UnrealEngineMaterialColor/MaterialColor8.png?raw=true)

按住鍵盤第一排的1，在空白處點左鍵，對出現的方塊點右鍵，選擇圖中紅色框框中的選項，並為他取一個你認得出來的名字，這邊取名為"Tint_Intensity"

![](https://github.com/Kura0913/Blog-image/blob/main/UnrealEngineMaterialColor/MaterialColor9.png?raw=true)

在空白處點右鍵，搜尋"Multiply"，叫出方塊，在空白處再點一下右鍵，搜尋"Blend_Overlay"，同樣叫出方塊，然後將線連接成下圖

![](https://github.com/Kura0913/Blog-image/blob/main/UnrealEngineMaterialColor/MaterialColor10.png?raw=true)

如果連接會用到"Opacity Mask"節點，則點選棕色方塊，到左邊欄找到"Blend Mode"選項，調成"Mask"來啟用節點

![](https://github.com/Kura0913/Blog-image/blob/main/UnrealEngineMaterialColor/MaterialColor11.png?raw=true)

點擊名為"BaceColor"的方塊，這時左下角可以找到一個可以選擇Texture的地方，將前面記下的Texture匯入，匯入成功後，紅色框框處都會變成你所選的Texture，完成後就可以存檔了

![](https://github.com/Kura0913/Blog-image/blob/main/UnrealEngineMaterialColor/MaterialColor12.png?raw=true)

回到自己建立的Material的資料夾，對自己建立的Material按右鍵，選擇紅色框框的選項，點選後會建立一個新的Material，取好名字後打開

![](https://github.com/Kura0913/Blog-image/blob/main/UnrealEngineMaterialColor/MaterialColor13.png?raw=true)

將右欄的"Parent"改為前面自己建立的Material

![](https://github.com/Kura0913/Blog-image/blob/main/UnrealEngineMaterialColor/MaterialColor14.png?raw=true)

此時右欄會出現剛剛我們做的設定，將他們打勾就可以啟用了

![](https://github.com/Kura0913/Blog-image/blob/main/UnrealEngineMaterialColor/MaterialColor15.png?raw=true)

這邊就示範幾種顏色

![](https://github.com/Kura0913/Blog-image/blob/main/UnrealEngineMaterialColor/MaterialColor16.png?raw=true)
![](https://github.com/Kura0913/Blog-image/blob/main/UnrealEngineMaterialColor/MaterialColor17.png?raw=true)
![](https://github.com/Kura0913/Blog-image/blob/main/UnrealEngineMaterialColor/MaterialColor18.png?raw=true)

稍微玩過之後就可以發現，"Tint_colour"可以用來做初步的選擇顏色，"Tint_Intensity"可以做後續的亮度調整，接下來就套用到原先的物件上，挑出自己滿意的顏色吧~

以上參考自:[https://www.youtube.com/watch?v=M1olxyt7Zw8](https://www.youtube.com/watch?v=M1olxyt7Zw8)