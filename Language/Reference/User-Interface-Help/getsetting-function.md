---
title: GetSetting function (Visual Basic for Applications)
keywords: vblr6.chm1020902
f1_keywords:
- vblr6.chm1020902
ms.prod: office
ms.assetid: 025f1d5d-6fc9-31ff-e59c-f5bcf47e3313
ms.date: 12/12/2018
ms.localizationpriority: medium
---


# GetSetting function

Returns a key setting value from an application's entry in the Windows [registry](../../Glossary/vbe-glossary.md#registry) or (on the Macintosh) information in the application's initialization file.

## Syntax

**GetSetting**(_appname_, _section_, _key_, [ _default_ ])

<br/>

The **GetSetting** function syntax has these [named arguments](../../Glossary/vbe-glossary.md#named-argument):

|Part|Description|
|:-----|:-----|
|_appname_|Required. [String expression](../../Glossary/vbe-glossary.md#string-expression) containing the name of the application or project whose key setting is requested. On the Macintosh, this is the filename of the initialization file in the Preferences folder in the System folder.|
|_section_|Required. String expression containing the name of the section where the key setting is found.|
|_key_|Required. String expression containing the name of the key setting to return.|
|_default_|Optional. [Expression](../../Glossary/vbe-glossary.md#expression) containing the value to return if no value is set in the key setting. If omitted, _default_ is assumed to be a zero-length string ("").|

## Remarks

If any of the items named in the **GetSetting** arguments don't exist, **GetSetting** returns the value of _default_.

## Example

This example first uses the **[SaveSetting](savesetting-statement.md)** statement to make entries in the Windows registry (or .ini file on 16-bit Windows platforms) for the application specified as _appname_, and then uses the **GetSetting** function to display one of the settings. Because the _default_ argument is specified, some value is guaranteed to be returned. Note that _section_ names can't be retrieved with **GetSetting**. Finally, the **[DeleteSetting](deletesetting-statement.md)** statement removes all the application's entries.


```vb
' Variant to hold 2-dimensional array returned by GetSetting.
Dim MySettings As Variant
' Place some settings in the registry.
SaveSetting "MyApp","Startup", "Top", 75
SaveSetting "MyApp","Startup", "Left", 50

Debug.Print GetSetting(appname := "MyApp", section := "Startup", _
                       key := "Left", default := "25")

DeleteSetting "MyApp", "Startup"

```

## See also

- [Functions (Visual Basic for Applications)](../functions-visual-basic-for-applications.md)

[!include[Support and feedback](~/includes/feedback-boilerplate.md)]
