---
layout: post
title: 'C# 透過 CSC.EXE 批次檔編譯原始碼成 DLL'
author: 'James Peng'
tags: ['C#']
---

## 初次的 Servlet ##

~~~text
@if not exist bin\ (@echo ※注意※bin資料夾不存在，自動建立)
@if not exist bin\ (@mkdir bin)
@if exist source\ (@C:\WINDOWS\Microsoft.NET\Framework\v2.0.50727\csc.exe /t:library /r:bin\MySql.Data.dll /out:bin\ServiceSample.dll /recurse:source\*.cs)
@if not exist source\ (@echo ※注意※找不到原始碼資料夾)
@if not exist source\ (@pause)
@if errorlevel 1 (@pause)
~~~


----------


編譯指令

~~~text
csc.exe /t:library /out:YourProject.dll /recurse:*.cs
~~~

使用 /recurse 可建立資料夾，方便整理 .cs 檔


----------

參考：

- Javaworld@TW http://www.javaworld.com.tw/
- 良葛格學習筆記 http://caterpillar.onlyfun.net/Gossip/index.html > JSP/Servlet
