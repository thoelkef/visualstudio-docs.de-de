---
title: Kommaoperator (,) (JavaScript) | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: '%2C'
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: comma operator
ms.assetid: 699fa0bf-cd0a-45ee-a291-2fbed4ecd470
caps.latest.revision: "13"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2cb504beefc5ce4c260ec8296e2cf097e17d349e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="comma-operator--javascript"></a>Kommaoperator (,) (JavaScript)
Bewirkt die sequenzielle Ausführung von zwei Ausdrücken.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
expression1, expression2  
```  
  
## <a name="parameters"></a>Parameter  
 `expression1`  
 Beliebiger Ausdruck.  
  
 `expression2`  
 Beliebiger Ausdruck.  
  
## <a name="remarks"></a>Hinweise  
 Die `,` Operator bewirkt, dass die Ausdrücke, die in der Reihenfolge von links nach rechts ausgeführt werden. Eine übliche Verwendung für die `,` Operator im Inkrementausdruck ist eine `for` Schleife. Zum Beispiel:  
  
```JavaScript  
j=25;  
for (i = 0; i < 10; i++, j++)  
{  
   k = i + j;  
}  
```  
  
 Die `for` -Anweisung können nur einen einzelnen Ausdruck am Ende jeder Pass-through einer Schleife ausgeführt werden. Die `,` Operators können mehrere Ausdrücke als ein einziger Ausdruck behandelt werden, damit beide Variablen inkrementiert werden können.  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Siehe auch  
 [für die Anweisung](../../javascript/reference/for-statement-javascript.md)   
 [Operatorrangfolge](../../javascript/operator-subtractprecedence-javascript.md)   
 [Zusammenfassung der Operatoren (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)