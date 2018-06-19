---
title: IsNaN-Funktion (JavaScript) | Microsoft Docs
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
- isNaN
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- isNaN method
ms.assetid: 5af4eb29-72f6-484f-93bd-04ae1261f849
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7b7e6d3687e795ea5d5e38308a8af0d73ba7f5ff
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
ms.locfileid: "24637620"
---
# <a name="isnan-function-javascript"></a>isNaN-Funktion (JavaScript)
Gibt einen booleschen Wert zurück, der angibt, ob ein Wert der reservierte Wert `NaN` ist (keine Zahl).  
  
## <a name="syntax"></a>Syntax  
  
```  
isNaN(numValue)   
```  
  
## <a name="return-value"></a>Rückgabewert  
 `true`, wenn der in den `Number`-Typ konvertierte Wert `NaN` lautet, andernfalls `false`.  
  
## <a name="remarks"></a>Hinweise  
 Die erforderliche `numValue` ist der Wert, der für getestet werden `NaN`.  
  
 In der Regel verwenden Sie diese Methode zum Testen der Rückgabewerte von den Methoden `parseInt` und `parseFloat`.  
  
 Alternativ können Sie eine Variable enthält `NaN` oder einen anderen Wert kann mit sich selbst verglichen werden. Wenn es als ungleich verglichen werden, ist es `NaN`. Grund hierfür ist, `NaN` ist der einzige Wert, der ungleich sich selbst ist.  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Gilt für**: [Global-Objekt](../../javascript/reference/global-object-javascript.md)  
  
## <a name="example"></a>Beispiel  
  
```JavaScript  
// Returns false.  
isNaN(100);  
  
// Returns false.  
isNaN("100");  
  
// Returns true.  
isNaN("ABC");  
  
// Returns true.  
isNaN("10C");  
  
// Returns true.  
isNaN("abc123");  
  
// Returns true.  
isNaN(Math.sqrt(-1));           
```  
  
## <a name="see-also"></a>Siehe auch  
 [IsFinite-Funktion](../../javascript/reference/isfinite-function-javascript.md)   
 [NaN-Konstante](../../javascript/reference/nan-constant-javascript.md)   
 [ParseFloat-Funktion](../../javascript/reference/parsefloat-function-javascript.md)   
 [parseInt-Funktion](../../javascript/reference/parseint-function-javascript.md)