---
title: Application.PageDeleteCanceled event (Visio)
ms.prod: visio
api_name:
- Visio.Application.PageDeleteCanceled
ms.assetid: 1efbd64c-365b-c967-59bb-8314a0fa6f34
ms.date: 06/08/2017
ms.localizationpriority: medium
---


# Application.PageDeleteCanceled event (Visio)

Occurs after an event handler has returned **True** (cancel) to a **QueryCancelPageDelete** event.


## Syntax

_expression_.**PageDeleteCanceled** (_Page_)

_expression_ A variable that represents an **[Application](Visio.Application.md)** object.


## Parameters

|Name|Required/Optional|Data type|Description|
|:-----|:-----|:-----|:-----|
| _Page_|Required| **[IVPAGE]**|The page that was going to be deleted.|

## Remarks

If you are using Microsoft Visual Basic or Visual Basic for Applications (VBA), the syntax in this topic describes a common, efficient way to handle events.

If you want to create your own **Event** objects, use the **[Add](visio.eventlist.add.md)** or **[AddAdvise](visio.eventlist.addadvise.md)** method. 

To create an **Event** object that runs an add-on, use the **Add** method as it applies to the **EventList** collection. 

To create an **Event** object that receives notification, use the **AddAdvise** method. 

To find an event code for the event that you want to create, see [Event codes](../visio/Concepts/event-codesvisio.md).

[!include[Support and feedback](~/includes/feedback-boilerplate.md)]