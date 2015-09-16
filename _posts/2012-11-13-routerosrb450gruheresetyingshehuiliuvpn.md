---
layout: post
title: 'RouterOS RB450G 如何RESET、映射回流、vpn'
author: 'James Peng'
tags: ['軟體使用心得']
---

RB450G 如何RESET機器

1.拔除電源

2.需要拆機殼

3.在板子內部右上角的部分有圓形中間有分開上面有Reset字樣,需使用用螺絲起子金屬把它短路

![image](http://lh3.ggpht.com/-ux_n7QhCuSU/UKJHKkr-mhI/AAAAAAAAOew/1TD2zAz2c7c/image%25255B39%25255D.png?imgmax=800 "image")

![image](http://lh3.ggpht.com/-XTIxepYA7ZI/UKJHM7yJ41I/AAAAAAAAOe0/WRrAhMxVhj8/image%25255B40%25255D.png?imgmax=800 "image")

4.再插電 等他開機完成

參考: <http://wiki.mikrotik.com/wiki/Manual:Password_reset>

* * * * *

RB450G 設定遠端桌面

IP –\> Firewall

[![image](http://lh5.ggpht.com/-T_Grm8AOdHU/UKJgV52vZHI/AAAAAAAAOkg/FU9z6pBs4SY/image_thumb%25255B30%25255D.png?imgmax=800 "image")](http://lh3.ggpht.com/-hABeAKqnxH0/UKJgU7mBHPI/AAAAAAAAOkc/XclEfLauAhQ/s1600-h/image%25255B70%25255D.png)

* * * * *

RB450G  如何設定80 port mapping 映射和回流

1.先把WEB管理介面80port 改其他PORT

IP –\> Services

![image](http://lh6.ggpht.com/-ADBQCCRUYn0/UKJHQw5QcuI/AAAAAAAAOe8/1GjXi9Zjtn4/image%25255B42%25255D.png?imgmax=800 "image")

2.設定映射

IP –\> Firewall

[![image](http://lh3.ggpht.com/-ObwPof5nR2w/UKJgXaobbbI/AAAAAAAAOk0/B-uVypZPH0s/image_thumb%25255B28%25255D.png?imgmax=800 "image")](http://lh5.ggpht.com/-XJL5M4d0ZKI/UKJgWl-EqXI/AAAAAAAAOks/t_C0D9IQZXI/s1600-h/image%25255B66%25255D.png)

[![image](http://lh6.ggpht.com/-ocrMt3m9ojA/UKJgY0JwIoI/AAAAAAAAOlE/CfdIoN4Fk-E/image_thumb%25255B26%25255D.png?imgmax=800 "image")](http://lh5.ggpht.com/-AlyVAn1UlvY/UKJgYOIGMGI/AAAAAAAAOk8/u2wVk0Ls3gI/s1600-h/image%25255B62%25255D.png)

外網ip就可以正常連入了,但內網ip無法連上

3.設定回流

[![image](http://lh5.ggpht.com/-YzUnfK3IYrQ/UKJgbcX1c_I/AAAAAAAAOlQ/Uf5-1NiJvKg/image_thumb%25255B24%25255D.png?imgmax=800 "image")](http://lh5.ggpht.com/-HGQMsmXBlGE/UKJgaDKG-5I/AAAAAAAAOlM/H-j_zZXneCw/s1600-h/image%25255B58%25255D.png)

[![image](http://lh6.ggpht.com/-i5QWeAp0o2w/UKJgdKi3RpI/AAAAAAAAOlk/gq-0VFXRGBA/image_thumb%25255B22%25255D.png?imgmax=800 "image")](http://lh4.ggpht.com/-eOtXANR8nGU/UKJgb3yKqhI/AAAAAAAAOlc/Cy8vxQQXbic/s1600-h/image%25255B54%25255D.png)

搞定

* * * * *

RB450G 如何設定自動連vpn

1.Interface –\> 新增PPTP client

填入要連入的VPN IP(公司的或學校的)、和相關帳號密碼

![image](http://lh6.ggpht.com/-xijhFyeK45o/UKJdRB_XGgI/AAAAAAAAOig/v1ESJpeY5w4/image%25255B38%25255D.png?imgmax=800 "image")

status: connected 就連上了

2.防火牆打開vpn出口

![image](http://lh6.ggpht.com/-C6wHYRYLFO4/UKJdTIe7b_I/AAAAAAAAOik/myyFVs2PZdw/image%25255B36%25255D.png?imgmax=800 "image")

![image](http://lh3.ggpht.com/-XhTxOobMcbU/UKJdVBZ0oGI/AAAAAAAAOio/-Np-RyD9srg/image%25255B37%25255D.png?imgmax=800 "image")

3.設路由，讓連到這些ip時自動用vpn

IP –\> Route

[![image](http://lh4.ggpht.com/-L4cMiRwqJxE/UKJggvSDFuI/AAAAAAAAOl0/86x3NW-jz9s/image_thumb%25255B20%25255D.png?imgmax=800 "image")](http://lh5.ggpht.com/-6l58_vyLU-I/UKJgfvfMN0I/AAAAAAAAOls/NiKoa8Rr8ic/s1600-h/image%25255B50%25255D.png)

[![image](http://lh6.ggpht.com/-dP-UViUhQWk/UKJgii_BYXI/AAAAAAAAOmE/JV1v17f9Qds/image_thumb%25255B18%25255D.png?imgmax=800 "image")](http://lh4.ggpht.com/-fWU0-EyOT6o/UKJghrFbwPI/AAAAAAAAOl8/dzTdDICZUQA/s1600-h/image%25255B46%25255D.png)

[![image](http://lh5.ggpht.com/-qPqaWrSXFxQ/UKJglHgaYVI/AAAAAAAAOmQ/lUbsaVfUgLs/image_thumb%25255B16%25255D.png?imgmax=800 "image")](http://lh5.ggpht.com/-r4K7_ezpS90/UKJgj8i7jmI/AAAAAAAAOmM/0kEqI3ye2Kw/s1600-h/image%25255B42%25255D.png)

測試成功

![image](http://lh3.ggpht.com/-FoMAAclB7sY/UKJdeGusLII/AAAAAAAAOi4/Qu6ZS55zc84/image%25255B32%25255D.png?imgmax=800 "image")

