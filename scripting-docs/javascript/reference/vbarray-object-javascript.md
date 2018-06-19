---
title: VBArray-Objekt (JavaScript) | Microsoft Docs
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
- VBArray
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- VBArray object constant
ms.assetid: f0b767f1-ea8a-4726-962b-2708d4742518
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b86e261a0cef445f1e0e0ecd651d5eb283cffce1
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
ms.locfileid: "24641620"
---
# <a name="vbarray-object-javascript"></a>VBArray-Objekt (JavaScript)
Bietet Zugriff auf sichere Visual Basic-Arrays.  
  
> [!WARNING]
>  Dieses Objekt wird nur in Internet Explorer unterstützt, nicht in [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] -Apps.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
varName = new VBArray(safeArray)   
```  
  
## <a name="parameters"></a>Parameter  
 `varName`  
 Erforderlich. Der Variablenname, dem das VBArray zugewiesen wird.  
  
 *safeArray*  
 Erforderlich. Ein VBArray-Wert.  
  
## <a name="remarks"></a>Hinweise  
 VBArrays sind schreibgeschützt und können nicht direkt erstellt werden. Das *safeArray* -Argument muss einen VBArray-Wert abgerufen haben, bevor es an den VBArray-Konstruktor übergeben wird. Dies kann nur durch Abrufen des Werts aus einem vorhandenen ActiveX oder einem anderen Objekt erfolgen.  
  
 VBArrays können über mehrere Dimensionen verfügen. Die Indizes der einzelnen Dimensionen können unterschiedlich sein. Die **dimensions** -Methode ruft die Anzahl der Dimensionen im Array ab; die `lbound` - und `ubound` -Methoden rufen den von jeder Dimension verwendeten Indexbereich ab.  
  
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
      document.writeln("<br />")  
   Next  
   CreateVBArray = a  
End Function  
-->  
</script>  
  
<script type="text/javascript">  
<!--  
function VBArrayTest(vbarray){  
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
  
## <a name="properties"></a>Eigenschaften  
 Das `VBArray` -Objekt hat keine Eigenschaften.  
  
## <a name="methods"></a>Methoden  
 [Dimensions-Methode](../../javascript/reference/dimensions-method-vbarray-javascript.md) &#124; [GetItem-Methode](../../javascript/reference/getitem-method-vbarray-javascript.md) &#124; [Lbound-Methode](../../javascript/reference/lbound-method-vbarray-javascript.md) &#124; [ToArray-Methode](../../javascript/reference/toarray-method-vbarray-javascript.md) &#124; [Ubound-Methode](../../javascript/reference/ubound-method-vbarray-javascript.md)  
  
## <a name="requirements"></a>Anforderungen  
 Wird in den folgenden Dokumentmodi unterstützt: Quirksmodus, Internet Explorer 6-Standardmodus, Internet Explorer 7-Standardmodus, Internet Explorer 8-Standardmodus, Internet Explorer 9-Standardmodus und Internet Explorer 10-Standardmodus. Wird in [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] -Apps nicht unterstützt. Siehe [Versionsinformationen](../../javascript/reference/javascript-version-information.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Array-Objekt](../../javascript/reference/array-object-javascript.md)