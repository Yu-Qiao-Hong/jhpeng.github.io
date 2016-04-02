---
layout: post
title: '系統功能表中新增功能表項目'
author: 'James Peng'
tags: ['Visual C++']
---

![](http://i.imgur.com/uDdZkwz.png)


![](http://i.imgur.com/vK59BxS.png)


## OnInitDialog() ##

~~~cpp
	m_pMenu = GetSystemMenu(FALSE);
	m_pMenu->AppendMenu(MF_STRING,IDI_PECULIARMENU,"系統功能表");
~~~


## OnSysCommand ##

~~~cpp
void CPeculiarMenuDlg::OnSysCommand(UINT nID, LPARAM lParam)
{
	if ((nID ) == IDM_ABOUTBOX)
	{
		CAboutDlg dlgAbout;
		dlgAbout.DoModal();
	}
	else if (nID == IDI_PECULIARMENU)
	{
			MessageBox("系統功能表","提示",MB_OK|MB_ICONINFORMATION);
	}
	else
	{
		CDialog::OnSysCommand(nID, lParam);
	}
}
~~~