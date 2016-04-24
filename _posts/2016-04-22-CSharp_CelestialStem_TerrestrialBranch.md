---
layout: post
title: 'C# 取得 天干 地支 算法'
author: 'James Peng'
tags: ['C#']
---

首先我們需要知道什麼是天干什麼是地支，有多少個天干多少個地支？

天干( Celestial Stem ) : 中國古代的一種文字計序符號，共10個字: 甲、乙、丙、丁、戊、己、庚、辛、壬、癸，循環使用。

地支( Terrestrial Branch ) : 中國古代的一種文字計序符號，共12個字∶子、醜、寅、卯、辰、巳、午、未、申、酉、戌、亥，循環使用。


----------


## 天干寓意 ##

- （甲）像草林破土而萌，陽在內而被陰包裹。又有認為，甲者鎧甲也，把萬物衝破其甲而突出了。
- （乙）草木初生，枝葉柔軟屈曲伸長。乙者軋也。
- （丙）丙，炳也，如赫赫太陽，炎炎火光，萬物皆炳然著見而明。
- （丁）壯也，草木成長壯實，好比人的成丁。
- （戊）茂也，象徵大地草木茂盛。
- （己）起也，紀也，萬物仰屈而起，有形可紀。
- （庚）更也，秋收而待來春。
- （辛）金味辛，物成而後有味。又有認為，辛者新也，萬物肅然更改，秀實新成。
- （壬）妊也，陽氣潛伏地中，萬物懷妊。
- （癸）揆也，萬物閉藏，懷妊地下，揆然明芽。


----------


## 地支寓意 ##

- （子）孽也，草木生子，吸土中水分而出，為一陽萌的開始。
- （醜）紐也，草木在土中出芽，屈曲著將要冒出地面。
- （寅）演也，津也，寒土中屈曲的草木，迎著春陽從地面伸展。
- （卯）茂也，日照東方，萬物滋茂。
- （辰）震也，伸也，萬物震起而生，陽氣生髮已經過半。
- （巳）起也，萬物盛長而起，陰氣消盡，純陽無陰。
- （午）仵也，萬物豐滿長大，陽起充盛，陰起開始萌生。
- （未）味也，果實成熟而有滋味。
- （申）身也，物體都已長成。
- （酉）老也，猶也，萬物到這時都猶縮收斂。
- （戌）滅也，草木凋零，生氣滅絕。
- （亥）劾也，陰氣劾殺萬物，到此已達極點


----------


天干地支兩者組合中生成六十甲子所以古人便說六十歲為一甲子

## 六十甲子循序： ##

1. 甲子
2. 乙丑
3. 丙寅
4. 丁卯
5. 戊辰
6. 己巳
7. 庚午
8. 辛未
9. 壬申
10. 癸酉
11. 甲戌
12. 乙亥
13. 丙子
14. 丁丑
15. 戊寅
16. 己卯
17. 庚辰
18. 辛巳
19. 壬午
20. 癸未
21. 甲申
22. 乙酉
23. 丙戌
24. 丁亥
25. 戊子
26. 己丑
27. 庚寅
28. 辛卯
29. 壬辰
30. 癸巳
31. 甲午
32. 乙未
33. 丙申
34. 丁酉
35. 戊戌
36. 己亥
37. 庚子
38. 辛丑
39. 任寅
40. 癸卯
41. 甲辰
42. 乙巳
43. 丙午
44. 丁未
45. 戊申
46. 己酉
47. 庚戌
48. 辛亥
49. 壬子
50. 癸丑
51. 甲寅
52. 乙卯
53. 丙辰
54. 丁己
55. 戊午
56. 己未
57. 庚申
58. 辛酉
59. 壬戌
60. 癸亥


----------

我們從上面了解到天干有10個地支有12個組合成60個甲子，OK我地首先做成2個數組用來保存十天干和十二地支。

天干：甲乙丙丁戊己庚辛壬癸
地支：子丑寅卯辰巳午未申酉戌亥


----------



# 年份的天干地支計算方式 #


因為年干支的干支配合雖後代才有，但其應用是仍從公元後1年開始。

剛好公元前第四年為甲子年 ​​，減去3是為了計算的方便，把公元前和公元後兩者的記年法分開來言。

根據《素問·六微旨要大論》中言“子甲相和，名曰歲立”理論，把公元後記年仍從甲子年 ​​開始，所以要減去前3年，目的是讓公元 ​​後一年亦為甲子年 ​​。

所以公式為：

> 天干= (當前年份— 3 ) Mod 10 
> 
> 地支= (當前年份— 3 ) Mod 12



天干地支：



<table border="1" cellspacing="0" cellpadding="0">
<tbody>
<tr>
<td valign="top" width="55">
<p align="center"><font><font class="">index</font></font></p>
</td>
<td valign="top" width="55">
<p align="center"><font><font>0</font></font></p>
</td>
<td valign="top" width="55">
<p align="center"><font><font>1</font></font></p>
</td>
<td valign="top" width="55">
<p align="center"><font><font>2</font></font></p>
</td>
<td valign="top" width="55">
<p align="center"><font><font>3</font></font></p>
</td>
<td valign="top" width="55">
<p align="center"><font><font>4</font></font></p>
</td>
<td valign="top" width="55">
<p align="center"><font><font>5</font></font></p>
</td>
<td valign="top" width="55">
<p align="center"><font><font>6</font></font></p>
</td>
<td valign="top" width="55">
<p align="center"><font><font>7</font></font></p>
</td>
<td valign="top" width="55">
<p align="center"><font><font>8</font></font></p>
</td>
<td valign="top" width="55">
<p align="center"><font><font>9</font></font></p>
</td>
<td valign="top" width="55">
<p align="center"><font><font>10</font></font></p>
</td>
<td valign="top" width="55">
<p align="center"><font><font>11</font></font></p>
</td>
</tr>
<tr>
<td valign="top" width="55">
<p align="center"><font><font>天干</font></font></p>
</td>
<td valign="top" width="55">
<p align="center"><font><font>癸</font></font></p>
</td>
<td valign="top" width="55">
<p align="center"><font><font>甲</font></font></p>
</td>
<td valign="top" width="55">
<p align="center"><font><font>乙</font></font></p>
</td>
<td valign="top" width="55">
<p align="center"><font><font>丙</font></font></p>
</td>
<td valign="top" width="55">
<p align="center"><font><font>丁</font></font></p>
</td>
<td valign="top" width="55">
<p align="center"><font><font>戊</font></font></p>
</td>
<td valign="top" width="55">
<p align="center"><font><font>己</font></font></p>
</td>
<td valign="top" width="55">
<p align="center"><font><font>庚</font></font></p>
</td>
<td valign="top" width="55">
<p align="center"><font><font>辛</font></font></p>
</td>
<td valign="top" width="55">
<p align="center"><font><font>壬</font></font></p>
</td>
<td valign="top" width="55">
<p align="center">
</p></td>
<td valign="top" width="55">
<p align="center">
</p></td>
</tr>
<tr>
<td valign="top" width="55">
<p align="center"><font><font>地支</font></font></p>
</td>
<td valign="top" width="55">
<p align="center"><font><font>亥</font></font></p>
</td>
<td valign="top" width="55">
<p align="center"><font><font>子</font></font></p>
</td>
<td valign="top" width="55">
<p align="center"><font><font>醜</font></font></p>
</td>
<td valign="top" width="55">
<p align="center"><font><font>寅</font></font></p>
</td>
<td valign="top" width="55">
<p align="center"><font><font>卯</font></font></p>
</td>
<td valign="top" width="55">
<p align="center"><font><font>辰</font></font></p>
</td>
<td valign="top" width="55">
<p align="center"><font><font>巳</font></font></p>
</td>
<td valign="top" width="55">
<p align="center"><font><font>午</font></font></p>
</td>
<td valign="top" width="55">
<p align="center"><font><font>未</font></font></p>
</td>
<td valign="top" width="55">
<p align="center"><font><font>申</font></font></p>
</td>
<td valign="top" width="55">
<p align="center"><font><font>酉</font></font></p>
</td>
<td valign="top" width="55">
<p align="center"><font><font>戌</font></font></p>
</td>
</tr>
<tr>
<td colspan="13" valign="top" width="712">
<p align="left"><font><font>(注：地支可以配合十二生肖年一起計算)</font></font></p>
</td>
</tr>
<tr>
<td valign="top" width="55">
<p align="center"><font><font>生肖</font></font></p>
</td>
<td valign="top" width="55">
<p align="center"><font><font>亥豬</font></font></p>
</td>
<td valign="top" width="55">
<p align="center"><font><font>子鼠</font></font></p>
</td>
<td valign="top" width="55">
<p align="center"><font><font>丑牛</font></font></p>
</td>
<td valign="top" width="55">
<p align="center"><font><font>寅虎</font></font></p>
</td>
<td valign="top" width="55">
<p align="center"><font><font>卯兔</font></font></p>
</td>
<td valign="top" width="55">
<p align="center"><font><font>辰龍</font></font></p>
</td>
<td valign="top" width="55">
<p align="center"><font><font>巳蛇</font></font></p>
</td>
<td valign="top" width="55">
<p align="center"><font><font>午馬</font></font></p>
</td>
<td valign="top" width="55">
<p align="center"><font><font>未羊</font></font></p>
</td>
<td valign="top" width="55">
<p align="center"><font><font>申猴</font></font></p>
</td>
<td valign="top" width="55">
<p align="center"><font><font>酉雞</font></font></p>
</td>
<td valign="top" width="55">
<p align="center"><font><font>戌狗</font></font></p>
<p>&nbsp;</p></td>
</tr>
</tbody>
</table>


----------


六十甲子公式：天干＋ 地支

計算年份對應的天干地支甲子都出黎啦下面當然是事例啦！就拿2010年來計算一下。

手算：

    Year = 2010 
    Celestial Stem = ( Year – 3 ) Mod 10 
    = ( 2010 – 3 ) Mod 10 
    = 2007 Mod 10 
    = 7 
    =庚


----------



    Terrestrial Branch = ( Year – 3 ) Mod 12 
    = ( 2010 – 3 ) Mod 12 
    = 2007 Mod 12 
    = 3 
    =寅
    Chinese Animal =寅虎


----------


    A Cycle Of Sixty Years(甲子) = Celestial Stem + Terrestrial Branch 
    =庚寅


----------

## C# 計算 年天干 ##

~~~csharp
        private string GetSky(int year)
        {
            string[] Sky = { "癸" , "甲", "乙", "丙", "丁", "戊", "己", "庚", "辛", "壬"};
            int i = (year - 3) % 10;
            return Sky[i];
        }
~~~

![](http://i.imgur.com/rFuaLHu.png)


----------


## C# 計算 年地支 ##

~~~csharp
        private string GetGround(int year)
        {
            string[] Ground = {"亥", "子", "丑", "寅", "卯", "辰", "巳", "午", "未", "申", "酉", "戌" };
            int i = (year - 3) % 12;
            return Ground[i];
        }
~~~

![](http://i.imgur.com/BFKRclf.png)



----------

## C# 計算 年天干地支 ##

~~~csharp
        private string GetSkyGround(int year)
        {
            return GetSky(year) + GetGround(year);
        }
~~~

![](http://i.imgur.com/5RJDZ1c.png)

----------

# 月份的天干地支計算方式 #



月份的天干地支算法，以2010年為事例我們先計算正月的天干地支
正月天干​​=如果天干數小於5公式上需要加上5如果大於等於5公式上需要減去5，
正月地支=年地支

## 公式如下： ##

    正月天干​​= 2 × Year Celestial Stem — 4 ＋ (Year Celestial Stem 〈 5 ) ? 5 : -5已經知道年份的天干數為7大於5 
    正月天干 ​​為= 2 × Year Celestial Stem — 4 ＋ -5 
    = 2 × 7 — 4 ＋ -5 
    = 14 — 4 ＋ -5 
    = 5 
    =戊



    正月天干 ​​地址=九月天干​​+ Year Terrestrial Branch 
    =戊寅


----------


## 日天干地支算法公式： ##

    日天干：=( 4 * C + [ C / 4 ] + [ 5 * Y ] + [ Y / 4 ] + [ 3 * ( M + 1 ) / 5 ] + D – 3 ) Mod 10 
    日地支：=( 8 * C + [ C / 4 ] + [ 5 * Y ] + [ Y / 4 ] + [ 3 * ( M + 1 ) / 5 ] + D + 7 + I ) Mod 12 


其中C代表年份頭兩位數如： 2010年C=20 
Y代表年份尾兩位數如： 2010年Y=10 
M代表月份數如2010年10月M=10 
D代表日數如2010年10月7日D =7 
I是需要判斷當前月份是奇數月還是偶數月奇數月I=0偶數月I=6 
[ ]是取整數的意思


----------


## 從上面公式中可以簡化為下面公式： ##

    日天干總數：G = 4 * C + [ C / 4 ] + [ 5 * Y ] + [ Y / 4 ] + [ 3 * ( M + 1 ) / 5 ] + D – 3 
    日地支總數：Z = G + 4 * C + 10 + I


    日天干：= G Mod 10 
    日地支：= Z Mod 12


----------


就以2010年10月7日來做例子
日天干總數：G = 4 * C + [ C / 4 ] + [ 5 * Y ] + [ Y / 4 ] + [ 3 * ( M + 1 ) / 5 ] + D – 3 
G = 4 * 20 + [ 20 / 4 ] + [5 * 10 ] + [ 10 / 4 ] + [ 3 * ( 10 + 1 ) / 5 ] + 7 – 3 
G = 80 + 5 + 50 + 2 + 6 + 7 – 3 
G = 147

日地支總數：Z = G + 4 * C + 10 + I 10月雙數I=6 
Z = 147 + 4 * 20 + 10 + 6 
Z = 147 + 80 + 10 + 6 
Z = 243

日天干: = G Mod 10 = 147 Mod 10 = 7 =庚
日地支: = Z Mod 12 = 243 Mod 12 = 3 =寅
日天干地支為：庚寅


----------


## 二十四小時和十二時辰對照表 ##

- 子(23-01)
- 醜(01-03)
- 寅(03-05)
- 卯(05-07)
- 辰(07-09)
- 己(09-11) 
- 午(11-13)
- 未(13-15)
- 申(15-17)
- 酉(17-19)
- 戊(19-21)
- 亥(21-23)

----------

參考：

- http://www.zhaorong.me/archives/751