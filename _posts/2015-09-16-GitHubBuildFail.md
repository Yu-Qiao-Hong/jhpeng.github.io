---
layout: post
title: 'Git操作：強制刪除提交到遠程版本庫的數據與版本記錄'
author: 'James Peng'
tags: ['GIT']
---

github page 昨天還builde 好好的，完全沒改動的情況下，今天始終Page build failure，最後才發現問題在於 highlight 語法。


解決方案：

1.把_config.yml裡的

~~~text
    markdown: kramdown 
~~~

改成

~~~text
    markdown: redcarpet
~~~

2.把post內的.md文章 有用到 highlight 語法

~~~text
{% highlight cpp %}
// Code
{% endhighlight %}
~~~

改成

    ~~~cpp
    // Code
    ~~~

搞定！


附註：

- C#的語法：不是 ~~~cs 而是 ~~~csharp
- .yml的語法：不是 ~~~yml 而是 ~~~yaml
- 純文字 ~~~text


參考：

[http://loyc.net/2014/blogging-on-github.html](http://loyc.net/2014/blogging-on-github.html)