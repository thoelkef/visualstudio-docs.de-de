---
title: Vergleichsoperatoren (JavaScript) | Microsoft Docs
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
- Comparison
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- comparison operators, script
- greater than operator
- comparison operators
- greater than or equal to operator
- inequity operator
- identity operator
ms.assetid: 084f90f0-d010-47cf-96dd-13d637fc9b68
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 067d570523fc2241b4f2e0442785a49aedb15200
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="comparison-operators-javascript"></a>Vergleichsoperatoren (JavaScript)
Geben einen booleschen Wert zurück, der das Ergebnis des Vergleichs angibt.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
expression1 comparisonoperator expression2  
```  
  
## <a name="parameters"></a>Parameter  
 `expression1`  
 Beliebiger Ausdruck.  
  
 `comparisonoperator`  
 Jeder Vergleichsoperator.  
  
 `expression2`  
 Beliebiger Ausdruck.  
  
## <a name="remarks"></a>Hinweise  
 Beim Vergleichen von Zeichenfolgen, [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] den Unicode-Zeichenwert des Zeichenfolgenausdrucks verwendet.  
  
 Im folgenden beschrieben, wie die verschiedenen Gruppen von Operatoren abhängig von den Typen und Werte des Verhalten `expression1` und `expression2`:  
  
 Relationale Operatoren: `<`, `>`, `<=`,`>=`  
  
-   Beide konvertieren `expression1` und `expression2` in Zahlen.  
  
-   Wenn beide Ausdrücke Zeichenfolgen sind, führen Sie einen Zeichenfolgenvergleich.  
  
-   Wenn einer der Ausdrücke ist `NaN`, den Rückgabetyp `false`.  
  
-   Negative 0 (null) entspricht der positiven NULL.  
  
-   Minus unendlich ist kleiner als alles, was sich selbst eingeschlossen.  
  
-   Plus unendlich ist größer als alles, was sich selbst eingeschlossen.  
  
 Gleichheitsoperatoren: `==`,`!=`  
  
-   Wenn die Typen der beiden Ausdrücke unterschiedlich sind, versucht, die sie in eine Zeichenfolge, eine Zahl oder ein boolescher Wert zu konvertieren.  
  
-   `NaN`stimmt nicht mit etwas sich selbst eingeschlossen.  
  
-   Negative 0 (null) entspricht der positiven NULL.  
  
-   `null`beide gleich `null` und `undefined`.  
  
-   Werte werden als gleich betrachtet werden identische Zeichenfolgen, numerisch äquivalente Zahlen, die dasselbe Objekt, das identische boolesche Werte oder (wenn verschiedene Typen) können sie in einem solchen Fall umgewandelt werden.  
  
-   Alle anderen Vergleichs wird als ungleich betrachtet.  
  
 Identity-Operatoren: `===`,`!==`  
  
 Diese Operatoren Verhalten sich die Gleichheitsoperatoren identisch, außer, dass keine Konvertierung ausgeführt wird. Wenn die Typen der beiden Ausdrücke nicht identisch sind, diese Ausdrücke stets `false`.  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Siehe auch  
 [Operatorrangfolge](../../javascript/operator-subtractprecedence-javascript.md)   
 [Zusammenfassung der Operatoren (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)