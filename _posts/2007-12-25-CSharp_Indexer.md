---
layout: post
title: 'C# 使用索引子 Indexer'
author: 'James Peng'
tags: ['C#']
---

C#中的索引子 (Indexer)是一個相當直覺好用的設計，讓自訂的類別 在存取內部資料時，像是存取陣列一樣。通常用來封裝內部集合或陣列。

例如，存取 TempRecord 執行個體中的溫度

一般的存取方式

~~~csharp
float temp = tr.temps[4]。
~~~

使用索引子的存取方式

~~~csharp
float temp = tr[4] ，
~~~


----------

# 如果想使用文字當做索引時 #


## 加入命名空間 ##

~~~csharp
using System.Collections;
~~~

----------


## 範例 StringIndexSample.cs ##

在 StringIndexSample 物件 中使用 Indexer，使用者可以指定 string 或是 int 就可以存取內部的資料：

~~~csharp


    public class StringIndexSample
    {

        ArrayList _fieldnumber = new ArrayList();
        ArrayList _fieldnames = new ArrayList();
        ArrayList _data = new ArrayList();


        public StringIndexSample()
        {

        }

        public StringIndexSample(string[] fieldnames, string[] data)
        {
            // check if the length of array fieldnames equals to the length of array data

            int length = fieldnames.Length;

            for (int i = 0; i < length; i++)
            {
                _fieldnumber.Add(i);
                _fieldnames.Add(fieldnames[i]);
                _data.Add(data[i]);
            }

        }

        public string this[string s]
        {
            get
            {
                int index;
                for (index = 0; index < this._fieldnames.Count; index++)
                {
                    if (this._fieldnames[index].Equals(s)) break;
                }
                return (string)(this._data[index]);
            }
            set
            {
                int index;
                for (index = 0; index < this._fieldnames.Count; index++)
                {
                    if (this._fieldnames[index].Equals(s)) break;
                }
                if (index < this._fieldnames.Count) this._data[index] = value;
                else
                {
                    _fieldnumber.Add(this._fieldnames.Count + 1);
                    _fieldnames.Add(s);
                    _data.Add(value);
                }
            }
        }



        public string this[int i]
        {
            get
            {
                int index;
                for (index = 0; index < this._fieldnames.Count; index++)
                {
                    if (this._fieldnumber[index].Equals(i)) break;
                }
                return (string)(this._data[index]);
            }
            set
            {
                int index;
                for (index = 0; index < this._fieldnames.Count; index++)
                {
                    if (this._fieldnumber[index].Equals(i)) break;
                }
                if (index < this._fieldnames.Count) this._data[index] = value;
                else
                {

                }
            }
        }



    } // end of class
~~~


----------


## 使用結果 ##

~~~text
    
        private void button1_Click(object sender, EventArgs e)
        {

            StringIndexSample testing = new StringIndexSample();

            //隨便輸入一個索引文字  並且給值
            testing["name"] = "james";
            MessageBox.Show(testing["name"]);

            //再輸入一個索引文字  並且給值 
            testing["url"] = "note.jhpeng.com";
            MessageBox.Show(testing["url"]);

            //也可以用數字叫出
            MessageBox.Show(testing[1]);
            MessageBox.Show(testing[2]);   
            

        }
~~~


![](http://i.imgur.com/5SkHtGI.png)

![](http://i.imgur.com/Lmokpcr.png)

----------

參考：

- https://msdn.microsoft.com/zh-tw/library/2549tw02.aspx
- https://msdn.microsoft.com/zh-tw/library/6x16t2tx.aspx