---
layout: post
title: 'Remote Debug 設定'
author: 'James Peng'
tags: ['Visual Studio']
---

# Remote Debug 設定 #

裝有Visual C++ 6.0/Visual Studio 2010者，稱Host電腦.

被Remote Debug者，稱Remote電腦.


----------


## 前置作業 Step 1. ##

將Remote電腦新增/修改為有密碼之使用者帳戶. (遠端連線需設密碼)

![](http://i.imgur.com/VDSgD3J.png)



----------


##  前置作業 Step 2. ##

連接Host、Remote電腦，即兩台電腦直接由網路線連接.


----------


## 前置作業 Step 3. ##

於Remote電腦C槽新增進行Debug工作的資料夾(ex. RemoteDbg)，並將其資料夾設置共用. 

操作 : 

右鍵/內容/共用/進階共用:共用此資料夾打勾，點選權限並開啟Everyone權限.

允許完全控制

變更


![](http://i.imgur.com/04fdhTt.png)


----------

## 前置作業 Step 4. ##

Host電腦於 我的電腦/網路 查看是否有看到Remote電腦所開啟的共用資料夾，若有請將其設置為網路磁碟機 (右鍵/連接網路磁碟機)，屆時會指定此磁碟機名稱(ex. Z:)，設置完成後可在【我的電腦】看到此磁碟機.

![](http://i.imgur.com/05SzlIT.png)

![](http://i.imgur.com/FhMSsHv.png)


----------

## 前置作業 Step 5. ##

將Remote Debug之程式執行檔(ex. forRemote.exe)放入此網路磁碟機，即放置於Remote電腦進行Debug工作的資料夾中.

----------


## 前置作業 Step 6-a. (Visual Studio 2010適用) ##


複製Visual Studio Remote Debugging Monitor 【註1】於Remote電腦，開啟並在Tools/Options中勾選 No Authentication (native only)與Allow any user to debug.

![](http://i.imgur.com/aoZuAEb.png)

註1：Visual Studio Remote Debugging monitor可在Host電腦找到，通常放置於 Program Files\Microsoft Visual Studio 10.0\Common7\IDE\Remote Debugger中，再依作業系統選擇適合的版本，例如win7 32bit則使用x86.



----------

## 前置作業 Step 6-b. (Visual C++ 6.0適用) ##

複製Visual C++ Debug Monitor等檔案【註2】於Remote電腦，開啟並在Settings/Target machine name 設定Host電腦之電腦名稱。於程式Debug前執行Connect即可.

![](http://i.imgur.com/US6dwkz.png)

註2：Visual C++ Debug Monitor等檔案，通常放置於

Program Files\Microsoft Visual Studio\Common\MSDev98\Bin中，複製六個檔案.

1. MSVCMON.EXE
2. DM.DLL
3. MSDIS110.DLL
4. msvcp60.DLL
5. psapi.DLL
6. TLN0T.DLL


----------

# Project Properties Setting #


## 【Visual Studio 2010】 Step 1. ##

位置：Project/Properties 

Configuration Properties/General/Output Directory設定為網路磁碟機(ex. Z:)

![](http://i.imgur.com/vH6Qfz0.png)


----------

## 【Visual Studio 2010】 Step 2. ##

位置：Configuration Properties/Debugging

選擇【Remote Windows Debugger】

參數設定如下:

- Remote Command 	設置程式執行`檔的絕對位置 (以Remote電腦的角度) 例如 C:\Remotedbg\forRemote.exe
- Working Directory 	設置Remote電腦之共用資料夾路徑 (以Remote電腦的角度) 例如 C:\Remotedbg
- Remote Server Name 	設置Remote電腦之【電腦名稱】 例如 B-PC
- Connection			點選Remote with no authentication (Native only)

![](http://i.imgur.com/Q9dDWIg.png)


----------


## 【Visual Studio 2010】 Step 3. ##

按F5 Start Debugging 。第一次建置專案Remote電腦可能會提示缺少某些DLL檔(ex. mfc100d.dll、msvcr100d.dll)，請在Host電腦system32資料夾中找，並複製到Remote電腦system32資料夾中；另外，Remote電腦的防火牆可能會影響debug的進行，若有提示再關掉即可.


----------

## 【Visual C++ 6.0】 Step 1. ##

位置：Build/Debugger Remote Connection
Connection項目選擇 Network(TCP/IP)，並在Settings/Target machine name欄位填入Remote電腦之電腦名稱.(ex. B-PC)

![](http://i.imgur.com/j64qx6U.png)


----------

## 【Visual C++ 6.0】 Step 2. ##

位置：Project/Settings/Debug

參數設定如下:

- Executable for debug session 		設置程式執行檔的位置 (以Host電腦角度)	例如 Z:\forRemote.exe
- Working directory					設置共用資料夾的位置 (以Remote電腦角度) 	例如 C:\Remotedbg
- Remote executable path and file name	設置程式執行檔的絕對位置 (以Remote電腦角度) 	例如 C:\Remotedbg\forRemote.exe
- Project/Settings/Link Output file name				設置Debug程式執行檔的位置 (以Host電腦角度)	例如 Z:\forRemote.exe

![](http://i.imgur.com/TVaZist.png)


----------

## 【Visual C++ 6.0】 Step 3. ##

按F5 Start Debugging 。第一次建置專案Remote電腦可能會提示缺少某些DLL檔(ex. mfc100d.dll、msvcr100d.dll)，請在Host電腦system32資料夾中找，並複製到Remote電腦system32資料夾中；另外，Remote電腦的防火牆可能會影響debug的進行，若有提示再關掉即可.


----------

## Remote Debug與DLL相關問題  ##

進行Remote Debug時，當程式有使用到其他額外的DLL檔，則需將此DLL放置於同一資料夾中(Remote電腦)；此外，若出現LoadLibrary抓不到此DLL檔的情況，可能是發生DLL Dependency問題，也就是使用此DLL檔亦需要其他DLL檔才能有效執行，而Remote電腦中並沒有這些DLL檔，導致程式無法正常執行.

解決方法：

可以利用Visual C++ 6.0 Tools中的【Dependency Walker】來查詢DLL檔間的相依性質，通常放置於Program Files\Microsoft Visual Studio\Common\Tools\DEPENDS.EXE 

操作：

將【Dependency Walker】放置於Remote電腦中，開啟欲使用的DLL檔來查詢相依性，其中有警告標示則代表缺少的相依DLL檔，可於Host電腦的system32資料夾中搜尋，並複製於Remote電腦的System32資料夾.

例如 程式需要使用MyRemote.dll，透過Dependency Walker載入，可以查詢缺少的相依DLL檔，在此例為MFC100.dll，如下圖所示：

![](http://i.imgur.com/qwDiyOM.png)