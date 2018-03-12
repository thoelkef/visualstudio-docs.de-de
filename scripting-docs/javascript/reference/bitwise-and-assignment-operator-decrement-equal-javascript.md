---
title: Bitweise AND-Zuweisungsoperator (&amp;=) (JavaScript) | Microsoft Docs
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
- '&='
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- '&= operator'
- assignment operators, bitwise [JavaScript]
- AND operator
- bitwise operators, AND operator
ms.assetid: e7e2eabb-4fc1-4fdc-9dd8-1e6d715371fa
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: dfd2a77e66296cafc6c8403570f0536e1333e081
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="bitwise-and-assignment-operator-amp-javascript"></a>Bitweise AND-Zuweisungsoperator (&amp;=) (JavaScript)
Legt das Ergebnis einer bitweisen AND-Operation für den Wert einer Variablen und den Wert eines Ausdrucks. Die Variable und des Ausdrucks werden als 32-Bit-Ganzzahlen behandelt.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
result &= expression  
```  
  
## <a name="parameters"></a>Parameter  
 `result`  
 Beliebige Variable.  
  
 `expression`  
 Beliebiger Ausdruck.  
  
## <a name="remarks"></a>Hinweise  
 Mithilfe dieser Operator entspricht der Angabe:  
  
```JavaScript  
result = result & expression  
```  
  
 Die [bitweisen und-Operator (&)](../../javascript/reference/bitwise-and-operator-decrement-javascript.md) prüft die binäre Darstellung der Werte von `result` und `expression` an und führt eine bitweise AND-Operation darauf. Die Ausgabe dieses Vorgangs verhält sich wie folgt:  
  
```JavaScript  
// 9 is 00000000000000000000000000001001  
var expr1 = 9;  
  
// 5 is 00000000000000000000000000000101  
var expr2 = 5;  
  
// 1 is 00000000000000000000000000000001  
expr1 &= expr2;  
  
document.write(expr1);  
```  
  
 Beide Ausdrücke in eine Ziffer 1 haben immer das Ergebnis einer "1" wurde an dieser Stelle. Andernfalls hat das Ergebnis 0 an dieser Stelle.  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Siehe auch  
 [Bitweiser AND-Operator (&)](../../javascript/reference/bitwise-and-operator-decrement-javascript.md)   
 [Operatorrangfolge](../../javascript/operator-subtractprecedence-javascript.md)   
 [Zusammenfassung der Operatoren (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)