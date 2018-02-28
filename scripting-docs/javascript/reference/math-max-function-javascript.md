---
title: Math.Max-Funktion (JavaScript) | Microsoft Docs
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
- max
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- max method
ms.assetid: f3ea1b8a-5fd0-482a-971b-b7f8e2b9b7eb
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: adf66164346f3802d92f8e0de82356df49bad5fa
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="mathmax-function-javascript"></a>Math.max-Funktion (JavaScript)
Gibt die größere eines Satzes von angegebenen numerischen Ausdrücken zurück.  
  
## <a name="syntax"></a>Syntax  
  
```  
Math.max([number1[, number2[... [, numberN]]]])   
```  
  
## <a name="remarks"></a>Hinweise  
 Das optionale `number1, number2, ..., numberN` Argumente sind numerische Ausdrücke ausgewertet werden soll.  
  
 Wenn keine Argumente bereitgestellt werden, ist der Rückgabewert gleich [Number. NEGATIVE_INFINITY](../../javascript/reference/number-constants-javascript.md). Wenn eines der Argumente ist `NaN`, der Rückgabewert ist ebenfalls `NaN`.  
  
## <a name="example"></a>Beispiel  
 Der folgende Code zeigt, wie die größere von zwei Ausdrücken abgerufen wird.  
  
```JavaScript  
var x = Math.max(107 - 3,  48 * 90);  
document.write(x);  
  
// Output:  
// 4320  
  
```  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Siehe auch  
 [Math.min-Funktion](../../javascript/reference/math-min-function-javascript.md)