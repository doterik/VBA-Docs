---
title: CheckBox.Undo method (Access)
keywords: vbaac10.chm10684
f1_keywords:
- vbaac10.chm10684
ms.prod: access
api_name:
- Access.CheckBox.Undo
ms.assetid: e69e5d59-398d-744c-0a99-e2ca9b290c9b
ms.date: 02/20/2019
ms.localizationpriority: medium
---


# CheckBox.Undo method (Access)

Use the **Undo** method to reset a control or form when its value has been changed.


## Syntax

_expression_.**Undo**

_expression_ A variable that represents a **[CheckBox](Access.CheckBox.md)** object.


## Remarks

For example, you can use the **Undo** method to clear a change to a record that contains an invalid entry.

If the **Undo** method is applied to a form, all changes to the current record are lost. If the **Undo** method is applied to a control, only the control itself is affected.

This method must be applied before the form or control is updated. You may want to include this method in a form's **BeforeUpdate** event or in a control's **Change** event.

The **Undo** method offers an alternative to using the **SendKeys** statement to send the value of the Esc key in an event procedure.


## Example

The following example shows how you can use the **Undo** method within a control's **Change** event procedure to force a field named **LastName** to reset to its original value if it changed.

```vb
Private Sub LastName_Change() 
 Me!LastName.Undo 
End Sub
```

<br/>

The next example uses the **Undo** method to reset all changes to a form before the form is updated.

```vb
Private Sub Form_BeforeUpdate(Cancel As Integer) 
 Me.Undo 
End Sub
```


[!include[Support and feedback](~/includes/feedback-boilerplate.md)]