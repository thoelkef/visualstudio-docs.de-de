---
title: Bitweiser Linksschiebeoperator (&lt;&lt;) (JavaScript) | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: <<
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- << operator
- left shift operators
- << operator, about << operator
- bitwise operators, Left Shift operator
ms.assetid: 18148596-7b86-4add-aeef-106991c69435
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9d63fc50659695f518e581edbed67c009b36577f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="bitwise-left-shift-operator-ltlt-javascript"></a>Bitweiser Linksschiebeoperator (&lt;&lt;) (JavaScript)
Links verschiebt die Bits eines Ausdrucks.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
result = expression1 << expression2  
```  
  
## <a name="parameters"></a>Parameter  
 *Ergebnis*  
 Beliebige Variable.  
  
 *expression1*  
 Beliebiger Ausdruck.  
  
 *expression2*  
 Beliebiger Ausdruck.  
  
## <a name="remarks"></a>Hinweise  
 Die  **<<**  Operator verschiebt die Bits eines *expression1* links durch die Anzahl der Bits, die im angegebenen *expression2*. Zum Beispiel:  
  
```JavaScript  
var temp  
temp = 14 << 2  
```  
  
 Die Variable *Temp* verfügt über einen Wert von 56, da 14 (binär 00001110), um zwei Bits nach links, 56 (binär 00111000 verschoben).  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Siehe auch  
 [Left Shift-Zuweisungsoperator (<\<=)](../../javascript/reference/left-shift-assignment-operator-decrement-equal-javascript.md)   
 [Bitweiser Rechtsschiebeoperator (>>)](../../javascript/reference/bitwise-right-shift-operator-decrement-javascript.md)   
 [Vorzeichenloser Rechtsschiebeoperator (>>>)](../../javascript/reference/unsigned-right-shift-operator-decrement-javascript.md)   
 [Operatorrangfolge](../../javascript/operator-subtractprecedence-javascript.md)   
 [Zusammenfassung der Operatoren (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)