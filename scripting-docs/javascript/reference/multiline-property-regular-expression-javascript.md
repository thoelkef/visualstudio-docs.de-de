---
title: "MultiLine-Eigenschaft (regulärer Ausdruck) (JavaScript) | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: multiline
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: multiline property
ms.assetid: ca7b276a-1fe2-4189-ac27-f089ab3e9974
caps.latest.revision: "13"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 289cb8d8e103d8c4ac1b1ef06714105d21cba743
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="multiline-property-regular-expression-javascript"></a>multiline-Eigenschaft (regulärer Ausdruck) (JavaScript)
Gibt einen booleschen Wert, der angibt, des Status der multiline-Flags (**m**) mit einem regulären Ausdruck verwendet. Standardmäßig wird **"false"**. Schreibgeschützt.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
rgExp.multiline  
```  
  
## <a name="remarks"></a>Hinweise  
 Die erforderliche `rgExp` Argument ist eine Instanz der `RegExp` Objekt  
  
 Die **mehrzeiligen** -Eigenschaft gibt **"true"** Wenn multiline-Flags für einen regulären Ausdruck festgelegt ist, und gibt **"false"** wird jedoch nicht. Die **mehrzeiligen** Eigenschaft **"true"** Wenn regular Expression-Objekt erstellt wurde, mit der **m** Flag.  
  
 Wenn **mehrzeiligen** ist **"false"**, "^" entspricht der Position am Anfang der Zeichenfolge und "$" entspricht der Position am Ende einer Zeichenfolge. Wenn **mehrzeiligen** ist **"true"**, "^" entspricht die Position am Anfang einer Zeichenfolge sowie die Position nach einem "\n" oder "\r" und "$" entspricht der Position, an das Ende einer Zeichenfolge und der Position "\n vor "oder"\r".  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel veranschaulicht das Verhalten der **mehrzeiligen** Eigenschaft. Wenn Sie "m" in der unten gezeigten Funktion übergeben, wird das Wort "while" ersetzt, mit dem Wort "und". Da mit multiline-Flags festgelegt ist, und das Wort "while" tritt am Anfang der Zeile nach einem Zeilenumbruchzeichen. Multiline-Flags ermöglicht die Suche in mehrzeiligen Zeichenfolgen ausgeführt werden.  
  
```JavaScript  
function RegExpMultilineDemo(flag){  
   // The flag parameter is a string that contains  
   // g, i, or m.  The flags can be combined.  
  
   // Check flags for validity.  
   if (flag.match(/[^gim]/))  
      {  
      return ("Flag specified is not valid");  
      }  
  
   // Create the string on which to perform the replacement.  
   var ss = "The man hit the ball with the bat ";  
   ss += "\nwhile the fielder caught the ball with the glove.";  
  
   // Replace "while" with "and".  
   var re = new RegExp("^while", flag);  
   var r = ss.replace(re, "and");          
  
   // Output the multiline flag and the resulting string.  
   var s = "";  
   s += "Result for multiline = " + re.multiline.toString();  
   s += ": " + r;  
  
   return(s);  
  
}  
  
sa = RegExpMultilineDemo("m");  
sb = RegExpMultilineDemo("");  
document.write (sa + "<br />" + sb);  
```  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **Gilt für**: [Regular Expression-Objekt](../../javascript/reference/regular-expression-object-javascript.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Global-Eigenschaft (regulärer Ausdruck)](../../javascript/reference/global-property-regular-expression-javascript.md)   
 [IgnoreCase-Eigenschaft (regulärer Ausdruck)](../../javascript/reference/ignorecase-property-regular-expression-javascript.md)   
 [Syntax regulärer Ausdrücke (JavaScript)](http://msdn.microsoft.com/en-us/ab0766e1-7037-45ed-aa23-706f58358c0e)