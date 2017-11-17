---
title: Vorzeichenloser Right Shift-Zuweisungsoperator (&gt;&gt;&gt;=) (JavaScript) | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: '>>>='
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- '>>>= operator'
- unsigned right shift assignment operator (>>>=)
- assignment operators, JavaScript
ms.assetid: f67c3737-7d39-41ae-9c11-8b16d38f6179
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1272cbb58645df605743c6790642cd0e295442aa
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="unsigned-right-shift-assignment-operator-gtgtgt-javascript"></a>Vorzeichenloser Right Shift-Zuweisungsoperator (&gt;&gt;&gt;=) (JavaScript)
Verschiebt den Wert einer Variablen um die Anzahl der Bits, die im Wert eines Ausdrucks angegeben sind, nach rechts, ohne das Vorzeichen beizubehalten, und weist das Ergebnis der Variablen zu.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
result >>>= expression  
```  
  
## <a name="parameters"></a>Parameter  
 *Ergebnis*  
 Beliebige Variable.  
  
 *Ausdruck*  
 Beliebiger Ausdruck.  
  
## <a name="remarks"></a>Hinweise  
 Mithilfe der >>> = Operator ist identisch mit der folgenden Schritte:  
  
```JavaScript  
result = result >>> expression  
```  
  
 Die  **>>>=**  Operator verschiebt die Bits eines *Ergebnis* nach rechts um die Anzahl der Bits, die im angegebenen *Ausdruck*. Nullen (0) werden von der linken Seite ausgefüllt. Ziffern rechts verschobene werden verworfen. Zum Beispiel:  
  
```JavaScript  
var temp  
temp = -14  
temp >>>= 2  
```  
  
 Die Variable *Temp* hat einen Anfangswert von-14 (11111111 11111111 11111111 11110010 zwei des Komplement binär). Wenn zwei Bits verschoben wird, entspricht dem Wert 1073741820 (00111111 11111111 11111111 11111100 binär).  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Siehe auch  
 [Vorzeichenloser Rechtsschiebeoperator (>>>)](../../javascript/reference/unsigned-right-shift-operator-decrement-javascript.md)   
 [Bitweiser Linksschiebeoperator (<\<)](../../javascript/reference/bitwise-left-shift-operator-decrement-javascript.md)   
 [Bitweiser Rechtsschiebeoperator (>>)](../../javascript/reference/bitwise-right-shift-operator-decrement-javascript.md)   
 [Operatorrangfolge](../../javascript/operator-subtractprecedence-javascript.md)   
 [Zusammenfassung der Operatoren (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)