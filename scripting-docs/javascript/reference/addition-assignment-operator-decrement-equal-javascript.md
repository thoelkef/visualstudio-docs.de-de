---
title: Additionszuweisungsoperator (+=) (JavaScript) | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: +=
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- addition assignment operator (+=)
- += operator
- assignment operators, JavaScript
ms.assetid: 8517d05c-38b0-4107-bea4-253eb420f438
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 38d86c537dda90dd7f44923b97384b3609dad5ba
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="addition-assignment-operator--javascript"></a>Additionszuweisungsoperator (+=) (JavaScript)
Addiert den den Wert eines Ausdrucks mit dem Wert einer Variable und weist das Ergebnis der Variablen zu.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
result += expression   
```  
  
## <a name="parameters"></a>Parameter  
 `result`  
 Beliebige Variable.  
  
 `expression`  
 Beliebiger Ausdruck.  
  
## <a name="remarks"></a>Hinweise  
 Mithilfe dieser Operator entspricht genau der Angabe: `result = result + expression`.  
  
 Die Typen der beiden Ausdrücke bestimmen das Verhalten der `+=` Operator.  
  
|If|Then|  
|--------|----------|  
|Beide Ausdrücke sind numerische oder boolesche|Hinzufügen|  
|Beide Ausdrücke sind Zeichenfolgen.|Verketten|  
|Ein Ausdruck ist numerisch und das andere ist eine Zeichenfolge|Verketten|  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Siehe auch  
 [Additionsoperator (+)](../../javascript/reference/addition-operator-decrement-javascript.md)   
 [Operatorrangfolge](../../javascript/operator-subtractprecedence-javascript.md)   
 [Zusammenfassung der Operatoren (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)