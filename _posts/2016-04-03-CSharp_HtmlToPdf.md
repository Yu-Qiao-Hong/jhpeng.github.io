---
layout: post
title: 'C# 將 HTML 轉 PDF'
author: 'James Peng'
tags: ['C#']
---

透過第三方dll NReco.PdfGenerator 套件可以簡單辦到
它具有免費和付費版本，非常值得的。

## 使用方法 ##

嘗試去讀取 Yahoo首頁 轉成 PDF 

~~~csharp
            new NReco.PdfGenerator.HtmlToPdfConverter().
            GeneratePdfFromFile(@"https://tw.yahoo.com/", null,
            AppDomain.CurrentDomain.BaseDirectory + "output.pdf");
~~~

## 結果:  ##

一真神奇 行cod 就完成了

![](http://i.imgur.com/yP8L45s.png)


## 參考： ##

- https://pdfgenerator.codeplex.com/
- http://www.nrecosite.com/pdf_generator_net.aspx
- https://www.nuget.org/packages/NReco.PdfGenerator/
- http://no2don.blogspot.com/2016/02/c-nrecopdfgenerator-htmlpdf.html#more