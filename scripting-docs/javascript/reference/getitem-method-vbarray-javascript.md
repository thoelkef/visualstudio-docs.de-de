---
title: GetItem-Methode (VBArray) (JavaScript) | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: getItem
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- getItem method
- Item property
ms.assetid: f62964ad-8b2f-4596-95d0-b20e587ecea5
caps.latest.revision: "16"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e6457435d047f2780a19fa8ce26fc2bb86f7ae0e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="getitem-method-vbarray-javascript"></a>getItem-Methode (VBArray) (JavaScript)
Gibt das Element an der angegebenen Position zurück.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
safeArray.getItem(dimension1[, dimension2, ...], dimensionN)   
```  
  
## <a name="parameters"></a>Parameter  
 *safeArray*  
 Erforderlich. Ein VBArray-Objekt.  
  
 *dimension1,..., dimensionN*  
 Gibt den genauen Speicherort des gewünschten Elements des VBArray an. *n* entspricht der Anzahl der Dimensionen im VBArray.  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel besteht aus drei Teilen. Der erste Teil ist VBScript-Code zum Erstellen eines sicheren Visual Basic-Arrays. Der zweite Teil ist [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] -Code, der das sichere Visual Basic-Array durchläuft und den Inhalt jedes Elements ausdruckt. Beide Teile gehören in die \<HEAD >-Abschnitt einer HTML-Seite. Der dritte Teil ist die [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] Code, der wechselt in den \<Text > Abschnitt aus, um die anderen beiden Teile auszuführen.  
  
```JavaScript  
<head>  
<script type="text/vbscript">  
<!--  
Function CreateVBArray()  
   Dim i, j, k  
   Dim a(2, 2)  
   k = 1  
   For i = 0 To 2  
      For j = 0 To 2  
         a(i, j) = k  
         document.writeln(k)  
         k = k + 1  
      Next  
      document.writeln("<BR>")  
   Next  
   CreateVBArray = a  
End Function  
-->  
</script>  
<script type="text/javascript">  
<!--  
function GetItemTest(vbarray)  
{  
   var i, j;  
   var a = new VBArray(vbarray);  
   for (i = 0; i <= 2; i++)  
   {  
      for (j =0; j <= 2; j++)  
      {  
         document.writeln(a.getItem(i, j));  
      }  
   }  
}  
-->  
</script>  
</head>  
<body>  
<script type="text/javascript">  
<!--  
   GetItemTest(CreateVBArray());  
-->  
</script>  
</body>  
```  
  
## <a name="requirements"></a>Anforderungen  
 Wird in den folgenden Dokumentmodi unterstützt: Quirksmodus, Internet Explorer 6-Standardmodus, Internet Explorer 7-Standardmodus, Internet Explorer 8-Standardmodus, Internet Explorer 9-Standardmodus und Internet Explorer 10-Standardmodus. Wird in [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] -Apps nicht unterstützt. Siehe [Versionsinformationen](../../javascript/reference/javascript-version-information.md).  
  
 **Gilt für**: [VBArray Object](../../javascript/reference/vbarray-object-javascript.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Dimensions-Methode (VBArray)](../../javascript/reference/dimensions-method-vbarray-javascript.md)   
 [Lbound-Methode (VBArray)](../../javascript/reference/lbound-method-vbarray-javascript.md)   
 [ToArray-Methode (VBArray)](../../javascript/reference/toarray-method-vbarray-javascript.md)   
 [ubound-Methode (VBArray)](../../javascript/reference/ubound-method-vbarray-javascript.md)