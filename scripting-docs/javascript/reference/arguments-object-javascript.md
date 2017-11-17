---
title: Arguments-Objekt (JavaScript) | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: arguments
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- arguments, arguments object
- arguments object
ms.assetid: 5eb79ca9-bbb8-4a42-aaf5-16a93ecb425f
caps.latest.revision: "15"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2a5c526d19ad5469d9d099f51cc5a2e2d089814f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="arguments-object-javascript"></a>arguments-Objekt (JavaScript)
Ein Objekt, das die Argumente der gegenwärtig ausgeführten Funktion und die Funktionen darstellt, die das Objekt aufgerufen hat.  
  
## <a name="syntax"></a>Syntax  
  
```  
[function.]arguments[n]  
```  
  
## <a name="parameters"></a>Parameter  
 *function*  
 Dies ist optional. Der Name der derzeit ausgeführten `Function` Objekt.  
  
 *n*  
 Erforderlich. Der nullbasierte Index, um Argumentwerte übergeben, um die `Function` Objekt.  
  
## <a name="remarks"></a>Hinweise  
 Sie können nicht explizit erstellen eine **Argumente** Objekt. Die **Argumente** Objekt ist nur verfügbar, wenn eine Funktion mit der Ausführung beginnt. Die **Argumente** Objekt der Funktion ist kein Array ist, aber die einzelnen Argumente erfolgt die gleiche Weise auf die Elemente des Arrays zugegriffen werden. Der Index  *n*  ist tatsächlich ein Verweis auf eine der der **0**  ***n***  Eigenschaften der **Argumente** Objekt.  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel veranschaulicht die Verwendung der **Argumente** Objekt.  
  
```JavaScript  
function ArgTest(a, b)  
{  
   var s = "";  
  
   s += "Expected Arguments: " + ArgTest.length;  
   s += "<br />";  
   s += "Passed Arguments: " + arguments.length;  
   s += "<br />";  
  
   s += "The individual arguments are: "  
   for (n = 0; n < arguments.length; n++)  
   {  
      s += ArgTest.arguments[n];  
      s += " ";  
   }  
  
   document.write(s);  
}  
  
ArgTest(1, 2, "hello", new Date())  
  
// Output:  
// Expected Arguments: 2  
// Passed Arguments: 4  
// The individual arguments are: 1 2 hello Tues Jan 8 08:27:09 PST 20xx  
```  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Siehe auch  
 [0,... n Eigenschaften (Arguments)](../../javascript/reference/0-dot-dot-dot-n-properties-arguments-javascript.md)   
 [Callee-Eigenschaft (Arguments)](../../javascript/reference/callee-property-arguments-javascript.md)   
 [length-Eigenschaft (Argumente)](../../javascript/reference/length-property-arguments-javascript.md)