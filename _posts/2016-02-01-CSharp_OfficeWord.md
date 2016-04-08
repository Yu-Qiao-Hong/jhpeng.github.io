---
layout: post
title: 'C# 透過 Microsoft.Office.Interop.Word 操作 Docx 文件'
author: 'James Peng'
tags: ['C#']
---

## 參考 ##

![](http://i.imgur.com/DtpIJPR.png)

MsOfficeWordAccessHelper.cs

~~~csharp
using DocumentFormat.OpenXml;
using DocumentFormat.OpenXml.Packaging;
using DocumentFormat.OpenXml.Wordprocessing;
using Microsoft.Office.Interop.Word;
using System;
using System.Collections.Generic;
using System.IO;
using System.Linq;
using System.Reflection;
using System.Text;
using System.Threading;
using System.Threading.Tasks;


namespace DataAccessComponents
{
    public class MsOfficeWordAccessHelper
    {
        private static WordReport report = new WordReport();


        public static void KillWinWordProcess()
        {
            System.Diagnostics.Process[] processes = System.Diagnostics.Process.GetProcessesByName("WINWORD");
            foreach (System.Diagnostics.Process process in processes)
            {
                if (process.MainWindowTitle.IndexOf("Microsoft Word") >=0 )
                {
                    process.Kill();
                }
            }
        }

        public static void KillWinWordTempFile(string path)
        {
            string wordPath = Path.GetDirectoryName(path);
            string[] files = Directory.GetFiles(wordPath);
            foreach (string file in files)
            {
                if (file.IndexOf("~$") >= 0)
                {
                    File.Delete(file);                    
                }
            }
        }


        public static void CopyWord(string templetPath, string savePath)
        {
            KillWinWordProcess();
            KillWinWordTempFile(templetPath);
            Thread.Sleep(10);
            report.Open(templetPath);
            report.SavedAs(savePath);
        }

        public static void InsertValue(string docPath, string tag, string strText)
        {
            
            report.Open(docPath);
            //report.InsertValueByBookmarks(tag, strText);
            report.InsertValueByString(tag, strText);
            report.SavedAs(docPath);
        }

        public static void InsertPicture(string docPath, string tag, string strPath)
        {
                       
            report.Open(docPath);
            System.Drawing.Image image = System.Drawing.Image.FromFile(strPath);
            int width = image.Width;
            int height = image.Height;
            report.InsertPictureByString(tag, strPath, width, height);
            report.SavedAs(docPath);
        }

        public static bool MergerWord(string[] arrCopies, string outDoc)
        {                              

            Object missing = Missing.Value;
            object oOutputDoc = outDoc;
            Microsoft.Office.Interop.Word.Application wordApp = new Microsoft.Office.Interop.Word.Application();
            object objTempDoc = arrCopies[0];
            wordApp.Documents.Open(ref objTempDoc,
                                                ref missing, ref missing, ref missing,
                                                ref missing, ref missing, ref missing,
                                                ref missing, ref missing, ref missing,
                                                ref missing, ref missing, ref missing,
                                                ref missing, ref missing, ref missing);
            wordApp.Application.Selection.EndKey(WdUnits.wdStory);
            
            object oPageBreak = Microsoft.Office.Interop.Word.WdBreakType.wdPageBreak;
            wordApp.Selection.InsertBreak(ref oPageBreak);
            wordApp.Application.Selection.EndKey(WdUnits.wdStory);

            string[] files = arrCopies;//Directory.GetFiles(sourcePath.Text.Trim());

           try
           {

            for (int iIdx = 1; iIdx < files.Length; iIdx++)
            {
                wordApp.Selection.InsertFile(files[iIdx], ref missing, ref missing, ref missing, ref missing);
                if (iIdx != files.Length - 1)
                {
                    wordApp.Selection.InsertBreak(ref oPageBreak);
                }
                wordApp.ActiveDocument.SaveAs(ref oOutputDoc,
                                                ref missing, ref missing, ref missing,
                                                ref missing, ref missing, ref missing,
                                                ref missing, ref missing, ref missing,
                                                ref missing, ref missing, ref missing,
                                                ref missing, ref missing, ref missing);
            }

            return true;
          }
          catch( Exception e)
          {
              e.ToString();
              return false;
          }
          finally
          {
                wordApp.Quit(
                  ref missing,     //SaveChanges
                  ref missing,     //OriginalFormat
                  ref missing      //RoutDocument
                  );
                wordApp = null;
          }

        }


        public static void HtmlToWord(string strOpenFileName, string strSaveFileName)
        {

            string inputFile = strOpenFileName;
            string outputFile = strSaveFileName;

            using (WordprocessingDocument myDoc =
                    WordprocessingDocument.Create(
                        outputFile, WordprocessingDocumentType.Document))
            {
                string altChunkId = "AltChunkId1";
                MainDocumentPart mainPart = myDoc.AddMainDocumentPart();
                mainPart.Document = new DocumentFormat.OpenXml.Wordprocessing.Document();
                mainPart.Document.Body = new Body();                
                var chunk = mainPart.AddAlternativeFormatImportPart(
                    AlternativeFormatImportPartType.Html, altChunkId);
                using (FileStream fileStream =
                        File.Open(inputFile, FileMode.Open))
                {
                    chunk.FeedData(fileStream);
                }
                AltChunk altChunk = new AltChunk() { Id = altChunkId };
                mainPart.Document.Append(altChunk);
                mainPart.Document.Save();
            }

        }


        public static void WordToText(string strOpenFileName, string strSaveFileName)
        {

            object openFileName = strOpenFileName;
            object saveFileName = strSaveFileName;
            object format = Microsoft.Office.Interop.Word.WdSaveFormat.wdFormatUnicodeText;
            object missing = System.Reflection.Missing.Value;

            Microsoft.Office.Interop.Word.Application myWord = new Microsoft.Office.Interop.Word.Application();
            myWord.Visible = false;
            myWord.Documents.Open(ref openFileName,
                            ref missing, ref missing, ref missing, ref missing, ref missing,
                            ref missing, ref missing, ref missing, ref missing, ref missing,
                            ref missing, ref missing, ref missing, ref missing, ref missing
                        );
            myWord.ActiveDocument.SaveAs(ref saveFileName, ref format,
                            ref missing, ref missing, ref missing, ref missing, ref missing,
                            ref missing, ref missing, ref missing, ref missing, ref missing,
                            ref missing, ref missing, ref missing, ref missing
                        );
            myWord.Quit(ref missing, ref missing, ref missing);
        }


        public static void WordToHtml(string strOpenFileName, string strSaveFileName)
        {

            object openFileName = strOpenFileName;     
            object saveFileName = strSaveFileName;    
            object format = Microsoft.Office.Interop.Word.WdSaveFormat.wdFormatHTML;    
            object missing = System.Reflection.Missing.Value;

            Microsoft.Office.Interop.Word.Application myWord = new Microsoft.Office.Interop.Word.Application();
            myWord.Visible = false;
            myWord.Documents.Open(ref openFileName,
                            ref missing, ref missing, ref missing, ref missing, ref missing,
                            ref missing, ref missing, ref missing, ref missing, ref missing,
                            ref missing, ref missing, ref missing, ref missing, ref missing
                        );
            myWord.ActiveDocument.SaveAs(ref saveFileName, ref format,
                            ref missing, ref missing, ref missing, ref missing, ref missing,
                            ref missing, ref missing, ref missing, ref missing, ref missing,
                            ref missing, ref missing, ref missing, ref missing
                        );
            myWord.Quit(ref missing, ref missing, ref missing);
        }



        public static void ExcelToHtml(string strOpenFileName, string strSaveFileName)
        {

            string copyPath = strOpenFileName;     
            string savePath = strSaveFileName;    
            object format = Microsoft.Office.Interop.Excel.XlFileFormat.xlHtml;  
            object missing = System.Reflection.Missing.Value;

            Microsoft.Office.Interop.Excel.Application myExcel = new Microsoft.Office.Interop.Excel.Application();
            myExcel.Visible = false;
            myExcel.Workbooks.Open(copyPath,
                        missing, missing, missing, missing, missing,
                        missing, missing, missing, missing, missing,
                        missing, missing, missing, missing
                    );
            myExcel.ActiveWorkbook.SaveAs(savePath, format,
                        null, null, false, false,
                        Microsoft.Office.Interop.Excel.XlSaveAsAccessMode.xlNoChange,
                        null, null, null, null, null
                    );
            myExcel.Quit();
        }


        /// <summary>
        /// Word文件轉PDF文件
        /// </summary>
        /// <param name="source">Word文件位置</param>
        /// <param name="target">PDF文件位置</param>
        /// <returns></returns>
        public static bool WordToPdf(string source, string target)
        {
            try
            {
                object missing = Missing.Value;
                var WordApp = new Microsoft.Office.Interop.Word.Application();
                Microsoft.Office.Interop.Word.Document doc = WordApp.Documents.Open(source);
                doc.SaveAs(target, Microsoft.Office.Interop.Word.WdSaveFormat.wdFormatPDF);
                WordApp.Visible = false;
                //WordApp.Quit();
                
                // Close the Word document, but leave the Word application open.
                // doc has to be cast to type _Document so that it will find the
                // correct Close method.                
                object saveChanges = WdSaveOptions.wdDoNotSaveChanges;
                ((_Document)doc).Close(ref saveChanges, ref missing, ref missing);                

                
                WordApp.Quit(ref missing, ref missing, ref missing);
                return true;
            }
            catch (Exception ex)
            {
                Console.WriteLine(ex.Message);
            }
            return false;
        }

        /// <summary>
        /// Excel文件轉PDF文件
        /// </summary>
        /// <param name="source">Excel文件位置</param>
        /// <param name="target">PDF文件位置</param>
        /// <returns></returns>
        public static bool ExcelToPdf(string source, string target)
        {
            try
            {
                var ExcelApp = new Microsoft.Office.Interop.Excel.Application();
                Microsoft.Office.Interop.Excel.Workbook book = ExcelApp.Workbooks.Open(source);
                Microsoft.Office.Interop.Excel.XlFileFormat xlFormatPDF = (Microsoft.Office.Interop.Excel.XlFileFormat)57;
                book.SaveAs(target, xlFormatPDF);
                ExcelApp.Visible = false;
                ExcelApp.Quit();
                return true;
            }
            catch (Exception ex)
            {
                Console.WriteLine(ex.Message);
            }
            return false;
        }

        /// <summary>
        /// PowerPoint文件轉PDF文件
        /// </summary>
        /// <param name="source">PowerPoint文件位置</param>
        /// <param name="target">PDF文件位置</param>
        /// <returns></returns>
        public static bool PowerPointToPdf(string source, string target)
        {
            try
            {
                var PowerPointApp = new Microsoft.Office.Interop.PowerPoint.Application();
                Microsoft.Office.Interop.PowerPoint.Presentation presentation = PowerPointApp.Presentations.Open(source, Microsoft.Office.Core.MsoTriState.msoFalse, Microsoft.Office.Core.MsoTriState.msoFalse, Microsoft.Office.Core.MsoTriState.msoFalse);
                presentation.SaveAs(target, Microsoft.Office.Interop.PowerPoint.PpSaveAsFileType.ppSaveAsPDF);
                PowerPointApp.Quit();
                System.Runtime.InteropServices.Marshal.FinalReleaseComObject(PowerPointApp);
                return true;
            }
            catch (Exception ex)
            {
                Console.WriteLine(ex.Message);
            }
            return false;
        }

    }
}

~~~



