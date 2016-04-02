---
layout: post
title: 'C# 使用 正規表達式 Regex 驗證'
author: 'James Peng'
tags: ['C#']
---

## 驗證輸入是否為數字 ##

~~~csharp
        /// <summary>
        /// 驗證輸入是否為數字
        /// </summary>
        /// <param name="str_number">用戶輸入的字串</param>
        /// <returns>方法返回布爾值</returns>
        public bool IsNumber(string str_number)
        {
            return System.Text.RegularExpressions.Regex.//使用正則表達式判斷是否匹配
                IsMatch(str_number, @"^[0-9]*$");
        }
~~~

----------

## 驗證輸入是否為非零正整數 ##

~~~csharp
        /// <summary>
        /// 驗證輸入是否為非零正整數
        /// </summary>
        /// <param name="str_intNumber">用戶輸入的數值</param>
        /// <returns>方法返回布林值</returns>
        public bool IsIntNumber(string str_intNumber)
        {
            return System.Text.RegularExpressions.Regex.//使用正規化運算式判斷是否符合
                IsMatch(str_intNumber, @"^\+?[1-9][0-9]*$");
        }
~~~

----------


## 驗證輸入是否為非零負整數 ##

~~~csharp
        /// <summary>
        /// 驗證輸入是否為非零負整數
        /// </summary>
        /// <param name="str_intNumber">用戶輸入的數值</param>
        /// <returns>方法返回布林值</returns>
        public bool IsIntNumber(string str_intNumber)
        {
            return System.Text.RegularExpressions.Regex.//使用正規劃運算式判斷是否符合
                IsMatch(str_intNumber, @"^\-[1-9][0-9]*$");
        }
~~~

----------


## 長度為6-18位 ##

~~~csharp
        /// <summary>
        /// 驗證密碼長度是否正確
        /// </summary>
        /// <param name="str_Length">密碼字串</param>
        /// <returns>方法返回布林值</returns>
        public bool IsPasswLength(string str_Length)
        {
            return System.Text.RegularExpressions.Regex.//使用正規化運算式判斷是否符合
                IsMatch(str_Length, @"^\d{6,18}$");
        }
~~~

----------


## 小數點兩位 ##

~~~csharp
        /// <summary>
        /// 驗證小數是否正確
        /// </summary>
        /// <param name="str_decimal">小數字串</param>
        /// <returns>返回布爾值</returns>
        public bool IsDecimal(string str_decimal)
        {
            return System.Text.RegularExpressions.Regex.//使用正則表達式判斷是否匹配
                IsMatch(str_decimal, @"^[0-9]+(.[0-9]{2})?$");
        }
~~~


----------

## 驗證月份是否正確 ##

~~~csharp
        /// <summary>
        /// 驗證月份是否正確
        /// </summary>
        /// <param name="str_Month">月份訊息字串</param>
        /// <returns>返回布爾值</returns>
        public bool IsMonth(string str_Month)
        {
            return System.Text.RegularExpressions.Regex.//使用正則表達式判斷是否匹配
                IsMatch(str_Month, @"^(0?[[1-9]|1[0-2])$");
        }
~~~


----------


## 驗證每月的31天 ##

~~~csharp
        /// <summary>
        /// 驗證每月的31天
        /// </summary>
        /// <param name="str_day">每月的天數</param>
        /// <returns>返回布爾值</returns>
        public bool IsDay(string str_day)
        {
            return System.Text.RegularExpressions.Regex.//使用正則表達式判斷是否匹配
                IsMatch(str_day, @"^((0?[1-9])|((1|2)[0-9])|30|31)$");
        }
~~~


----------


## 驗證輸入字符是否為大寫字母 ##

~~~csharp

        /// <summary>
        /// 驗證輸入字符是否為大寫字母
        /// </summary>
        /// <param name="str_UpChar">用戶輸入的字串</param>
        /// <returns>方法返回布林值</returns>
        public bool IsUpChar(string str_UpChar)
        {
            return System.Text.RegularExpressions.Regex.//使用正規化運算式判斷是否符合
                IsMatch(str_UpChar, @"^[A-Z]+$");
        }
~~~


----------


## 驗證輸入字符是否為小寫字母 ##

~~~csharp
        /// <summary>
        /// 驗證輸入字符是否為小寫字母
        /// </summary>
        /// <param name="str_UpChar">用戶輸入的字串</param>
        /// <returns>方法返回布林值</returns>
        public bool IsUpChar(string str_UpChar)
        {
            return System.Text.RegularExpressions.Regex.//使用正規化運算式判斷是否匹配
                IsMatch(str_UpChar, @"^[a-z]+$");
        }
~~~