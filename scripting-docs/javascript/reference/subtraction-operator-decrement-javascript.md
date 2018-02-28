---
title: Subtraktionsoperator (-) (JavaScript) | Microsoft Docs
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
- '-'
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- '- operator, about - operator'
- '- operator'
- negation operator
- subtraction operator, syntax
- arithmetic operators, subtraction
- operators, subtraction
ms.assetid: cd0681d3-15cd-49fe-b4dd-e087de55d778
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fb79aab0a57c733871dbfc73ac96c7ddbf4db37c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="subtraction-operator---javascript"></a>Subtraktionsoperator (-) (JavaScript)
Subtrahiert den Wert eines Ausdrucks von einem anderen oder unäre Negation von einem einzelnen Ausdruck enthält.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
result = number1 - number2;  
```  
  
## <a name="parameters"></a>Parameter  
 *Ergebnis*  
 Beliebige numerische Variable.  
  
 `number`  
 Ein beliebiger numerischer Ausdruck.  
  
 `number1`  
 Ein beliebiger numerischer Ausdruck.  
  
 `number2`  
 Ein beliebiger numerischer Ausdruck.  
  
## <a name="remarks"></a>Hinweise  
 In der Syntax 1 wird die  **-**  Operator wird der arithmetische Subtraktion-Operator verwendet, um den Unterschied zwischen zwei Zahlen zu suchen. In der Syntax 2 wird die  **-**  Operator wird als der unäre Negationsoperator verwendet, um den negativen Wert eines Ausdrucks anzugeben.  
  
 Bei Syntax 2 wird werden wie alle unäre Operatoren für Ausdrücke wie folgt ausgewertet:  
  
-   Wenn undefined zugewiesen oder `null` Ausdrücke ein Laufzeitfehler ausgelöst wird.  
  
-   Objekte werden in Zeichenfolgen konvertiert.  
  
-   Zeichenfolgen werden nach Möglichkeit in Zahlen konvertiert. Wenn dies nicht der Fall ist, wird ein Laufzeitfehler ausgelöst.  
  
-   Boolesche Werte werden als Zahlen (0, wenn "false", 1, wenn "true") behandelt.  
  
 Der Operator wird auf die daraus resultierende Zahl angewendet. In der Syntax 2, wenn die daraus resultierende Zahl ungleich NULL ist, *Ergebnis* entspricht die daraus resultierende Zahl mit umgekehrtem Vorzeichen. Wenn die daraus resultierende Zahl Null ist, *Ergebnis* 0 (null).  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Siehe auch  
 [Subtraktionszuweisungsoperator (-)](../../javascript/reference/subtraction-assignment-operator-decrement-equal-javascript.md)   
 [Operatorrangfolge](../../javascript/operator-subtractprecedence-javascript.md)   
 [Zusammenfassung der Operatoren (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)