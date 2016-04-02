---
layout: post
title: 'C# 將 HTML 轉 PDF'
author: 'James Peng'
tags: ['C#']
---

透過第三方dll NReco.PdfGenerator 套件可以簡單辦到

## 使用方法 去讀取yahoo首頁 ##

~~~csharp
            new NReco.PdfGenerator.HtmlToPdfConverter().
            GeneratePdfFromFile(@"https://tw.yahoo.com/", null,
            AppDomain.CurrentDomain.BaseDirectory + "output.pdf");
~~~

## 結果:  ##

![](http://i.imgur.com/yP8L45s.png)


## 參考： ##

- https://pdfgenerator.codeplex.com/
- http://www.nrecosite.com/pdf_generator_net.aspx
- https://www.nuget.org/packages/NReco.PdfGenerator/
- http://no2don.blogspot.com/2016/02/c-nrecopdfgenerator-htmlpdf.html#more