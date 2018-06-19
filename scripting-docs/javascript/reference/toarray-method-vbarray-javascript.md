---
title: ToArray-Methode (VBArray) (JavaScript) | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- toArray
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- toArray method
ms.assetid: 664de44c-2039-4289-82f6-948e9d744d80
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: eeee8acad04125eb942089b4d8dacef6f0f5e6fb
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
ms.locfileid: "24641770"
---
# <a name="toarray-method-vbarray-javascript"></a>toArray-Methode (VBArray) (JavaScript)
Gibt ein [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] -Standardarray zurück, das aus einem VBArray konvertiert wurde.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
safeArray.toArray( )   
```  
  
## <a name="remarks"></a>Hinweise  
 Der erforderliche *safeArray* -Verweis ist ein VBArray-Objekt.  
  
 Die Konvertierung übersetzt das mehrdimensionale VBArray in ein eindimensionales [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] -Array. Jede nachfolgende Dimension wird an das Ende der voherigen angefügt. Beispielsweise wird ein VBArray mit drei Dimensionen und drei Elemente in jeder Dimension folgendermaßen in ein [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] -Array konvertiert:  
  
 Angenommen, das VBArray enthält: (1, 2, 3), (4, 5, 6), (7, 8, 9). Nach der Übersetzung enthält das [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] -Array: 1, 2, 3, 4, 5, 6, 7, 8, 9.  
  
 Es gibt derzeit keine Möglichkeit, ein [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] -Array in ein VBArray zu konvertieren.  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel besteht aus drei Teilen. Der erste Teil ist VBScript-Code zum Erstellen eines sicheren Visual Basic-Arrays. Der zweite Teil ist [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] -Code, der das sichere Visual Basic-Array in ein [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] -Array konvertiert. Beide Teile gehören in die \<HEAD >-Abschnitt einer HTML-Seite. Der dritte Teil ist die [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] Code, der wechselt in den \<Text > Abschnitt aus, um die anderen beiden Teile auszuführen.  
  
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
function VBArrayTest(vbarray)  
{  
   var a = new VBArray(vbarray);  
   var b = a.toArray();  
   var i;  
   for (i = 0; i < 9; i++)   
   {  
      document.writeln(b[i]);  
   }  
}  
-->  
</script>  
</head>  
  
<body>  
<script type="text/javascript">  
<!--  
   VBArrayTest(CreateVBArray());  
-->  
</script>  
</body>  
```  
  
## <a name="requirements"></a>Anforderungen  
 Wird in den folgenden Dokumentmodi unterstützt: Quirksmodus, Internet Explorer 6-Standardmodus, Internet Explorer 7-Standardmodus, Internet Explorer 8-Standardmodus, Internet Explorer 9-Standardmodus und Internet Explorer 10-Standardmodus. Wird in [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] -Apps nicht unterstützt. Siehe [Versionsinformationen](../../javascript/reference/javascript-version-information.md).  
  
 **Gilt für**: [VBArray Object](../../javascript/reference/vbarray-object-javascript.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Dimensions-Methode (VBArray)](../../javascript/reference/dimensions-method-vbarray-javascript.md)   
 [GetItem-Methode (VBArray)](../../javascript/reference/getitem-method-vbarray-javascript.md)   
 [Lbound-Methode (VBArray)](../../javascript/reference/lbound-method-vbarray-javascript.md)   
 [ubound-Methode (VBArray)](../../javascript/reference/ubound-method-vbarray-javascript.md)