---
title: Partition function (Visual Basic for Applications)
keywords: vblr6.chm1010095
f1_keywords:
- vblr6.chm1010095
ms.prod: office
ms.assetid: a9565bfc-640f-4550-455f-7d50d110df43
ms.date: 01/14/2019
ms.localizationpriority: medium
---


# Partition function

Returns a **Variant** (**String**) indicating where a number occurs within a calculated series of ranges.

## Syntax

**Partition**(_number_, _start_, _stop_, _interval_)

<br/>

The **Partition** function syntax has these [named arguments](../../Glossary/vbe-glossary.md#named-argument):

|Part|Description|
|:-----|:-----|
|_number_|Required. The number that you want to evaluate against the ranges.|
|_start_|Required. The number that is the start of the overall range of numbers. The number can't be less than 0.|
|_stop_|Required. The number that is the end of the overall range of numbers. The number can't be equal to or less than _start_.|
|_interval_|Required. The number that is the difference between one range and the next. The number can't be less than 1.|

## Remarks

The **Partition** function identifies the particular range in which _number_ falls and returns a **Variant** (**String**) describing that range. The **Partition** function is most useful in queries. You can create a select query that shows how many orders fall within various ranges, for example, order values from 1 to 1000, 1001 to 2000, and so on.

The following table shows how the ranges are determined using three sets of _start_, _stop_, and _interval_ parts. The First Range and Last Range columns show what **Partition** returns. The ranges are represented by _lowervalue_: _uppervalue_, where the low end (_lowervalue_) of the range is separated from the high end (_uppervalue_) of the range with a colon (**:**).

<br/>

|_start_|_stop_|_interval_|Before First|First Range|Last Range|After Last|
|:-----|:-----|:-----|:-----|:-----|:-----|:-----|
|0|99|5|" :-1"|" 0: 4"|" 95: 99"|" 100: "|
|20|199|10|" : 19"|" 20: 29"|" 190: 199"|" 200: "|
|100|1010|20|" : 99"|" 100: 119"|" 1000: 1010"|" 1011: "|

In the table shown previously, the third line shows the result when _start_ and _stop_ define a set of numbers that can't be evenly divided by _interval_. The last range extends to _stop_ (11 numbers) even though _interval_ is 20.

If necessary, **Partition** returns a range with enough leading spaces so that there are the same number of characters to the left and right of the colon as there are characters in _stop_, plus one. This ensures that if you use **Partition** with other numbers, the resulting text will be handled properly during any subsequent sort operation.

If _interval_ is 1, the range is _number:number_, regardless of the _start_ and _stop_ arguments. For example, if _interval_ is 1, _number_ is 100 and _stop_ is 1000, **Partition** returns " 100: 100".

Any argument can be a decimal value, but it will be rounded to the nearest even integer before processing.
If any of the arguments is [Null](../../Glossary/vbe-glossary.md#null), **Partition** returns a **Null**.

## Example

This example assumes that you have an Orders table that contains a Freight field. It creates a select procedure that counts the number of orders for which freight cost falls into each of several ranges. The **Partition** function is used first to establish these ranges, and then the SQL **Count** function counts the number of orders in each range. 

In this example, the arguments to the **Partition** function are _start_ = 0, _stop_ = 500, _interval_ = 50. The first range would therefore be 0:49, and so on up to 500.

```sql
SELECT DISTINCTROW Partition([freight],0, 500, 50) AS Range,
Count(Orders.Freight) AS Count
FROM Orders
GROUP BY Partition([freight],0,500,50);
```

## See also

- [Functions (Visual Basic for Applications)](../functions-visual-basic-for-applications.md)

[!include[Support and feedback](~/includes/feedback-boilerplate.md)]
