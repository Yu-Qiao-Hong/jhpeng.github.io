---
layout: post
title: 'C# 讀寫 INI'
author: 'James Peng'
tags: ['C#']
---

## INI取值 ##

~~~csharp
private string strSection = "Ethernet";
string m_strSocketIpAddress = IniAccessHelper.GetKeyValue(strInifileName, strSection, "m_strSocketIpAddress", "0.0.0.0");
            }
~~~


----------


## INI寫值 ##

~~~csharp
IniAccessHelper.SetKeyValue(strInifileName, strSection, "m_iSocketPort", value.ToString());
            }
~~~

----------


## IniAccessHelper.cs ##

~~~csharp

    public class IniAccessHelper
    {
        public GeneralSetting General;
        public LogSetting Log;
        public GpioSetting Gpio;
        public GpibSetting Gpib;
        public EthernetSetting Ethernet;

        private static string _FilePath = string.Empty;
        //private static string INI_NAME = string.Empty;


        public IniAccessHelper(string strName)
        {
           // INI_NAME = strName;

            string dirPath = "INI";
            bool bINI = Directory.Exists(dirPath);
            if (!bINI)
            {
                Directory.CreateDirectory(dirPath);
            }

            General = new GeneralSetting(strName);
            Log = new LogSetting(strName);
            Gpio = new GpioSetting(strName);
            Gpib = new GpibSetting(strName);
            Ethernet = new EthernetSetting(strName);
        }

        //TestCase INI

        [DllImport("kernel32")]
        private static extern long WritePrivateProfileString(string section, string key, string val, string filePath);
        [DllImport("kernel32")]
        private static extern int GetPrivateProfileString(string section, string key, string def, StringBuilder retVal, int size, string filePath);


        public static bool SetIniFileName(string strIniFile)
        {
            _FilePath = System.Windows.Forms.Application.StartupPath + "\\INI" + strIniFile;
            return File.Exists(_FilePath);
        }

        public static void SetKeyValue(string INI_NAME, string strSection, string strKey, string strValue)
        {
            if (_FilePath == string.Empty) SetIniFileName(INI_NAME);

            WritePrivateProfileString(strSection, strKey, strValue, _FilePath);
        }


        public static string GetKeyValue(string INI_NAME, string strSection, string strKey)
        {
            if (_FilePath == string.Empty) SetIniFileName(INI_NAME);

            StringBuilder temp = new StringBuilder(255);
            int i = GetPrivateProfileString(strSection, strKey, "", temp, 255, _FilePath);
            return temp.ToString();
        }



        public static string GetKeyValue(string INI_NAME, string Section, string Key, string DefaultValue)
        {
            if (_FilePath == string.Empty) SetIniFileName(INI_NAME);

            StringBuilder sbResult = null;
            try
            {
                sbResult = new StringBuilder(255);
                GetPrivateProfileString(Section, Key, "", sbResult, 255, _FilePath);
                return (sbResult.Length > 0) ? sbResult.ToString() : DefaultValue;
            }
            catch
            {
                return string.Empty;
            }
        }
    }
~~~