---
title: 0,... n Eigenschaften (Arguments) (JavaScript) | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: 0...n
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: 0...n properties
ms.assetid: 52857c4b-3d56-4500-93ff-4db4729c2578
caps.latest.revision: "13"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f46c7dafef1cdc27d27f619936349637af172740
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="0n-properties-arguments-javascript"></a>0...n-Eigenschaften (Argumente) (JavaScript)
Gibt den tatsächlichen Wert einzelner Argumente aus einem **Argumente** zurückgegebenes Objekt die **Argumente** Eigenschaft einer ausgeführten Funktion.  
  
## <a name="syntax"></a>Syntax  
  
```  
[function.]arguments[[0|1|2|...|n]]  
```  
  
## <a name="parameters"></a>Parameter  
 *function*  
 Dies ist optional. Der Name der derzeit ausgeführten `Function` Objekt.  
  
 0, 1, 2, *, n*  
 Erforderlich. Nicht Negative ganze Zahl im Bereich von 0 bis  *n*  , wobei 0 für das erste Argument darstellt und  *n*  das letzte Argument darstellt. Der Wert des letzten Arguments  *n*  ist **arguments.length 1**.  
  
## <a name="remarks"></a>Hinweise  
 Die Werte von 0 zurückgegeben. . . n Eigenschaften sind die tatsächlichen Werte, die an die ausgeführte Funktion übergeben. Beim nicht tatsächlich ein Array von Argumenten, die einzelnen Argumente, die bilden die **Argumente** Objekt erfolgt die gleiche Weise, dass Arrayelemente zugegriffen werden.  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel veranschaulicht die Verwendung der **0...**  ***n***Eigenschaften der **Argumente** Objekt. Um das Beispiel vollständig zu verstehen, müssen übergeben Sie ein oder mehrere Argumente an die Funktion:  
  
```JavaScript  
function ArgTest(){  
   var s = "";  
   s += "The individual arguments are: "  
   for (n = 0; n < arguments.length; n++){  
      s += ArgTest.arguments[n];  
      s += " ";  
   }  
   return(s);  
}  
document.write(ArgTest(1, 2, "hello", new Date()));  
```  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **Gilt für**: [Arguments-Objekt](../../javascript/reference/arguments-object-javascript.md)&#124; [Objekt-Funktion](../../javascript/reference/function-object-javascript.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Length-Eigenschaft (Arguments)](../../javascript/reference/length-property-arguments-javascript.md)   
 [length-Eigenschaft (Funktion)](../../javascript/reference/length-property-function-javascript.md)