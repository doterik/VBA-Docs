---
title: TextStyles.Count property (Publisher)
keywords: vbapb10.chm5898243
f1_keywords:
- vbapb10.chm5898243
ms.prod: publisher
api_name:
- Publisher.TextStyles.Count
ms.assetid: c8620d07-d5ad-68f6-67c6-0179da441a4c
ms.date: 06/15/2019
ms.localizationpriority: medium
---


# TextStyles.Count property (Publisher)

Returns a **Long** that represents the number of items in the specified collection.


## Syntax

_expression_.**Count**

_expression_ A variable that represents a **[TextStyles](Publisher.TextStyles.md)** object.


## Example

This example displays the number of pages in the active document.

```vb
Sub CountNumberOfPages() 
 MsgBox "Your publication contains " & _ 
 ActiveDocument.Pages.Count & " page(s)." 
End Sub
```

<br/>

This example displays the number of shapes in the active document.

```vb
Sub CountNumberOfShapes() 
 Dim intShapes As Integer 
 Dim pg As Page 
 
 For Each pg In ActiveDocument.Pages 
 intShapes = intShapes + pg.Shapes.Count 
 Next 
 
 MsgBox "Your publication contains " & intShapes & " shape(s)." 
End Sub
```

[!include[Support and feedback](~/includes/feedback-boilerplate.md)]