---
title: WebBrowserControl.GridlineTint property (Access)
keywords: vbaac10.chm14636
f1_keywords:
- vbaac10.chm14636
ms.prod: access
api_name:
- Access.WebBrowserControl.GridlineTint
ms.assetid: b5d2c928-bfa7-6510-a5c8-3ce0ce380375
ms.date: 02/14/2019
ms.localizationpriority: medium
---


# WebBrowserControl.GridlineTint property (Access)

Gets or sets the tint applied to the theme color in the **[GridlineColor](access.WebBrowserControl.gridlinecolor.md)** property of the specified object. Read/write **Single**.


## Syntax

_expression_.**GridlineTint**

_expression_ A variable that represents a **[WebBrowserControl](Access.WebBrowserControl.md)** object.


## Remarks

The **GridlineTint** property contains a numeric expression that can be used to lighten the theme color in the **GridlineColor** property. The default value of the **GridlineTint** property is 100, which is neutral, and does not change the theme color. 

To lighten the color, first determine the percentage by which to lighten from 1 to 100, and then subtract that value as a whole number from 100 and use the remainder. For example, to lighten the theme color tint by 75%, subtract 75 from 100 and use the remainder, which is 25.

This property is not surfaced in the property sheet.




[!include[Support and feedback](~/includes/feedback-boilerplate.md)]