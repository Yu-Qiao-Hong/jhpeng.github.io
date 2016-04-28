---
layout: post
title: 'C# DevExpress 使用 TreeList 心得'
author: 'James Peng'
tags: ['C#']
---

![](http://i.imgur.com/IiZ8yoM.png)

![](http://i.imgur.com/ZxUr1ja.png)



----------


## 加入 命名空間 ##

~~~csharp
using DevExpress.XtraTreeList.Columns;
using DevExpress.XtraTreeList.Nodes;
~~~

----------

## 清除 ##

~~~csharp             
                treeList.BeginUnboundLoad();
                treeList.Nodes.Clear();
                treeList.Columns.Clear();
~~~


----------


## 設定標題 ##

~~~csharp
           TreeListColumn col;

            // columns
            col = treeList.Columns.Add();
            col.Name = "col_Parameter";
            col.Caption = "Parameter";
            col.Visible = true;
            col.OptionsColumn.AllowSort = false;
            col.OptionsColumn.AllowEdit = false;

            col = treeList.Columns.Add();
            col.Name = "col_Unit";
            col.Caption = "Unit";
            col.Visible = true;
            col.OptionsColumn.AllowSort = false;
            col.OptionsColumn.AllowEdit = false;

            col = treeList.Columns.Add();
            col.Name = "col_Address";
            col.Caption = "Address";
            col.Visible = true;
            col.OptionsColumn.AllowSort = false;
            col.OptionsColumn.AllowEdit = false;

            col = treeList.Columns.Add();
            col.Name = "col_SeetingValue";
            col.Caption = "Seeting Value";
            col.Visible = true;
            col.OptionsColumn.AllowSort = false;
            col.OptionsColumn.AllowEdit = false;

            col = treeList.Columns.Add();
            col.Name = "col_Default";
            col.Caption = "Default";
            col.Visible = true;
            col.OptionsColumn.AllowSort = false;
            col.OptionsColumn.AllowEdit = false;

            col = treeList.Columns.Add();
            col.Name = "col_Minimum";
            col.Caption = "Minimum";
            col.Visible = true;
            col.OptionsColumn.AllowSort = false;
            col.OptionsColumn.AllowEdit = false;

            col = treeList.Columns.Add();
            col.Name = "col_Maximum";
            col.Caption = "Maximum";
            col.Visible = true;
            col.OptionsColumn.AllowSort = false;
            col.OptionsColumn.AllowEdit = false;
           
     
~~~

![](http://i.imgur.com/F9lfLeR.png)

----------


## 加入樹狀資料 ##


~~~csharp
            TreeListNode ident = treeList.AppendNode(new object[] {  "INDENTI", "" }, null);
            ident.Tag = "root";
            ident.Nodes.Add( "VENDOR", "");
            ident.Nodes.Add( "PROD_TYPE", "");
            ident.Nodes.Add( "PROD_NAME", "");
            ident.Nodes.Add( "REVISION", "");
           
     
~~~

![](http://i.imgur.com/IBBLKQa.png)


----------

## 展開 ##

~~~csharp
                treeList.ExpandAll();
                treeList.EndUnboundLoad();
~~~


----------




