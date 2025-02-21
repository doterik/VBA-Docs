---
title: Range.Find method (Excel)
keywords: vbaxl10.chm144128
f1_keywords:
- vbaxl10.chm144128
ms.prod: excel
api_name:
- Excel.Range.Find
ms.assetid: d9585265-8164-cb4d-a9e3-262f6e06b6b8
ms.date: 08/14/2019
ms.localizationpriority: high
---


# Range.Find method (Excel)

Finds specific information in a range.

[!include[Add-ins note](~/includes/addinsnote.md)]

## Syntax

_expression_.**Find** (_What_, _After_, _LookIn_, _LookAt_, _SearchOrder_, _SearchDirection_, _MatchCase_, _MatchByte_, _SearchFormat_)

_expression_ A variable that represents a **[Range](excel.range(object).md)** object.


## Parameters

|Name|Required/Optional|Data type|Description|
|:-----|:-----|:-----|:-----|
| _What_|Required| **Variant**|The data to search for. Can be a string or any Microsoft Excel data type.|
| _After_|Optional| **Variant**|The cell after which you want the search to begin. This corresponds to the position of the active cell when a search is done from the user interface.<br/><br/>Notice that _After_ must be a single cell in the range. Remember that the search begins after this cell; the specified cell isn't searched until the method wraps back around to this cell.<br/><br/>If you don't specify this argument, the search starts after the cell in the upper-left corner of the range.|
| _LookIn_|Optional| **Variant**|Can be one of the following **[XlFindLookIn](excel.xlfindlookin.md)** constants: **xlFormulas**, **xlValues**, **xlComments**, or **xlCommentsThreaded**.|
| _LookAt_|Optional| **Variant**|Can be one of the following **[XlLookAt](excel.xllookat.md)** constants: **xlWhole** or **xlPart**.|
| _SearchOrder_|Optional| **Variant**|Can be one of the following **[XlSearchOrder](excel.xlsearchorder.md)** constants: **xlByRows** or **xlByColumns**.|
| _SearchDirection_|Optional| **Variant** |Can be one of the following **[XlSearchDirection](Excel.xlSearchDirection.md)** constants: **xlNext** or **xlPrevious**.|
| _MatchCase_|Optional| **Variant**| **True** to make the search case-sensitive. The default value is **False**.|
| _MatchByte_|Optional| **Variant**|Used only if you have selected or installed double-byte language support. **True** to have double-byte characters match only double-byte characters. **False** to have double-byte characters match their single-byte equivalents.|
| _SearchFormat_|Optional| **Variant**|The search format.|

## Return value

A **Range** object that represents the first cell where that information is found.


## Remarks

This method returns **Nothing** if no match is found. The **Find** method does not affect the selection or the active cell.

The settings for _LookIn_,  _LookAt_,  _SearchOrder_, and _MatchByte_ are saved each time you use this method. If you don't specify values for these arguments the next time you call the method, the saved values are used. Setting these arguments changes the settings in the **Find** dialog box, and changing the settings in the **Find** dialog box changes the saved values that are used if you omit the arguments. To avoid problems, set these arguments explicitly each time you use this method.

Use the **[FindNext](Excel.Range.FindNext.md)** and **[FindPrevious](Excel.Range.FindPrevious.md)** methods to repeat the search.

When the search reaches the end of the specified search range, it wraps around to the beginning of the range. To stop a search when this wraparound occurs, save the address of the first found cell, and then test each successive found-cell address against this saved address.

To find cells that match more complicated patterns, use a **For Each...Next** statement with the **Like** operator. For example, the following code searches for all cells in the range A1:C5 that use a font whose name starts with the letters Cour. When Microsoft Excel finds a match, it changes the font to Times New Roman.

```vb
For Each c In [A1:C5] If c.Font.Name Like "Cour*" Then c.Font.Name = "Times New Roman" End If Next`

```

## Examples

This example finds all cells in the range A1:A500 in worksheet one that contain the value 2, and changes the entire cell value to 5. That is, the values 1234 and 99299 both contain 2 and both cell values will become 5.

```vb
Sub FindValue()
    
    Dim c As Range
    Dim firstAddress As String

    With Worksheets(1).Range("A1:A500") 
        Set c = .Find(2, lookin:=xlValues) 
        If Not c Is Nothing Then 
            firstAddress = c.Address 
            Do 
                c.Value = 5 
                Set c = .FindNext(c) 
            Loop While Not c Is Nothing
        End If 
    End With
    
End Sub
```

This example finds all cells in the range A1:A500 on worksheet one that contain the substring "abc" and then replaces "abc" with "xyz".

```vb
Sub FindString()

    Dim c As Range
    Dim firstAddress As String

    With Worksheets(1).Range("A1:A500")
        Set c = .Find("abc", LookIn:=xlValues)
        If Not c Is Nothing Then
            firstAddress = c.Address
            Do
                c.Value = Replace(c.Value, "abc", "xyz")
                Set c = .FindNext(c)
            Loop While Not c Is Nothing
        End If
    End With

End Sub
```


<!-- ******Removed this sample by request in this Issue: https://github.com/MicrosoftDocs/VBA-Docs/issues/133******

**Sample code provided by:** Holy Macro! Books, [Holy Macro! It's 2,500 Excel VBA Examples](https://www.mrexcel.com/store/index.php?l=product_detail&p=1).

This example takes a path and name of a workbook and a search term, and searches the specified workbook for the search term. If the search term is found, the address of the result is stored in cell D10 of the current workbook.

```vb
Option Explicit

Sub FindAddress()
    'Defining the variables.
    Dim GCell As Range
    Dim Page$, Txt$, MyPath$, MyWB$, MySheet$
    
    
    'The text for which to search.
    Txt = "Hello"
    'The path to the workbook in which to search.
    MyPath = "C:\Your\File\Path\"
    'The name of the workbook in which to search.
    MyWB = "YourFileName.xls"
    
    'Use the current sheet as the place to store the data for which to search.
    MySheet = ActiveSheet.Name
    
    'If an error occurs, use the error handling routine at the end of this file.
    On Error GoTo ErrorHandler
   
    'Turn off screen updating, and then open the target workbook.
    Application.ScreenUpdating = False
    Workbooks.Open FileName:=MyPath & MyWB
    
    'Search for the specified text
    Set GCell = ActiveSheet.Cells.Find(Txt)
    
    'Record the address of the data, along with the date, in the current workbook.
    With ThisWorkbook.ActiveSheet.Range("D10")
        .Value = "Address of " & Txt & ":"
        .Offset(0, 1).Value = "Date:"
        .Offset(1, 0).Value = GCell.Address
        .Offset(1, 1).Value = Date
        .Columns.AutoFit
        .Offset(1, 1).Columns.AutoFit
    End With
    
    'Close the data workbook, without saving any changes, and turn screen updating back on.
    ActiveWorkbook.Close savechanges:=False
    Application.ScreenUpdating = True
Exit Sub

'Error Handling section.
ErrorHandler:
Select Case Err.Number
        'Common error #1: file path or workbook name is wrong.
        Case 1004
            Range("D10:E11").ClearContents
            Application.ScreenUpdating = True
            MsgBox "The workbook " & MyWB & " could not be found in the path" & vbCrLf & MyPath & "."
        Exit Sub
        
        'Common error #2: the specified text wasn't in the target workbook.
        Case 9, 91
            ThisWorkbook.Sheets(MySheet).Range("D10:E11").ClearContents
            Workbooks(MyWB).Close False
            Application.ScreenUpdating = True
            MsgBox "The value " & Txt & " was not found."
        Exit Sub
        
        'General case: turn screenupdating back on, and exit.
        Case Else
            Application.ScreenUpdating = True
        Exit Sub
End Select

End Sub
```


### About the contributor

Holy Macro! Books publishes entertaining books for people who use Microsoft Office. See the complete catalog at MrExcel.com. -->



[!include[Support and feedback](~/includes/feedback-boilerplate.md)]
