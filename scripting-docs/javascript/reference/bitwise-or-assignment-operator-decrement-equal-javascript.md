---
title: Bitweiser OR -Zuweisungsoperator (| =) (JavaScript) | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: '|='
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- assignment operators, bitwise [JavaScript]
- '|= operator'
- bitwise operators, OR operator
- OR operator
ms.assetid: 9b424ff6-4442-4621-b3b6-83e7fd1e5cd5
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8ce9cadcf07906c9eba6749706620ae6293c2682
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="bitwise-or-assignment-operator--javascript"></a>Bitweiser OR-Zuweisungsoperator (|=) (JavaScript)
Führt eine bitweise OR-Operation für den Wert einer Variablen und den Wert eines Ausdrucks durch und weist das Ergebnis der Variablen zu.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
result |= expression  
```  
  
## <a name="parameters"></a>Parameter  
 *Ergebnis*  
 Beliebige Variable.  
  
 *Ausdruck*  
 Beliebiger Ausdruck.  
  
## <a name="remarks"></a>Hinweise  
 Mithilfe dieses Operators ist genau derselbe, als wenn:  
  
```JavaScript  
result = result | expression  
```  
  
 Die **&#124; =** Operator prüft die binäre Darstellung der Werte von *Ergebnis* und *Ausdruck* an und führt eine bitweise OR-Operation für sie. Das Ergebnis dieses Vorgangs verhält sich wie folgt:  
  
```JavaScript  
0101    (result)  
1100    (expression)  
----  
1101    (output)  
```  
  
 Jedes Mal, wenn entweder der Ausdrücke eine "1" wurde in eine Ziffer, das Ergebnis einer "1" wurde an dieser Stelle. Andernfalls hat das Ergebnis 0 an dieser Stelle.  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Siehe auch  
 [Bitweise OR-Operator (&#124;)](../../javascript/reference/bitwise-or-operator-decrement-javascript.md)   
 [Operatorrangfolge](../../javascript/operator-subtractprecedence-javascript.md)   
 [Zusammenfassung der Operatoren (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)