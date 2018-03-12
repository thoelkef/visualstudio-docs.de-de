---
title: Logischer NOT-Operator (!) (JavaScript) | Microsoft Docs
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
- '!'
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Logical NOT operator
- '! operator'
- '! operator, about ! operator'
ms.assetid: 68c3dc71-ae95-4293-9155-67405846d71d
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 29c27b9cd670989eb2112de5067e68bd09d76903
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="logical-not-operator--javascript"></a>Logischer NOT-Operator (!) (JavaScript)
Führt eine logische Negation für einen Ausdruck durch.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
result = !expression  
```  
  
## <a name="parameters"></a>Parameter  
 *Ergebnis*  
 Beliebige Variable.  
  
 *Ausdruck*  
 Beliebiger Ausdruck.  
  
## <a name="remarks"></a>Hinweise  
 Die folgende Tabelle veranschaulicht wie *Ergebnis* bestimmt wird.  
  
|Wenn `expression` ist|Klicken Sie dann `result` ist|  
|------------------------|----------------------|  
|True|False|  
|False|True|  
  
 Alle unäre Operatoren, wie z. B. die **!** Operator Auswerten von Ausdrücken wie folgt:  
  
-   Wenn undefined zugewiesen oder `null` Ausdrücke ein Laufzeitfehler ausgelöst wird.  
  
-   Objekte werden in Zeichenfolgen konvertiert.  
  
-   Zeichenfolgen werden nach Möglichkeit in Zahlen konvertiert. Wenn dies nicht der Fall ist, wird ein Laufzeitfehler ausgelöst.  
  
-   Boolesche Werte werden als Zahlen (0, wenn "false", 1, wenn "true") behandelt.  
  
 Der Operator wird auf die daraus resultierende Zahl angewendet.  
  
 Für die **!** Operator, wenn *Ausdruck* ungleich NULL ist *Ergebnis* 0 (null). Wenn *Ausdruck* ist 0 (null), *Ergebnis* ist 1.  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Siehe auch  
 [Bitweiser NOT-Operator (~)](../../javascript/reference/bitwise-not-operator-decrement-tilde-javascript.md)   
 [Operatorrangfolge](../../javascript/operator-subtractprecedence-javascript.md)   
 [Zusammenfassung der Operatoren (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)