---
layout: post
title: 'ASUS X550V 改裝win7'
author: 'James Peng'
tags: ['asus','windows']
---

 

Windows 8
系統的電腦在開機時無法進入BIOS設定？如果您遇到這個問題，其實是Windows 8
為了加速電腦開機與關機的一個快速啟動技術，這快速啟動技術在我們每次讓電腦關機時，電腦其實沒有完全關機，而是在睡眠狀態，所以您會發現電腦每次在開機與關機時速度會快很多。但Windows
8
快速啟動功能，有時也會讓我們使用者要設定BIOS時會有一些麻煩，因為不能馬上在開機時進入BIOS設定，而是要讓電腦進入作業系統後在完全重新啟動一次，才能進入BIOS。

#### WIN8.1 怎麼進入 bios ：

[![image](http://lh4.ggpht.com/-IaPi1NgqVp0/U_QA5DObkAI/AAAAAAAAZLQ/Omet0U_TEd0/image_thumb%25255B12%25255D.png?imgmax=800 "image")](http://lh3.ggpht.com/-w53DafaH6tI/U_QA2pcEU-I/AAAAAAAAZLI/SVlG8Ig6WhA/s1600-h/image%25255B24%25255D.png)

[![image](http://lh3.ggpht.com/-DCAraQhCTsc/U_QA713va2I/AAAAAAAAZLg/XXdFx3XWtzI/image_thumb%25255B11%25255D.png?imgmax=800 "image")](http://lh3.ggpht.com/-vPd73WHmUDU/U_QA6T2N-RI/AAAAAAAAZLY/N9JPjgnvzgQ/s1600-h/image%25255B23%25255D.png)

 

[![image](http://lh5.ggpht.com/-e_215enEPoU/U_QA-_9xEQI/AAAAAAAAZLw/sIciKPFeWkM/image_thumb%25255B14%25255D.png?imgmax=800 "image")](http://lh3.ggpht.com/-EtthowPIdqw/U_QA9fFlYcI/AAAAAAAAZLo/-SJuoe0aSyY/s1600-h/image%25255B28%25255D.png)

 

[![image](http://lh5.ggpht.com/-zZ3kwOATTZY/U_QBBCrQ2rI/AAAAAAAAZMA/4ZjIf46uwgE/image_thumb%25255B16%25255D.png?imgmax=800 "image")](http://lh6.ggpht.com/-Zs5YltVMltg/U_QA_zZWD_I/AAAAAAAAZL4/DVOlYyNcmUA/s1600-h/image%25255B32%25255D.png)

[![image](http://lh3.ggpht.com/-eUru5bK32-4/U_QBDrHsI6I/AAAAAAAAZMQ/lN3ZKJRRe8M/image_thumb%25255B18%25255D.png?imgmax=800 "image")](http://lh3.ggpht.com/-Ka_hVLlx0V4/U_QBCLyGMII/AAAAAAAAZMI/4_CgT9hjte4/s1600-h/image%25255B36%25255D.png)

 

[![image](http://lh4.ggpht.com/-amPqRe__Wwk/U_QBHUbu4zI/AAAAAAAAZMg/Hgk8Df8Gk8c/image_thumb%25255B20%25255D.png?imgmax=800 "image")](http://lh3.ggpht.com/-ISMF-ywSaYc/U_QBFiHgieI/AAAAAAAAZMY/TSBpIAGY2q8/s1600-h/image%25255B40%25255D.png)

請先進入到BIOS (**開機時長按F2鍵不放**)。

 

#### WIN8.1 怎麼 光碟開機：

你這是預裝Win8的，UEFI啟動。  
UEFI不支持光碟機，UEFI的啟動Usb可以。  

如果是自己想重裝Win8以下的系統，要先改BIOS，再按esc啟動。

第1步驟：

切換到"Security"菜單將"Secure Boot Control"設定為Disabled，

[![image](http://lh4.ggpht.com/-Z1iFEyFY2y0/U_QBKgRBoqI/AAAAAAAAZMw/9HgD-K9XMZk/image_thumb%25255B2%25255D.png?imgmax=800 "image")](http://lh6.ggpht.com/-GXCteZ6b5Xw/U_QBIn0PInI/AAAAAAAAZMo/BNK2bK7i39o/s1600-h/image%25255B4%25255D.png)

 

[![image](http://lh4.ggpht.com/-0iZdGKyuCy8/U_QBOOrj2bI/AAAAAAAAZNA/pa5l3Bzpl1g/image_thumb%25255B4%25255D.png?imgmax=800 "image")](http://lh3.ggpht.com/-EXPjHwjILWY/U_QBL7pbrnI/AAAAAAAAZM4/A3UTszgEszs/s1600-h/image%25255B8%25255D.png)

 

第2步驟：

切換到"Boot"選單內將"Lunch CSM"設定為Enabled，如果"Lunch CSM"
這個不能撰擇不能設定為Enabled，請先將第一步驟改好後存檔離開，再進bios，就可以繼續改。

[![image](http://lh5.ggpht.com/-vgP-Zd2Z8Ao/U_QBREGsd_I/AAAAAAAAZNQ/hAKM0wKdOk4/image_thumb%25255B8%25255D.png?imgmax=800 "image")](http://lh3.ggpht.com/-ps_0I0YV67o/U_QBPl_8MHI/AAAAAAAAZNI/wCl79w56h3E/s1600-h/image%25255B16%25255D.png)

 

第3步驟：

最後按F10儲存設定並重新啟動。

[![image](http://lh5.ggpht.com/-j59cSmx1kHY/U_QBVap7D1I/AAAAAAAAZNg/gE_qlDkzlEE/image_thumb%25255B6%25255D.png?imgmax=800 "image")](http://lh6.ggpht.com/-iPSgVr-xbdA/U_QBTM51xzI/AAAAAAAAZNY/VF7ztWYouVQ/s1600-h/image%25255B12%25255D.png)

開機時長按ESC鍵

呼叫開機選單即可選擇光碟開機。

 

參考；

1.  <http://mypaper.pchome.com.tw/kisgccc/post/1325011489>
2.  <http://benyouhui.it168.com/thread-4744515-1-1.html>
3.  <http://www.pcsetting.com/windows/windows-8-wu-fa-jin-ru-biosshe-ding-jiao-xue>

