---
title: Math.Min-Funktion (JavaScript) | Microsoft Docs
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
- min
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- min method
ms.assetid: a1d7dd85-27ef-45cd-aa2a-f8e80f0b2898
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bb496cff65db11cf6c99d6a6e687f39e20ea857c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="mathmin-function-javascript"></a>Math.min-Funktion (JavaScript)
Gibt die kleinere von einem Satz von numerischen Ausdrücken zurück.  
  
## <a name="syntax"></a>Syntax  
  
```  
Math.min([number1[, number2[... [,numberN]]]])  
```  
  
## <a name="remarks"></a>Hinweise  
 Das optionale `number1, number2, ..., numberN` Argumente sind numerische Ausdrücke ausgewertet werden soll.  
  
 Wenn keine Argumente bereitgestellt werden, ist der Rückgabewert gleich [Number. POSITIVE_INFINITY](../../javascript/reference/number-constants-javascript.md). Wenn eines der Argumente ist `NaN`, der Rückgabewert ist ebenfalls `NaN`.  
  
## <a name="example"></a>Beispiel  
 Der folgende Code zeigt, wie die kleinere von zwei Ausdrücken abgerufen wird.  
  
```JavaScript  
var x = Math.min(107 - 3, 48 * 90);  
document.write(x);  
  
// Output:  
// 104  
```  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Siehe auch  
 [Math.max-Funktion](../../javascript/reference/math-max-function-javascript.md)