---
layout: post
title: 'C# Thread 執行緒的建立、啟動和結束'
author: 'James Peng'
tags: ['C#']
---

# 建立、啟動和結束執行緒 #

## 參考 ##

~~~csharp
 using System.Threading;
~~~

## 在執行緒啟動時會呼叫這個方法 ##

~~~csharp
public class Worker
{
    // 在執行緒啟動時會呼叫這個方法。
    public void DoWork()
    {
        while (!_shouldStop)
        {
            Console.WriteLine("worker thread: working...");
        }
        Console.WriteLine("worker thread: terminating gracefully.");
    }
    public void RequestStop()
    {
        _shouldStop = true;
    }
    // 使用 Volatile 做為編譯器的提示，
    // 這樣就可以讓多個執行緒存取這個資料成員。
    private volatile bool _shouldStop;
}
~~~

## 建立執行緒 ##

~~~csharp
        // 建立 Thread 物件。這樣並不會啟動執行緒。
        Worker workerObject = new Worker();
        Thread workerThread = new Thread(workerObject.DoWork);
~~~

## 啟動執行緒 ##

~~~csharp
        // 啟動背景工作執行緒。
        workerThread.Start();
        Console.WriteLine("main thread: Starting worker thread...");

        // 執行迴圈，直到背景工作執行緒啟動。
        while (!workerThread.IsAlive);

        // 讓 Main 執行緒進入休眠狀態 1 毫秒，
        // 以便執行緒執行某些工作:
        Thread.Sleep(1);
~~~

## 結束執行緒 ##

~~~csharp
        // 要求背景工作執行緒自行停止:
        workerObject.RequestStop();

        // 在物件的執行緒結束前，使用 Join 方法 
        // 來封鎖目前的執行緒。
        workerThread.Join();
        Console.WriteLine("main thread: Worker thread has terminated.");
~~~

## 執行結果 ##

~~~text
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
main thread: Starting worker thread...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: working...
worker thread: terminating gracefully.
main thread: Worker thread has terminated.
請按任意鍵繼續 . . .
~~~


----------

參考：

- https://code.msdn.microsoft.com/Threading-Sample-bc441f8e/file/46647/2/%E5%9F%B7%E8%A1%8C%E7%B7%92%E8%99%95%E7%90%86%E7%AF%84%E4%BE%8B.zip
- https://code.msdn.microsoft.com/Threading-Sample-bc441f8e
- https://msdn.microsoft.com/zh-tw/library/5xt1dysy(v=vs.90).aspx
