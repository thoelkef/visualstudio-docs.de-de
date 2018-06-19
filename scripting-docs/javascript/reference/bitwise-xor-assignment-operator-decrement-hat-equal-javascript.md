---
title: Bitweiser XOR-Zuweisungsoperator (^ =) (JavaScript) | Microsoft Docs
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
- ^=
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- ^= operator, about ^= operator
- assignment operators, bitwise [JavaScript]
- bitwise operators, XOR operator
- XOR operator
- ^= operator
ms.assetid: a6ded216-27b6-4fc4-a51b-7d10cc6f820c
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 511ff5b3346bb2b04bf4c24cb3e0b715b2ccf4c5
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
ms.locfileid: "24634030"
---
# <a name="bitwise-xor-assignment-operator--javascript"></a>Bitweiser XOR-Zuweisungsoperator (^=) (JavaScript)
Führt eine bitweise XOR-Operation für eine Variable und einen Ausdruck durch und weist das Ergebnis der Variablen zu.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
result ^= expression  
```  
  
## <a name="parameters"></a>Parameter  
 *Ergebnis*  
 Beliebige Variable.  
  
 *Ausdruck*  
 Beliebiger Ausdruck.  
  
## <a name="remarks"></a>Hinweise  
 Mithilfe der  **^=**  Operator ist derselbe, als wenn:  
  
```JavaScript  
result = result ^ expression  
```  
  
 Die  **^=**  Operator die binäre Darstellung der Werte von zwei Ausdrücken und führt eine bitweise exklusive OR-Operation darauf. Das Ergebnis dieses Vorgangs verhält sich wie folgt:  
  
```JavaScript  
0101    (result)  
1100    (expression)  
----  
1001    (result)  
```  
  
 Wenn eine und nur einer der Ausdrücke eine "1" wurde in eine Ziffer, einen "1" das Ergebnis an dieser Stelle wurde. Andernfalls hat das Ergebnis 0 an dieser Stelle.  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Siehe auch  
 [Bitweiser XOR-Operator (^)](../../javascript/reference/bitwise-xor-operator-decrement-hat-javascript.md)   
 [Operatorrangfolge](../../javascript/operator-subtractprecedence-javascript.md)   
 [Zusammenfassung der Operatoren (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)