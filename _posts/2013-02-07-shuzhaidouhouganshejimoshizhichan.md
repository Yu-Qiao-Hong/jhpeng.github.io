---
layout: post
title: '[書摘讀後感] 設計模式之禪'
author: 'James Peng'
tags: ['讀書心得']
---

[![13 -
10](http://lh4.ggpht.com/-vDJ4kBFFL-o/URyCoxPwEWI/AAAAAAAARKA/3aYNCLl-Pb8/13%252520-%25252010%25255B5%25255D.jpg?imgmax=800 "13 - 10")](http://www.taaze.tw/apredir.html?ap125329572_a_11100247878)

> 設計模式之禪  
> 作者：秦小波  
> 譯者：楊仁和  
> 出版社：碁峰  
> 出版日期：2010年10月19日  
> 語言：繁體中文 ISBN：9789862760062  
> 裝訂：平裝

造句：

1.  設計模式之 殘念
2.  設計模式之 慚愧
3.  設計模式之 難纏
4.  設計模式之 春蠶到死絲方盡
5.  設計模式之 夏蟬至秋聲方竭

 

[![13 -
9](http://lh3.ggpht.com/-D8QLtRsqyR8/URyCpgu010I/AAAAAAAARKI/R0BETnB9m2w/13%252520-%2525209%25255B9%25255D.jpg?imgmax=800 "13 - 9")](http://www.taaze.tw/apredir.html?ap125329572_a_11100247878)

內容簡介：

> 設計模式領域的又一里程碑之作  
>  The Zen of Design Patterns
>
> 禪宗日：“教外別傳，不立文字”，禪的境界本不該用文字來描述，言語也道不明白，但為了傳道，悟道者仍要藉言語來說明。
>
> 何為禪？一種境界，一種體驗，一種精神領域的最高修為。何為設計模式？對物件導向思想的深刻理解，對軟體設計方法和編碼經驗的完美總結。
>
> 本書是創造者的心路歷程，是實踐者的智慧結晶，是得道者的禪悟。它透過幽默風趣的故事和通俗易懂的講述方式，引導你悟透設汁模式的真諦。
>
> 如果你在思考下面這些問題，也許本書就是你想要的！
>
> ．業務分析如此細緻，架構設計如此強健、可靠且穩定，但為何仍然無法適應業務發展的需要，而且生命周期只有短短幾年？
>
> ．為何你的團隊協作了多年卻始終無法沉澱出可重利用的組件或構件？依賴和解耦合的標準是什麼？如何才能做到既不相互“刺傷”，又能相互“取暖”的境界？
>
> ．架構設計時，如何才能實現高可擴展性和易維護性？如何避免維護成本大於開發成本的悲哀現狀？
>
> ．交易型的系統如何大規模地藉用設計模式的思想，以實現高性能、高可靠性的建設目標？
>
> ．架構設計時，如果遇到這樣的情況：“有一個請求者和多個處理者，同時要求二者之間解耦合，以便處理者可以動態地擴展“，這該如何處理？
>
> ．如果遇到這樣的場景：“多個物件依賴一個物件，該物件狀態改變時，所有的依賴者都要相應地獲得通知，並且要求物件之間鬆散耦合”，這該如何處理？
>
> ．萬物皆物件，不可能把每一個物件都分解到原子級別，如何適度地細化物件的粒度？怎樣界定物件的粒度大小？
>
> ．同為創建類模式，工廠方法模式和建造者模式都可以建立物件，它們之間有何區別？適用的場景又有何不同？
>
> ．狀態模式和策略模式的通用類別圖如此相似，在實際的應用場景中如何區分它們？
>
> ．如何使命令模式和責任鏈模式完美地搭配並建立一個高可擴展性的系統架構，以解決客戶端和處理者皆被參數化的場景？
>
> ．觀察者模式和責任鏈模式真的沒有可比性嗎？它們的主要區別何在？實際應用中如何使用？
>
> ．組合模式只能用來表示部分和整體的關係嗎？從中擴展出的規格模式是如何實作的？透明的組合模式和安全的組合模式有何區別？

* * * * *

**書摘1：**

> 單一職責原則 [Single Responsibility
> Principle](http://zh.wikipedia.org/wiki/%E5%8D%95%E4%B8%80%E5%8A%9F%E8%83%BD%E5%8E%9F%E5%88%99)
> ，簡稱SRP。
>
> 原文定義：There should never be more than one reason for a class to
> change.
>
> 翻譯：應該有且僅有**一個原因**，引起class的**變化**。
>
> 最佳實踐：
>
> -   建議interface一定要做到單一職責，class的設計盡量做到只有一個原因引起變化。

 

**讀後感：**

 

餐刀

餐叉

湯匙

筷子

國家

西方

西方

西方

東方

學習成本

容易

容易

容易

困難

複雜性

低

低

低

高

職責

切牛排

固定牛排

喝湯

夾菜、扒飯、叉貢丸、切肉。

變化因素

1.  食物{x}

1.  食物{x}

1.  食物{x}

1.  食物{x}。
2.  用法{y}。

舉例  
(new 出的Instance)

切牛排的餐刀  
切豬排的餐刀  
切雞排的餐刀  

切貢丸的餐刀

叉牛排的餐叉  
叉豬排的餐叉  
叉雞排的餐叉  

叉貢丸的餐叉

挖湯的湯匙  
挖布丁的湯匙  
挖果凍的湯匙  
挖炒飯的湯匙

夾菜的筷子。  
挖飯的筷子。  
叉貢丸的筷子。  
切肉排的筷子。

class的**變化**

切{x}的餐刀  

叉{x}的餐叉  

挖{x}的湯匙  

{y}{x}的筷子  
{y}{x}的筷子  
{y}{x}的筷子

職責數量

單一職責

單一職責

單一職責

多重職責

職責應該單一，並且簡單得讓我不需要深入思考。

東方人：「吃個飯，洋鬼子拿要一堆餐具，我們拿雙筷子就好了。」（吃飯簡單，但餐具使用變複雜）

西方人：「吃個飯，黃猴子把餐具搞那麼複雜，我們餐具都不用學。」（餐具簡單，但西餐規矩變多）

原則是死的，人是活的。還是要自行衡量。（真玄）

 

* * * * *

**書摘2：**

> 里氏替換原則 ([Liskov substitution
> principle](http://zh.wikipedia.org/wiki/%E9%87%8C%E6%B0%8F%E6%9B%BF%E6%8D%A2%E5%8E%9F%E5%88%99))
> ，簡稱LSP
>
> 原文定義：
>
> 1.  If for each object o1 of type S there is an object o2 of type T
>     such that for all programs P defined in terms of T,the behavior of
>     P is unchanged when o1 is substituted for o2 then S is a subtype
>     of T.
> 2.  Functions that use pointers or references to base classes must be
>     able to use objects of derived classes without knowing it.
>
> 翻譯：
>
> 1.  如果對每一個型別為S的物件o1，都有型別為T的物件o2，使得以T定義的所有程式P在所有的物件o1都替換成o2時，程式P的行為沒有發生變化，那麼型別S就是型別T的子型別。
> 2.  所有參照基礎類別的地方必須能透明地使用其衍生類別的物件。
>
>  

 

**讀後感：**

以下為個人理解：

童話故事「乞丐王子」，「王子」和
「乞丐」替換身分後也不會產生錯誤或異常，皇宮侍衛根本就不知道是「乞丐王子」還是「王子乞丐」。

童話界稱之為「**乞丐王子替換原則**」。以上比喻可能有點問題。

換個比喻

我有個
吃3號電池的高級體重計(系統)，不管我裝「黑貓電池、白貓電池」還是「盡量電池」，高級體重計不會產生錯誤或異常，能正常執行。

<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<tbody>
<tr class="odd">
<td align="left">台灣用語
父類別
子類別</td>
<td align="left">大陸用語
基類別
派生類別</td>
<td align="left">英文名
base class
derived class</td>
</tr>
</tbody>
</table>

「**不管白貓黑貓，能抓到老鼠就是好貓**」 by 鄧小平同志

 

* * * * *

**書摘3：**

> 倚賴倒置原則 Dependency Inversion Principle，簡稱DIP。
>
> 原文定義：
>
> -   High level modules should not depend upon low level modules. Both
>     shoulddepend upon abstractions.
> -   Abstractions should not depend upon details. Details should depend
>     uponabstractions.
>
> 翻譯：
>
> -   高層模組不應該倚賴低層模組，兩者都應該倚賴其抽象。
> -   抽象不應該倚賴細節。
> -   細節應該倚賴抽象。
>
> 更精簡的定義就是「介面導向程式設計」

 

**讀後感：**

可以結合里氏替換原則。

「**Design by Contract**」就是要「**按照契約來設計**」。

製造廠商只要遵照「契約規格書」來設計「3號電池」，就不用依賴「同一家代工廠」。

<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<tbody>
<tr class="odd">
<td align="left">台灣用語
介面
類別</td>
<td align="left">大陸用語
接口
類</td>
<td align="left">英文名
interface
class</td>
</tr>
</tbody>
</table>

 

至於「倚賴倒置」這個詭異名詞是啥：

<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<tbody>
<tr class="odd">
<td align="left"> 
倚賴正置
倚賴倒置</td>
<td align="left">現實世界
實際存在的
抽象的</td>
<td align="left">製造電池依賴
同一家代工廠
相同規格書</td>
</tr>
</tbody>
</table>

就是反過來依賴「抽象的東西」，就像是借我幾億元，「依賴借據」應該是比較穩固的。（人間蒸發）

 

* * * * *

**書摘4：**

> 介面隔離原則 Interface Segregation Principle，簡稱ISP。
>
> 原文定義：
>
> -   Clients should not be forced to depend upon interfaces that they
>     don't use.
> -   The dependency of one class to another one should depend on the
>     smallest possible interface.
>
> 翻譯：
>
> 1.  客戶端不應該依賴他不需要的介面。
> 2.  類別間的依賴關係應該建立在最小的介面上。

**讀後感：**

就是依賴他需要的介面就好。

You can’t have everything, I mean where would you put it? (Steven
Wright)  
你不能全都要，我說，你有地方擺嗎？

「殺雞焉用牛刀」

 

可以和單一職責原則比較。

 

單一職責原則

介面隔離原則

注重的點

職責越少越好

介面裡的方法盡量少

餐刀

職責單一為「切牛排」。

切的介面：

1.  右手切的方法。
2.  左手切的方法。

餐叉

職責單一為「固定牛排」。

叉的介面：

1.  右手叉的方法。
2.  左手叉的方法。

湯匙

職責單一為「喝湯」。

挖的介面：

1.  右手挖的方法。
2.  左手挖的方法。

筷子

職責多重為「夾菜、扒飯、叉貢丸、切分肉」。

筷子的介面：

1.  右手夾的方法。
2.  左手夾的方法。
3.  右手單支叉的方法。
4.  左手單支叉的方法。
5.  右手挖的方法。
6.  左手挖的方法。
7.  右手切的方法。
8.  左手切的方法。

 

筷子部分可以改為建立在最小的介面上，如下：

 

單一職責原則

介面隔離原則

筷子

職責多重為「夾菜、扒飯、叉貢丸、切分肉」。

夾的介面：

1.  右手夾的方法。
2.  左手夾的方法。

叉的介面：

1.  右手單支叉的方法。
2.  左手單支叉的方法。

挖的介面：

1.  右手挖的方法。
2.  左手挖的方法。

切的介面：

1.  右手切的方法。
2.  左手切的方法。

介面一樣不能分太細，否則會變成一個介面、一個方法。

怎麼吃飯。

 

* * * * *

**書摘5：**

> 迪米特法則 [Law of
> Demeter](http://zh.wikipedia.org/wiki/%E5%BE%97%E5%A2%A8%E5%BF%92%E8%80%B3%E5%AE%9A%E5%BE%8B)，簡稱LoD。最少知識原則[Least
> Knowledge
> Principle](http://zh.wikipedia.org/wiki/%E5%BE%97%E5%A2%A8%E5%BF%92%E8%80%B3%E5%AE%9A%E5%BE%8B)，簡稱LKP。兩個是同一個規則。
>
> 原文定義：
>
> -   Each unit should have only limited knowledge about other units:
>     only units "closely" related to the current unit.
> -   Each unit should only talk to its friends; don't talk to
>     strangers.
> -   Only talk to your immediate friends.
>
> 翻譯：
>
> 1.  每個單元對於其他的單元只能擁有有限的知識：只是與當前單元緊密聯繫的單元；
> 2.  每個單元只能和它的朋友交談：不能和陌生單元交談；
> 3.  只和朋友交流。

**讀後感：**

其實就是物件導向的「封裝概念」和「資訊隱藏概念」。

肥宅幫正妹修電腦，正妹並不想知道太多技術細節。

正妹內心OS為「死肥宅，修好快滾，臭死了」(資訊隱藏)

你可以相信朋友，但不可以相信朋友的朋友。

 

人心隔肚皮。

 

* * * * *

**書摘6：**

> 開閉原則 [Open Close
> Principle](http://zh.wikipedia.org/wiki/%E5%BC%80%E9%97%AD%E5%8E%9F%E5%88%99)，簡稱OCP。
>
> 原文定義：
>
> -   software entities (classes, modules, functions, etc.) should be
>     open for extension, but closed for modification
>
> 翻譯：
>
> -   一個軟體實體如類別、模組和函式應該對擴展開放，對修改關閉。

 

**讀後感：**

例如，你的iphone。

<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<tbody>
<tr class="odd">
<td align="left"> 
擴展開放，對修改開放。
擴展開放，對修改關閉。</td>
<td align="left">想要加強續航力
1.拆開來改電池，再裝回去。<br />2. 破壞保固。
1.加裝一個電源殼。<br />2.不破壞保固。</td>
</tr>
</tbody>
</table>

還是乖乖外接尿袋。好了。

 

* * * * *

**結論：**

這些大師不知道再說哪國語言。

還蠻多精神標語的。抽象的難以實作。

後面23種設計模式還沒看，我就累了，下次有空再看。（沒空）

 

快過年了。恭喜發財啊！（敷衍）

