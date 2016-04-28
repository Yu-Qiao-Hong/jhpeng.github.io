---
layout: post
title: 'C# 取得磁碟剩餘空間'
author: 'James Peng'
tags: ['C#']
---


## 取得磁碟剩餘空間 ##

~~~csharp

        [DllImport("kernel32.dll")]
        private static extern bool GetDiskFreeSpaceEx(
        string lpDirectoryName, out ulong lpFreeBytesAvailable, out ulong lpTotalNumberOfBytes, out ulong lpTotalNumberOfFreeBytes);

        /// <summary>
        /// 取得磁碟剩餘空間
        /// </summary>
        /// <param name="driveDirectoryName">驅動器名 C:\ </param>
        /// <param name="SizeTag">gb mb kb</param>
        /// <returns>剩餘空間</returns>
        private static ulong GetFreeSpace(string driveDirectoryName, string SizeTag = "byte" )
        {
            ulong freeBytesAvailable, totalNumberOfBytes, totalNumberOfFreeBytes;
            if (!driveDirectoryName.EndsWith(":\\"))
            {
                driveDirectoryName += ":\\";
            }
            GetDiskFreeSpaceEx(driveDirectoryName, out freeBytesAvailable, out totalNumberOfBytes, out totalNumberOfFreeBytes);

            if (SizeTag.ToLower() == "kb")
            {
                return (freeBytesAvailable/1024);
            }
            else if (SizeTag.ToLower() == "mb")
            {
                return (freeBytesAvailable / 1024 /1024);
            }
            else if (SizeTag.ToLower() == "gb")
            {
                return (freeBytesAvailable /1024 / 1024 / 1024);
            }
            else
            {
                return freeBytesAvailable;
            }
            
        }
~~~


----------


## 用法 ##

~~~csharp
        private void button1_Click(object sender, EventArgs e)
        {
            MessageBox.Show(GetFreeSpace(@"c:\", "gb").ToString() + " GB");

            MessageBox.Show(GetFreeSpace(@"c:\", "mb").ToString() + " MB");

            MessageBox.Show(GetFreeSpace(@"c:\", "kb").ToString() + " KB");

            MessageBox.Show(GetFreeSpace(@"c:\").ToString() + " Byte");
        }
~~~

![](http://i.imgur.com/dGXILFY.png)

![](http://i.imgur.com/TCsiokP.png)

![](http://i.imgur.com/YclLB7q.png)

![](http://i.imgur.com/X2mjmfn.png)

----------

參考：

- http://fecbob.pixnet.net/blog/post/36367042