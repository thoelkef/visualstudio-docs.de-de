---
title: Bitweiser AND-Operator (&amp;) (JavaScript) | Microsoft Docs
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
- '&'
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- assignment operators, bitwise [JavaScript]
- '& operator, about & operator'
- AND operator
- '& operator'
- bitwise operators, AND operator
- '& operator, bitwise operators'
ms.assetid: a8c17a55-2599-4518-98d7-671699f4d5f3
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fa8b3eec0cbd7c172d08b16120fb54f3be3c6a48
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
ms.locfileid: "24634240"
---
# <a name="bitwise-and-operator-amp-javascript"></a>Bitweiser AND-Operator (&amp;) (JavaScript)
Führt eine bitweise AND-Operation für zwei 32-Bit-Ausdrücke.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
result = expression1 & expression2  
```  
  
## <a name="parameters"></a>Parameter  
 `result`  
 Das Ergebnis des Vorgangs.  
  
 `expression1`  
 Beliebiger Ausdruck.  
  
 `expression2`  
 Beliebiger Ausdruck.  
  
## <a name="remarks"></a>Hinweise  
 Die `&` führt eine bitweise AND‑Operation für jede der Bits von zwei 32-Bit-Ausdrücken. Wenn beide Bits 1 sind, ist das Ergebnis 1. Das Ergebnis ist, andernfalls 0.  
  
|Bit1|Bit2|And-Wert|  
|----------|----------|-----------------|  
|0|0|0|  
|1|1|1|  
|1|0|0|  
|0|1|0|  
  
 Den folgenden Beispielen wird veranschaulicht, wie die `&` Operator.  
  
```JavaScript  
// 9 is 00000000000000000000000000001001  
var expr1 = 9;  
  
// 5 is 00000000000000000000000000000101  
var expr2 = 5;  
  
// 1 is 00000000000000000000000000000001  
var result = expr1 & expr2;  
  
document.write(result);  
// Output: 1  
```  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Siehe auch  
 [Bitweise AND-Zuweisungsoperator (& =)](../../javascript/reference/bitwise-and-assignment-operator-decrement-equal-javascript.md)   
 [Operatorrangfolge](../../javascript/operator-subtractprecedence-javascript.md)   
 [Zusammenfassung der Operatoren (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)