---
title: Unreal Engine：GPU Lightmass 全域照明
date: 2023-09-21 20:58:45
tags: [Unreal Engine]
categories: 
- [Unreal Engine, GPU Lightmass]
keywords: Unreal Engine,UE4,UE5,Unreal Engine 4,Unreal Engine 5,GPU,GPU Lightmass
---
GPU Lightmass插件是一個 light-baking的解決方案，可預先計算移動性設定為「固定」或「靜態」的燈光的複雜光影，並將該資料儲存在應用於場景幾何體的產生的光照貼圖紋理中。GPU Lightmass 顯著減少了計算、建構和產生複雜場景的照明資料所需的時間，其速度與使用 Swarm 和基於 CPU 的 Lightmass 的分散式建構相當，是一個相當利於開發的工具，接下來便開始GPU Lightmass的安裝教學。
<!-- more -->

### 啟用插件
打開想要增加此功能的專案，點選 Edit -> Plugin 

![](https://github.com/Kura0913/Blog-image/blob/main/GPULightmass/1.png?raw=true)

在搜尋欄打GPU，找到GPU Lightmass，左邊勾選啟用插件，接下來會要求重啟專案，依照指示重啟

![](https://github.com/Kura0913/Blog-image/blob/main/GPULightmass/2.png?raw=true)

重啟過後插件便已經安裝完成

### 專案設定

接下來必須做一些設定讓GPU Lightmass可以順利啟用，點選 Edit -> Project settings

![](https://github.com/Kura0913/Blog-image/blob/main/GPULightmass/3.png?raw=true)

Engine -> Rendering -> Hardware Ray Tracing，依照圖中的設定勾選 

![](https://github.com/Kura0913/Blog-image/blob/main/GPULightmass/4.png?raw=true)

Engine -> Rendering -> Virtual Texture，依照圖中的設定勾選

![](https://github.com/Kura0913/Blog-image/blob/main/GPULightmass/5.png?raw=true)

完成設定後，依照指示重啟專案

### 更改系統配置
GPU執行命令時間過長時，Windows會認為顯示卡已經崩潰，並會重置驅動程序，導致引擎關閉。為了避免此情況，透過變更 Windows 登錄中的逾時偵測和復原 (TDR) 時間，可以增加 Windows 偵測到 GPU 逾時所需的時間。按Win + R 開啟執行，輸入"regedit" 開啟登錄編輯程式，導覽至類別:

```
Computer\HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\GraphicsDrivers
```


查看是否有名為"TdrDelay"的變數，沒有則空白處點擊右鍵，新增 -> DWORD(32-位元)值，將名稱命名為:TdrDelay

![](https://github.com/Kura0913/Blog-image/blob/main/GPULightmass/6.png?raw=true)

建立完成後點擊兩下開啟"TdrDelay"，選擇10進位，數值資料輸入60(可自行調整)，完成後按確定

![](https://github.com/Kura0913/Blog-image/blob/main/GPULightmass/7.png?raw=true)

這樣就能防止Unreal Engine在使用該插件時，因為執行的時間過長而導致關閉，若因為專案地圖過大，建置時間拉長還是發生了關閉的狀況，把TdrDelay的時間拉長即可


### 使用 GPU Lightmass

完成設定後就能正常使用GPU Lightmass，打開專案，Build -> GPU Lightmass

![](https://github.com/Kura0913/Blog-image/blob/main/GPULightmass/8.png?raw=true)

點選左上方的Build Lighting就會開始建置光影，而下方的設定則可以參考[官方文件](https://docs.unrealengine.com/4.27/en-US/RenderingAndGraphics/RayTracing/MovieRenderQueue/#systemconfiguration_optionalbutrecommended_)來依據需求做調整

![](https://github.com/Kura0913/Blog-image/blob/main/GPULightmass/9.png?raw=true)

