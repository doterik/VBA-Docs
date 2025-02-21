---
title: TabControl.MultiRow property (Access)
keywords: vbaac10.chm12086
f1_keywords:
- vbaac10.chm12086
ms.prod: access
api_name:
- Access.TabControl.MultiRow
ms.assetid: b5c3a830-d0df-7cbc-c83b-4b93bced8cd7
ms.date: 03/26/2019
ms.localizationpriority: medium
---


# TabControl.MultiRow property (Access)

Use the **MultiRow** property to specify or determine whether a tab control can display more than one row of tabs. Read/write **Boolean**.


## Syntax

_expression_.**MultiRow**

_expression_ A variable that represents a **[TabControl](Access.TabControl.md)** object.


## Remarks

The **MultiRow** property uses the following settings.

|Setting|Visual Basic|Description|
|:-----|:-----|:-----|
|Yes|**True**|Multiple rows are allowed.|
|No|**False**|(Default) Multiple rows aren't allowed.|

You can also set the default for this property by setting a control's **[DefaultControl](access.form.defaultcontrol.md)** property in Visual Basic.

When the **MultiRow** property is set to **True**, the number of rows is determined by the width and number of tabs. The number of rows may change if the control is resized or if additional tabs are added to the control.

When the **MultiRow** property is set to **False** and the width of the tabs exceeds the width of the control, navigation buttons appear on the right side of the tab control. Use the navigation buttons to scroll through all the tabs on the tab control.


## Example

To return the value of the **MultiRow** property for a tab control named **Details** on the **Order Entry** form, you can use the following.

```vb
Dim b As Boolean 
b = Forms("Order Entry").Controls("Details").MultiRow
```

<br/>

To set the value of the **MultiRow** property, you can use the following.

```vb
Forms("Order Entry").Controls("Details").MultiRow = True
```


[!include[Support and feedback](~/includes/feedback-boilerplate.md)]