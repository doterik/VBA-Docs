---
title: Application.HyperlinkPart method (Access)
keywords: vbaac10.chm12569
f1_keywords:
- vbaac10.chm12569
ms.prod: access
api_name:
- Access.Application.HyperlinkPart
ms.assetid: 011665ea-c650-fab3-a736-f26a3de1b65e
ms.date: 02/05/2019
ms.localizationpriority: medium
---


# Application.HyperlinkPart method (Access)

The **HyperlinkPart** method returns information about data stored as a Hyperlink data type.


## Syntax

_expression_.**HyperlinkPart** (_Hyperlink_, _Part_)

_expression_ A variable that represents an **[Application](Access.Application.md)** object.


## Parameters

|Name|Required/Optional|Data type|Description|
|:-----|:-----|:-----|:-----|
| _Hyperlink_|Required|**Variant**|The data stored in a **Hyperlink** field.|
| _Part_|Optional|**[AcHyperlinkPart](Access.AcHyperlinkPart.md)**|An **AcHyperlinkPart** constant representing the information that you want returned by the **HyperlinkPart** method.|

## Return value

String


## Remarks

You use the **HyperlinkPart** method to return one of three values from a **Hyperlink** field or the displayed value. The value returned depends on the setting of the _part_ argument. 

The _part_ argument is optional. If it's not used, the function returns the value Microsoft Access displays for the hyperlink (which corresponds to the **acDisplayedValue** setting for the _part_ argument). The returned values can be one of the four parts of the **Hyperlink** field (_displaytext_,  _address_,  _subaddress_, or  _screentip_), the full address,  _address_# _subaddress_, or the value Microsoft Access displays for the hyperlink.

> [!NOTE] 
> If you use the **HyperlinkPart** method in a query, the _part_ argument is required, and you can't use the constants listed above but must use the actual value instead.

When a value is provided in the  _displaytext_ part of a **Hyperlink** field, the value displayed by Microsoft Access will be the same as the _displaytext_ setting. When there's no value in the _displaytext_ part of a **Hyperlink** field, the value displayed will be the _address_ or _subaddress_ part of the **Hyperlink** field, depending on which value is first present in the field.

The following table shows the values returned by the **HyperlinkPart** method for data stored in a **Hyperlink** field.

|Hyperlink field data|HyperlinkPart method returned values|
|:-----|:-----|
|#https://www.microsoft.com#|**acDisplayedValue**: `https://www.microsoft.com`<br/><br/>**acDisplayText**: **acAddress**: `https://www.microsoft.com`<br/><br/>**acSubAddress**: **acScreenTip**: **acFullAddress**: `https://www.microsoft.com`|
|Microsoft#https://www.microsoft.com#|**acDisplayedValue**: `Microsoft`<br/><br/>**acDisplayText**: `Microsoft`<br/><br/>**acAddress**: `https://www.microsoft.com`<br/><br/>**acSubAddress**: **acScreenTip**: **acFullAddress**: `https://www.microsoft.com`|
|Customers#https://www.microsoft.com#Form Customers|**acDisplayedValue**: `Customers`<br/><br/>**acDisplayText**: `Customers`<br/><br/>**acAddress**: `https://www.microsoft.com`<br/><br/>**acSubAddress**: `Form Customers`<br/><br/>**acScreenTip**: **acFullAddress**: `https://www.microsoft.com#Form Customer`|
|##Form Customers#Enter Information|**acDisplayedValue**: `Form Customers`<br/><br/>**acDisplayText**: **acAddress**: **acSubAddress**: `Form Customers`<br/><br/>**acScreenTip**: `Enter Information`<br/><br/>**acFullAddress**: `#FormCustomer`|

When you add an _address_ part to a **Hyperlink** field by using the **Insert Hyperlink** dialog box (available by choosing **Hyperlink** on the **Insert** menu) or by typing an address part directly into a **Hyperlink** field, Access adds the two # symbols that delimit parts of the hyperlink data.

You can add or edit the _displaytext_ part of a hyperlink field by right-clicking a hyperlink in a table, form, or report, pointing to **Hyperlink** on the shortcut menu, and then typing the display text in the **Text to display** box.

When you add data to a **Hyperlink** field directly, you must include the two # symbols to delimit the parts of the hyperlink data.


## Example

The following example uses all four of the _part_ argument constants to display information returned by the **HyperlinkPart** method for each record in a table containing a **Hyperlink** field. To try this example, paste the DisplayHyperlinkParts procedure into the Declarations section of a module. You can call the DisplayHyperlinkParts procedure from the Debug window, passing to it the name of a table containing hyperlinks and the name of the field containing Hyperlink data. For example:

```vb
DisplayHyperlinkParts "MyHyperlinkTableName", "MyHyperlinkFieldName" 
 
Public Sub DisplayHyperlinkParts(ByVal strTable As String, _ 
 ByVal strField As String) 
 
 Dim rst As New ADODB.Recordset 
 Dim strMsg As String 
 
 
 rst.Open strTable, CurrentProject.Connection, _ 
 adOpenForwardOnly, adLockReadOnly 
 
 ' For each record in table. 
 Do Until rst.EOF 
 strMsg = "DisplayValue = " _ 
 & HyperlinkPart(rst(strField), acDisplayedValue) _ 
 & vbCrLf & "DisplayText = " _ 
 & HyperlinkPart(rst(strField), acDisplayText) _ 
 & vbCrLf & "Address = " _ 
 & HyperlinkPart(rst(strField), acAddress) _ 
 & vbCrLf & "SubAddress = " _ 
 & HyperlinkPart(rst(strField), acSubAddress) _ 
 & vbCrLf & "ScreenTip = " _ 
 & HyperlinkPart(rst(strField), acScreenTip) _ 
 & vbCrLf & "Full Address = " _ 
 & HyperlinkPart(rst(strField), acFullAddress) 
 
 ' Show parts returned by HyperlinkPart function. 
 MsgBox strMsg 
 rst.MoveNext 
 Loop 
 
End Sub
```

<br/>

When you use the **HyperlinkPart** method in a query, the _part_ argument is required. For example, the following SQL statement uses the **HyperlinkPart** method to return information about data stored as a Hyperlink data type in the **URL** field of the Links table:

```sql
SELECT Links.URL, HyperlinkPart([URL],0) 
 AS Display, HyperlinkPart([URL],1) 
 AS Name, HyperlinkPart([URL],2) 
 AS Addr, HyperlinkPart([URL],3) 
 AS SubAddr, HyperlinkPart([URL],4) 
 AS ScreenTip 
 FROM Links
```




[!include[Support and feedback](~/includes/feedback-boilerplate.md)]
