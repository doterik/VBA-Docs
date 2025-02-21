---
title: TextRange.Font property (Publisher)
keywords: vbapb10.chm5308419
f1_keywords:
- vbapb10.chm5308419
ms.prod: publisher
api_name:
- Publisher.TextRange.Font
ms.assetid: c5795f33-4e7b-f765-9ba8-f5b6706561d6
ms.date: 06/15/2019
ms.localizationpriority: medium
---


# TextRange.Font property (Publisher)

Sets or returns a **[Font](Publisher.Font.md)** object that represents character formatting attributes applied to the specified object. Read/write.


## Syntax

_expression_.**Font**

_expression_ A variable that represents a **[TextRange](Publisher.TextRange.md)** object.


## Example

This example selects text and formats the font as bold.

```vb
Sub test2() 
 With Selection.TextRange 
 .Start = 50 
 .End = 150 
 .Font.Bold = msoTrue 
 End With 
End Sub
```

[!include[Support and feedback](~/includes/feedback-boilerplate.md)]