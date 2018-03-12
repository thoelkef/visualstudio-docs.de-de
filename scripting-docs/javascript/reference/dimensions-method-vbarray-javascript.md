---
title: Dimensions-Methode (VBArray) (JavaScript) | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- dimensions
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- dimensions method
- VBArray object constant
ms.assetid: ac83589e-85d9-48cb-b28d-c579e65fd604
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9896a5beced00614a825b1921b6046b0ac8a396a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="dimensions-method-vbarray-javascript"></a>dimensions-Methode (VBArray) (JavaScript)
Gibt die Anzahl der Dimensionen in einem VBArray zurück  
  
## <a name="syntax"></a>Syntax  
  
```  
  
array.dimensions( )   
```  
  
## <a name="remarks"></a>Hinweise  
 Das erforderliche *array* ist ein VBArray-Objekt.  
  
## <a name="example"></a>Beispiel  
 Die **dimensions** -Methode bietet eine Möglichkeit, die Anzahl der Dimensionen in einem angegebenen VBArray abzurufen.  
  
 Das folgende Beispiel besteht aus drei Teilen. Der erste Teil ist VBScript-Code zum Erstellen eines sicheren Visual Basic-Arrays. Der zweite Teil ist [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] -Code, der die Anzahl der Dimensionen im sicheren Array und die obere Grenze jeder Dimension bestimmt. Beide Teile gehören in die \<HEAD >-Abschnitt einer HTML-Seite. Der dritte Teil ist die [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] Code, der wechselt in den \<Text > Abschnitt aus, um die anderen beiden Teile auszuführen.  
  
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
         a(j, i) = k  
         k = k + 1  
      Next  
   Next  
   CreateVBArray = a  
End Function  
-->  
</script>  
  
<script type="text/javascript">  
<!--  
function VBArrayTest(vba)  
{  
   var i;  
   var a = new VBArray(vba);  
   var s = "";  
   for (i = 1; i <= a.dimensions(); i++)  
   {  
      s += "The upper bound of dimension ";  
      s += i + " is ";  
      s += a.ubound(i);  
      s += ".<br />";  
   }  
   return(s);  
}  
-->  
</script>  
</head>  
  
<body>  
<script type="text/javascript">  
   document.write(VBArrayTest(CreateVBArray()));  
</script>  
</body>  
```  
  
## <a name="requirements"></a>Anforderungen  
 Wird in den folgenden Dokumentmodi unterstützt: Quirksmodus, Internet Explorer 6-Standardmodus, Internet Explorer 7-Standardmodus, Internet Explorer 8-Standardmodus, Internet Explorer 9-Standardmodus und Internet Explorer 10-Standardmodus. Wird in [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] -Apps nicht unterstützt. Siehe [Versionsinformationen](../../javascript/reference/javascript-version-information.md).  
  
 **Gilt für**: [VBArray Object](../../javascript/reference/vbarray-object-javascript.md)  
  
## <a name="see-also"></a>Siehe auch  
 [GetItem-Methode (VBArray)](../../javascript/reference/getitem-method-vbarray-javascript.md)   
 [Lbound-Methode (VBArray)](../../javascript/reference/lbound-method-vbarray-javascript.md)   
 [ToArray-Methode (VBArray)](../../javascript/reference/toarray-method-vbarray-javascript.md)   
 [ubound-Methode (VBArray)](../../javascript/reference/ubound-method-vbarray-javascript.md)