---
title: ListBox.BorderWidth property (Access)
keywords: vbaac10.chm11249
f1_keywords:
- vbaac10.chm11249
ms.prod: access
api_name:
- Access.ListBox.BorderWidth
ms.assetid: 3e0ddff1-7e60-5fbd-7680-6d9da7baead8
ms.date: 02/20/2019
ms.localizationpriority: medium
---


# ListBox.BorderWidth property (Access)

Use the **BorderWidth** property to specify the width of a control's border. Read/write **Byte**.


## Syntax

_expression_.**BorderWidth**

_expression_ A variable that represents a **[ListBox](Access.ListBox.md)** object.


## Remarks

The **BorderWidth** property uses the following settings.

|Setting|Visual Basic|Description|
|:-----|:-----|:-----|
|Hairline|0|(Default) The narrowest border possible on your system.|
|1 pt to 6 pt|1 to 6|The width as indicated in points.|

You can set the default for this property by using the control's default control style or the **[DefaultControl](access.form.defaultcontrol.md)** property in Visual Basic.

To use the **BorderWidth** property, the **SpecialEffect** property must be set to Flat or Shadowed, and the **BorderStyle** property must not be set to Transparent. If the **SpecialEffect** property is set to any other value, and/or the **BorderStyle** property is set to Transparent, and you set the **BorderWidth** property, the **SpecialEffect** property is automatically reset to Flat, and the **BorderStyle** property is automatically reset to Solid.

The exact border width depends on your computer and printer. On some systems, the hairline and 1-point widths appear the same.




[!include[Support and feedback](~/includes/feedback-boilerplate.md)]