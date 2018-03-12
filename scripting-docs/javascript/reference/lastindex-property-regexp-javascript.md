---
title: LastIndex-Eigenschaft (RegExp) (JavaScript) | Microsoft Docs
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
- lastIndex
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- lastIndex property
ms.assetid: c8ae2a13-6dff-4cbe-b662-aca3d66c2a7f
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d5e24fe14d335e1494b13518543f56025625de0b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="lastindex-property-regexp-javascript"></a>lastIndex-Eigenschaft (RegExp) (JavaScript)
Gibt die Zeichenposition, an die nächste Übereinstimmung beginnt, in einer durchsuchten Zeichenfolge zurück.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
RegExp.lastIndex  
```  
  
## <a name="remarks"></a>Hinweise  
 Das Objekt, das dieser Eigenschaft zugeordnet ist immer die globale `RegExp` Objekt.  
  
 Die `lastIndex` Eigenschaft ist nullbasiert, d. h. der Index des ersten Zeichens ist 0 (null). Der Anfangswert ist-1. Der Wert wird geändert, wenn eine Übereinstimmung gefunden wird.  
  
 Die `lastIndex` Eigenschaft geändert wird, indem die `exec` und **testen** Methoden die `RegExp` -Objekt, und die `match`, **ersetzen**, und **Teilen**Methoden die `String` Objekt.  
  
 Die folgenden Regeln gelten für die Werte der `lastIndex`:  
  
-   Wenn keine Übereinstimmung vorhanden ist `lastIndex` auf-1 festgelegt ist.  
  
-   Wenn `lastIndex` ist größer als die Länge der Zeichenfolge **testen** und `exec` fehl und `lastIndex` auf-1 festgelegt ist.  
  
-   Wenn `lastIndex` ist gleich der Länge der Zeichenfolge ist, entspricht der reguläre Ausdruck, wenn das Muster der leeren Zeichenfolge entspricht. Andernfalls schlägt die Übereinstimmung fehl und `lastIndex` auf "-1" zurückgesetzt.  
  
-   Andernfalls `lastIndex` auf der nächsten Position nach der aktuellsten Übereinstimmung festgelegt ist.  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel veranschaulicht die Verwendung der `lastIndex` Eigenschaft. Diese Funktion durchläuft eine Suchzeichenfolge und druckt die **Index** und `lastIndex` Werte für jedes Wort in der Zeichenfolge.  
  
```JavaScript  
function RegExpTest()  
{  
   var ver = Number(ScriptEngineMajorVersion() + "." + ScriptEngineMinorVersion())  
   if (ver < 5.5)  
   {  
      document.write("You need a newer version of JavaScript for this to work");  
      return;  
   }  
  
   var src = "The quick brown fox jumps over the lazy dog.";  
  
   // Create regular expression pattern with a global flag.  
   var re = /\w+/g;  
  
   // Get the next word, starting at the position of lastindex.  
   var arr;  
   while ((arr = re.exec(src)) != null)  
      {  
      // New line:  
      document.write ("<br />");    
      document.write (arr.index + "-" + re.lastIndex + " ");  
      document.write (arr);  
      }  
}  
```  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Gilt für**: [RegExp-Objekt](../../javascript/reference/regexp-object-javascript.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Syntax regulärer Ausdrücke (JavaScript)](http://msdn.microsoft.com/en-us/ab0766e1-7037-45ed-aa23-706f58358c0e)