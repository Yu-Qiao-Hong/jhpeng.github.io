---
layout: post
title: 'WIN8自動login 不需password'
author: 'James Peng'
tags: ['Win8']
---

    HKLM\Software\Microsoft\Windows NT\CurrentVersion\winlogon 


## Set:  ##

1. AutoAdminLogon = "1" Enabled  (Zero would mean turn off)
2. DefaultUserName = "Guyt" (Your logon username)
3. DefaultPassword = "Passw0rd" (Remember this or change)
4. DefaultDomainName = "Compal" (Only needed if this computer has joined a domain)


![](http://i.imgur.com/sTWJGA6.png)

![](http://i.imgur.com/qybAwEM.png)


## 參考 ##

- http://technet.microsoft.com/en-us/library/cc939702.aspx
- http://www.computerperformance.co.uk/win8/windows8-autoadminlogon-registry.htm


  

