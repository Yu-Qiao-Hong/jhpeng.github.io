---
layout: post
title: 'C#中取得最後編譯時間'
author: 'James Peng'
tags: ['csharp']
---

C#獲取程序集的版本號：

~~~csharp
string ver = System.Reflection.Assembly.GetExecutingAssembly().GetName().Version.ToString();
~~~


 
在實際的軟件開發工作中，我們通常需要記錄某個工程的最後編譯時間，原來在C++中，我們有個__DATE__，__TIME__，__FILE__，__LINE__這樣的異性宏定義可以使用，但是在C#中，不能使用，但是可以用以下語句來獲得最後編譯時間。

~~~csharp
System.IO.File.GetLastWriteTime(this.GetType().Assembly.Location)
~~~


參考：

[http://tangzhongxin.blog.163.com/blog/static/89219612010113173146319/](http://tangzhongxin.blog.163.com/blog/static/89219612010113173146319/)