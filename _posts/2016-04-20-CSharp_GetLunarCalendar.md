---
layout: post
title: 'C# 取得對應日期的農曆'
author: 'James Peng'
tags: ['C#']
---


## 取得對應日期的農曆 ##

~~~csharp

        /// <summary>
        /// 獲取對應日期的農曆
        /// </summary>
        /// <param name="dtDay">西曆日期</param>
        /// <returns></returns>
        public string GetLunarCalendar(DateTime dtDay)
        {

            //天干
            string[] TianGan = { "甲", "乙", "丙", "丁", "戊", "己", "庚", "辛", "壬", "癸" };

            //地支
            string[] DiZhi = { "子", "醜", "寅", "卯", "辰", "巳", "午", "未", "申", "酉", "戌", "亥" };

            //十二生肖
            string[] ShengXiao = { "鼠", "牛", "虎", "兔", "龍", "蛇", "馬", "羊", "猴", "雞", "狗", "豬" };

            //農曆日期
            string[] DayName = {"*","初一","初二","初三","初四","初五",
                                "初六","初七","初八","初九","初十",
                                "十一","十二","十三","十四","十五",
                                "十六","十七","十八","十九","二十",
                                "廿一","廿二","廿三","廿四","廿五",
                                "廿六","廿七","廿八","廿九","三十"};

            //農曆月份
            string[] MonthName = { "*", "正", "二", "三", "四", "五", "六", "七", "八", "九", "十", "十一", "臘" };

            //西曆月計數天
            int[] MonthAdd = { 0, 31, 59, 90, 120, 151, 181, 212, 243, 273, 304, 334 };

            //農曆資料
            int[] LunarData = {2635,333387,1701,1748,267701,694,2391,133423,1175,396438
                                ,3402,3749,331177,1453,694,201326,2350,465197,3221,3402
                                ,400202,2901,1386,267611,605,2349,137515,2709,464533,1738
                                ,2901,330421,1242,2651,199255,1323,529706,3733,1706,398762
                                ,2741,1206,267438,2647,1318,204070,3477,461653,1386,2413
                                ,330077,1197,2637,268877,3365,531109,2900,2922,398042,2395
                                ,1179,267415,2635,661067,1701,1748,398772,2742,2391,330031
                                ,1175,1611,200010,3749,527717,1452,2742,332397,2350,3222
                                ,268949,3402,3493,133973,1386,464219,605,2349,334123,2709
                                ,2890,267946,2773,592565,1210,2651,395863,1323,2707,265877};


            string sYear = dtDay.Year.ToString();
            string sMonth = dtDay.Month.ToString();
            string sDay = dtDay.Day.ToString();
            int year;
            int month;
            int day;
            try
            {
                year = int.Parse(sYear);
                month = int.Parse(sMonth);
                day = int.Parse(sDay);
            }
            catch
            {
                year = DateTime.Now.Year;
                month = DateTime.Now.Month;
                day = DateTime.Now.Day;
            }

            int nTheDate;
            int nIsEnd;
            int k, m, n, nBit, i;
            string calendar = string.Empty;
            //計算到初始時間1921年2月8日的天數：1921-2-8(正月初一)
            nTheDate = (year - 1921) * 365 + (year - 1921) / 4 + day + MonthAdd[month - 1] - 38;
            if ((year % 4 == 0) && (month > 2))
                nTheDate += 1;
            //計算天干，地支，月，日
            nIsEnd = 0;
            m = 0;
            k = 0;
            n = 0;
            while (nIsEnd != 1)
            {
                if (LunarData[m] < 4095)
                    k = 11;
                else
                    k = 12;
                n = k;
                while (n >= 0)
                {
                    //獲取LunarData[m]的第n個二進位位的值
                    nBit = LunarData[m];
                    for (i = 1; i < n + 1; i++)
                        nBit = nBit / 2;
                    nBit = nBit % 2;
                    if (nTheDate <= (29 + nBit))
                    {
                        nIsEnd = 1;
                        break;
                    }
                    nTheDate = nTheDate - 29 - nBit;
                    n = n - 1;
                }
                if (nIsEnd == 1)
                    break;
                m = m + 1;
            }
            year = 1921 + m;
            month = k - n + 1;
            day = nTheDate;
            //return year + "-" + month + "-" + day;

            if (k == 12)
            {
                if (month == LunarData[m] / 65536 + 1)
                    month = 1 - month;
                else if (month > LunarData[m] / 65536 + 1)
                    month = month - 1;
            }
            //年
            calendar = year + "年";
            //生肖
            calendar += ShengXiao[(year - 4) % 60 % 12].ToString() + "年 ";
            // //天干
            calendar += TianGan[(year - 4) % 60 % 10].ToString();
            // //地支
            calendar += DiZhi[(year - 4) % 60 % 12].ToString() + " ";

            //農曆月
            if (month < 1)
                calendar += "閏" + MonthName[-1 * month].ToString() + "月";
            else
                calendar += MonthName[month].ToString() + "月";

            //農曆日
            calendar += DayName[day].ToString() + "日";

            return calendar;

        }
~~~


----------


## 用法 ##

~~~csharp
        private void button1_Click(object sender, EventArgs e)
        {
            MessageBox.Show(GetLunarCalendar(DateTime.Now));
        }
~~~

![](..\images\2016-04-20-CSharp_GetLunarCalendar\9kzMmX5.png)

----------

參考：

- http://fecbob.pixnet.net/blog/post/38088813
- http://www.nongli.info/
