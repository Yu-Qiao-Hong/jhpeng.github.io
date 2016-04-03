---
layout: post
title: 'C# 建立並寫入二進制檔案資料'
author: 'James Peng'
tags: ['C#']
---

~~~csharp
        private void button2_Click(object sender, EventArgs e)
        {
            if (String.IsNullOrEmpty(textBox1.Text.Trim()))
            {
                MessageBox.Show("請選擇檔案路徑");
                return;
            }

            if (String.IsNullOrEmpty(textBox2.Text.Trim()))
            {
                MessageBox.Show("請設定檔案名稱");
                return;
            }

            try
            {
                FileStream myStream = new FileStream(textBox1.Text + "\\" + textBox2.Text + ".bin", FileMode.Create);
                BinaryWriter myWriter = new BinaryWriter(myStream);
                for (int i = 0; i < 10; i++)
                {
                    myWriter.Write(i);
                }
                myWriter.Close();
                myStream.Close();
                MessageBox.Show("建立並寫入成功！");
            }
            catch (Exception ex)
            {
                MessageBox.Show(ex.Message);
            }
        }
~~~


----------

參考：

- https://msdn.microsoft.com/zh-tw/library/system.io.binarywriter(v=vs.110).aspx

