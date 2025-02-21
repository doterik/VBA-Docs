---
title: PivotTable.DrillDown method (Excel)
keywords: vbaxl10.chm235206
f1_keywords:
- vbaxl10.chm235206
ms.prod: excel
ms.assetid: 01824849-6c03-d263-aeb5-68b6c331bf0f
ms.date: 05/08/2019
ms.localizationpriority: medium
---


# PivotTable.DrillDown method (Excel)

Enables you to drill down into the data within an OLAP-based or PowerPivot-based cube hierarchy.


## Syntax

_expression_.**DrillDown** (_PivotItem_, _PivotLine_)

_expression_ A variable that represents a **[PivotTable](Excel.PivotTable.md)** object.


## Parameters

|Name|Required/Optional|Data type|Description|
|:-----|:-----|:-----|:-----|
| _PivotItem_|Required|PIVOTITEM|The member from which the drill down is performed.|
| _PivotLine_|Optional|**Variant**|Specifies the line in the PivotTable where the operation starting member resides. In cases where PivotLine is not specified, defaults to the top PivotLine where the member appears.|

## Return value

**VOID**


## Example

The following sample code demonstrates the **DrillDown** method as used on a PivotTable.

```vb
ActiveSheet.PivotTables("PivotTable1").DrillDown ActiveSheet.PivotTables( _
      "PivotTable1").PivotFields("[Customer].[Customer Geography].[Country]"). _
      PivotItems("[Customer].[Customer Geography].[Country].&[Australia]"), _
      ActiveSheet.PivotTables("PivotTable1").PivotRowAxis.PivotLines(1)
```

<br/>

The following sample code demonstrates the **DrillDown** method as used on a PivotChart.

```vb
ActiveChart.PivotLayout.PivotTable.DrillDown ActiveChart.PivotLayout.PivotTable _
      .PivotFields("[Customer].[Customer Geography].[Country]").PivotItems( _
      "[Customer].[Customer Geography].[Country].&[Australia]"), ActiveChart. _
      PivotLayout.PivotTable.PivotRowAxis.PivotLines(1)
```




[!include[Support and feedback](~/includes/feedback-boilerplate.md)]