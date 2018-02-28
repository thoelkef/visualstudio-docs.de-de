---
title: Callee-Eigenschaft (Arguments) (JavaScript) | Microsoft Docs
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
- callee
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- callee property
ms.assetid: ad9d4d21-73f0-44f6-8bec-502f3456cd23
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 33f1c2926d76c0a1f088c8f4222b6f24c004b73b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="callee-property-arguments-javascript"></a>callee-Eigenschaft (arguments) (JavaScript)
Gibt die `Function` Objekt ausgeführt wird, d. h. den Textkörper des angegebenen `Function` Objekt.  
  
## <a name="syntax"></a>Syntax  
  
```  
[function.]arguments.callee  
```  
  
## <a name="remarks"></a>Hinweise  
 Das optionale *Funktion* -Argument ist der Name der derzeit ausgeführten `Function` Objekt.  
  
 Die `callee` Eigenschaft ist ein Mitglied der **Argumente** -Objekt, das zur Verfügung steht, wenn die zugehörige Funktion ausgeführt wird.  
  
 Der Anfangswert von der `callee` Eigenschaft ist für die `Function` Objekt ausgeführt wird. Dadurch können anonyme Funktionen, um rekursiv sein.  
  
## <a name="example"></a>Beispiel  
  
```JavaScript  
function factorial(n){  
  if (n <= 0)  
     return 1;  
  else  
     return n * arguments.callee(n - 1)  
}  
document.write(factorial(4));  
```  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **Gilt für**: [Arguments-Objekt](../../javascript/reference/arguments-object-javascript.md)&#124; [Objekt-Funktion](../../javascript/reference/function-object-javascript.md)  
  
## <a name="see-also"></a>Siehe auch  
 [caller-Eigenschaft (Funktion)](../../javascript/reference/caller-property-function-javascript.md)