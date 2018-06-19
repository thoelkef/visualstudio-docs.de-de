---
title: Arguments-Eigenschaft (Funktion) (JavaScript) | Microsoft Docs
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
- arguments
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- arguments, arguments property
- Arguments property
ms.assetid: efc7a1ee-0880-4f05-b0f2-808f31a4af1d
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5b0b18fb8164639119e5db5e7a5d76b4280f9c9d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
ms.locfileid: "24633400"
---
# <a name="arguments-property-function-javascript"></a>arguments-Eigenschaft (Funktion) (JavaScript)
Ruft die Argumente für die aktuell ausgeführte `Function` Objekt.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
function.arguments  
```  
  
## <a name="remarks"></a>Hinweise  
 Die `function` Argument ist der Name der derzeit ausgeführten Funktion und kann ausgelassen werden.  
  
 Diese Eigenschaft ermöglicht eine Funktion, eine Variable Anzahl von Argumenten zu behandeln. Die **Länge** Eigenschaft von der `arguments` Objekt enthält die Anzahl von Argumenten, die an die Funktion übergeben. Die einzelnen Argumente enthalten sind, der `arguments` Objekt zugegriffen werden kann, auf die gleiche Weise auf die Elemente des Arrays zugegriffen werden.  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel veranschaulicht die Verwendung der `arguments`-Eigenschaft.  
  
```JavaScript  
function ArgTest(arg1, arg2){  
   var s = "";  
   s += "The individual arguments are: "  
   for (n = 0; n < arguments.length; n++){  
      s += ArgTest.arguments[n];  
      s += " ";  
   }  
   return(s);  
}  
document.write(ArgTest(1, 2, "hello"));  
  
//Output: function ArgTest(arg1, arg2){  
   var s = "";  
   s += "The individual arguments are: "  
   for (n = 0; n < arguments.length; n++){  
      s += ArgTest.arguments[n];  
      s += " ";  
   }  
   return(s);  
}  
document.write(ArgTest(1, 2, "hello"));  
  
// Output: The individual arguments are: 1 2 hello  
```  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]  
  
## <a name="see-also"></a>Siehe auch  
 [Arguments-Objekt](../../javascript/reference/arguments-object-javascript.md)   
 [function-Anweisung](../../javascript/reference/function-statement-javascript.md)