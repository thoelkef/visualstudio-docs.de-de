---
title: Additionsoperator (+) (JavaScript) | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: +
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- arithmetic operators, addition
- strings [Visual Studio], concatenating
- concatenation operators, vs. addition operator
- addition operator
- + operator
ms.assetid: ec1237d3-e78b-4e77-bd7d-c0204cf03acd
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 70ff02b1f234da7b88d28e66da82262ccef7bfaf
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="addition-operator--javascript"></a>Additionsoperator (+) (JavaScript)
Fügt den Wert eines numerischen Ausdrucks in einen anderen oder verkettet zwei Zeichenfolgen.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
result = expression1 + expression2  
```  
  
## <a name="parameters"></a>Parameter  
 `result`  
 Beliebige Variable.  
  
 `expression1`  
 Beliebiger Ausdruck.  
  
 `expression2`  
 Beliebiger Ausdruck.  
  
## <a name="remarks"></a>Hinweise  
 Die Typen der beiden Ausdrücke bestimmen das Verhalten der  **+**  Operator.  
  
|If|Then|  
|--------|----------|  
|Beide Ausdrücke sind numerische oder boolesche|Hinzufügen|  
|Beide Ausdrücke sind Zeichenfolgen.|Verketten|  
|Ein Ausdruck ist numerisch und das andere ist eine Zeichenfolge|Verketten|  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Siehe auch  
 [Additionszuweisungsoperator (+=)](../../javascript/reference/addition-assignment-operator-decrement-equal-javascript.md)   
 [Operatorrangfolge](../../javascript/operator-subtractprecedence-javascript.md)   
 [Zusammenfassung der Operatoren (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)