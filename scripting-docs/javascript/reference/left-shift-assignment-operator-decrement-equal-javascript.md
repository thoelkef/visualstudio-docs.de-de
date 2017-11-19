---
title: Left Shift-Zuweisungsoperator (&lt;&lt;=) (JavaScript) | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: <<=
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- <<= operator [JavaScript]
- left shift assignment operator (<<=) [JavaScript]
- left shift operators [JavaScript]
- assignment operators, JavaScript
ms.assetid: 9f30ff46-48cc-4931-b260-edef31ff0076
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bf00545947f6a84f99c519fcbed887b84c179fb5
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="left-shift-assignment-operator-ltlt-javascript"></a>Left Shift-Zuweisungsoperator (&lt;&lt;=) (JavaScript)
Verschiebt die angegebene Anzahl von Bits nach links und weist das Ergebnis auf `result`. Die Bits, die durch den Vorgang frei gewordene werden mit 0 aufgefüllt.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
result <<= expression  
```  
  
## <a name="parameters"></a>Parameter  
 `result`  
 Beliebige Variable.  
  
 `expression`  
 Die Anzahl der Bits verschoben.  
  
## <a name="remarks"></a>Hinweise  
 Mithilfe der `<<=` Operator entspricht der Angabe`result = result << expression`  
  
 Im folgenden Beispiel wird die Verwendung des `<<=`-Operators gezeigt.  
  
```JavaScript  
// 14 is 00000000000000000000000000001110  
var temp = 14;  
temp <<= 2;   
document.write(temp);  
// 56 is 00000000000000000000000000111000  
Output: 56  
```  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Siehe auch  
 [Bitweiser Linksschiebeoperator (<\<)](../../javascript/reference/bitwise-left-shift-operator-decrement-javascript.md)   
 [Bitweiser Rechtsschiebeoperator (>>)](../../javascript/reference/bitwise-right-shift-operator-decrement-javascript.md)   
 [Vorzeichenloser Rechtsschiebeoperator (>>>)](../../javascript/reference/unsigned-right-shift-operator-decrement-javascript.md)   
 [Operatorrangfolge](../../javascript/operator-subtractprecedence-javascript.md)   
 [Zusammenfassung der Operatoren (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)