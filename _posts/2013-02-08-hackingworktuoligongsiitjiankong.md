---
layout: post
title: '[Hacking Work] 脫離公司IT監控'
author: 'James Peng'
tags: ['Hacking Work','知行合一']
---

![e-spying](http://lh3.ggpht.com/-QOcDjgvn2VQ/URyixcaxF1I/AAAAAAAAR3c/RRuJxG4rhsY/e-spying%25255B4%25255D.jpg?imgmax=800 "e-spying")

> **公司規則1：IT 監控程式 會偷看員工電腦安裝什麼軟體和資料。**
>
> [![image](http://lh5.ggpht.com/-21eEN9n9BlI/URSUAGh0SLI/AAAAAAAAQIQ/7OVyeMywLc8/image_thumb%25255B65%25255D.png?imgmax=800 "image")](http://lh4.ggpht.com/-rMdesQEBcC4/URST-7WAGeI/AAAAAAAAQII/DkC8qqrTR6k/s1600-h/image%25255B116%25255D.png)[![image](http://lh6.ggpht.com/-b1Ymhi_SFyw/URSUBg-X8AI/AAAAAAAAQIg/aptgfNAEYiM/image_thumb%25255B68%25255D.png?imgmax=800 "image")](http://lh5.ggpht.com/-pCwApBqNI7A/URSUA0hJPlI/AAAAAAAAQIY/hRXMhvgLGqI/s1600-h/image%25255B121%25255D.png)  

被掌握數位足跡（而且被highlight了）

> **公司規則2：Skype傳送檔案被鎖。**
>
> [![image](http://lh6.ggpht.com/-1qX4g8PcQgc/URSPc4hyirI/AAAAAAAAQCc/m2ORruJFOOA/image_thumb%25255B7%25255D.png?imgmax=800 "image")](http://lh3.ggpht.com/-_sC3rkkxILo/URSPbxrneII/AAAAAAAAQCU/Ih3KUdxVg0M/s1600-h/image%25255B16%25255D.png)

當蝙蝠俠開著蝙蝠車出門執行任務——你有看過他停下來等紅燈變綠燈嗎？

如果必須遵守一堆蠢規定，怎麼可能樂在工作嘛！

* * * * *

**Hacking** **步驟1：找出公司「IT監控程式」**

透過Process Explorer，展開explorer.exe裡找。

[![image](http://lh5.ggpht.com/--pCHWSW1ATA/URSPeXJDC-I/AAAAAAAAQCs/kg6pfiTdxMw/image_thumb%25255B15%25255D.png?imgmax=800 "image")](http://lh6.ggpht.com/-r7VOIdlaO2U/URSPdu4b1EI/AAAAAAAAQCk/5tZ2e8EDo20/s1600-h/image%25255B30%25255D.png)

 

* * * * *

**Hacking** **步驟2：砍掉Process**

透過「cmd命令提示字元」執行

> Taskkill /IM **監控程式.exe** /F

成功: 處理程序 "ITAgent.exe" (PID 4620) 已經終止了。

> [![image](http://lh3.ggpht.com/-qHi2JLGHlHA/URSPgBmSkXI/AAAAAAAAQC8/2dc3kdZgvf0/image_thumb%25255B12%25255D.png?imgmax=800 "image")](http://lh3.ggpht.com/-0OR3TEpaIqs/URSPfcLFOSI/AAAAAAAAQC0/15eGNMQyxoI/s1600-h/image%25255B25%25255D.png)

注意：使用者必須有Administrator權限。

* * * * *

**Hacking** **步驟3：Skype解開傳送檔案**

打開登錄編輯程式 regedit

[![image](http://lh5.ggpht.com/-k-UPi9dACDE/URSPiDaU6bI/AAAAAAAAQDM/hxzYS-byvh4/image_thumb%25255B26%25255D.png?imgmax=800 "image")](http://lh3.ggpht.com/-XvxukK34Z2Y/URSPgnho36I/AAAAAAAAQDE/Iy31tMsQXfA/s1600-h/image%25255B49%25255D.png)

Windows的系統登錄機碼中找到[HKEY\_LOCAL\_
MACHINE\\SOFTWARE\\Policies\\Skype\\Phone]

[![image](http://lh4.ggpht.com/-TLdGQQnhuRM/URSPj49o0LI/AAAAAAAAQDc/l5hpy44DzC4/image_thumb%25255B28%25255D.png?imgmax=800 "image")](http://lh4.ggpht.com/-kk2tWWMjC8k/URSPi7Yo2GI/AAAAAAAAQDU/ApxpSesOHBo/s1600-h/image%25255B53%25255D.png)

"DisableFileTransfer" =dword:00000001值。 改0

[![image](http://lh5.ggpht.com/-m-YU0JESyW8/URSPlbkDGzI/AAAAAAAAQDs/sVb7F9Z0CGw/image_thumb%25255B31%25255D.png?imgmax=800 "image")](http://lh3.ggpht.com/-aB6uo9AUxd8/URSPkr2cLeI/AAAAAAAAQDk/oGm5L_o3JyU/s1600-h/image%25255B58%25255D.png)

[![image](http://lh5.ggpht.com/-sJLYXx5DF3w/URSPm5ip8sI/AAAAAAAAQD8/9hEqTpj4bSA/image_thumb%25255B34%25255D.png?imgmax=800 "image")](http://lh5.ggpht.com/-SJV7GhaO2F8/URSPmA5QF4I/AAAAAAAAQD0/qTCt3r1NIDs/s1600-h/image%25255B65%25255D.png)

[![image](http://lh6.ggpht.com/-S6-OXCK4W8Q/URSPoOcZiRI/AAAAAAAAQEM/Hp6dADSYkkA/image_thumb%25255B37%25255D.png?imgmax=800 "image")](http://lh6.ggpht.com/-_EdcvQXaT_g/URSPnYm4U8I/AAAAAAAAQEE/Uvw-dYpC8VU/s1600-h/image%25255B70%25255D.png)

把修改結果「匯出」因為邪惡的IT監控程式，每次開機都會改回來。

[![image](http://lh3.ggpht.com/-EbL-r9odY-8/URSPpHFWf2I/AAAAAAAAQEc/nGmSOwrnBdU/image_thumb%25255B40%25255D.png?imgmax=800 "image")](http://lh4.ggpht.com/-NtavlEQndmw/URSPopjZdJI/AAAAAAAAQEU/mGLWHe0AhAo/s1600-h/image%25255B75%25255D.png)

儲存檔名 UnlockSkype.reg

[![image](http://lh5.ggpht.com/-8rgeCKjOG0E/URSPqwnJkXI/AAAAAAAAQEs/2ZERC6RmjD0/image_thumb%25255B42%25255D.png?imgmax=800 "image")](http://lh5.ggpht.com/-ayWgAkvghyo/URSPqLtsQZI/AAAAAAAAQEk/pVFeBdFAKnE/s1600-h/image%25255B79%25255D.png)

如果你已經開著skype 記得關掉重開才會生效。

* * * * *

**Hacking** **步驟4：每次開機時自動砍IT監控程式+解鎖skype**

建立批次檔 WorkHacking.bat，內容為：

> Taskkill /IM ITAgent.exe /F  
> Taskkill /IM ITCurusr.exe /F  
> UnlockSkype.reg

[![image](http://lh6.ggpht.com/-SketduKwYAA/URSPsOqpNzI/AAAAAAAAQE8/gy-H9PSc8g0/image_thumb%25255B45%25255D.png?imgmax=800 "image")](http://lh5.ggpht.com/-wUYGVzXMqJc/URSPrbrDlsI/AAAAAAAAQE0/fiDCZJxxwCk/s1600-h/image%25255B84%25255D.png)

把批次檔WorkHacking.bat 建立一個「捷徑」

[![image](http://lh3.ggpht.com/-qWhT5FaaUBA/URSPthUIGQI/AAAAAAAAQFM/TQ660Nl6HxE/image_thumb%25255B58%25255D.png?imgmax=800 "image")](http://lh3.ggpht.com/-auyy8BrIjLk/URSPs_rPJ_I/AAAAAAAAQFE/AXJBJ1LJMqc/s1600-h/image%25255B105%25255D.png)

[![image](http://lh5.ggpht.com/-OCWflmKcm2k/URSPus0GSAI/AAAAAAAAQFc/tYvwV2Z7NP4/image_thumb%25255B54%25255D.png?imgmax=800 "image")](http://lh6.ggpht.com/-57B-qKRE-o0/URSPuGb9biI/AAAAAAAAQFU/cEii62N7FOo/s1600-h/image%25255B99%25255D.png)

放到「啟用」資料夾裡。

[![image](http://lh5.ggpht.com/-zzaWXqjkoQM/URSPwOpYadI/AAAAAAAAQFs/kKrI7xJ30Sc/image_thumb%25255B49%25255D.png?imgmax=800 "image")](http://lh3.ggpht.com/-o5OF-6LIZy4/URSPvRRRFCI/AAAAAAAAQFk/CEr8HZQKV1w/s1600-h/image%25255B90%25255D.png)

[![image](http://lh6.ggpht.com/-EoArFl3KMHI/URSPxnvLodI/AAAAAAAAQF8/xN76bXMnF8M/image_thumb%25255B57%25255D.png?imgmax=800 "image")](http://lh3.ggpht.com/-ra0VZBJBmoA/URSPxETi3NI/AAAAAAAAQF0/X_P2FC9NlRs/s1600-h/image%25255B104%25255D.png)

ok完成！重開機看看～

* * * * *

結論：

1.  掌握數位足跡(digital footprint)將掌握全局。
2.  打算「知行合一」。
3.  同事用：[按此下載](https://skydrive.live.com/redir?resid=59D7E35D1B1C90A2!108)。

 

* * * * *

參考：

-    [夠「駭」才能成為職場A咖](http://www.jhpeng.com/2013/01/a.html)
-   <http://forum.thewindowsclub.com/windows-tips-tutorials-articles/29463-kill-processes-using-command-prompt-windows-7-a.html>
-   <http://briian.com/?p=6574>

