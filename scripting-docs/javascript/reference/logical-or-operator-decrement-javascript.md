---
title: Logischen Operator OR (||) (JavaScript) | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- '||'
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- '|| operator'
- logical OR operator
ms.assetid: 95295331-6269-4311-8391-dc1c68e116ab
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 80c8e1bcae57e13642a0c77ae75c7c2aac58ace6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
ms.locfileid: "24638730"
---
# <a name="logical-or-operator--javascript"></a>Logischer OR-Operator (||) (JavaScript)
Führt eine logische Disjunktion zweier Ausdrücke durch.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
result = expression1 || expression2  
```  
  
## <a name="parameters"></a>Parameter  
 *Ergebnis*  
 Beliebige Variable.  
  
 *expression1*  
 Beliebiger Ausdruck.  
  
 *expression2*  
 Beliebiger Ausdruck.  
  
## <a name="remarks"></a>Hinweise  
 Wenn eine oder beide Ausdrücke **"true"**, *Ergebnis* ist **"true"**. Die folgende Tabelle veranschaulicht wie *Ergebnis* bestimmt wird:  
  
|Wenn `expression1` ist|Und `expression2` ist|Die `result` ist|  
|-------------------------|--------------------------|---------------------|  
|True|True|True|  
|True|False|True|  
|False|True|True|  
|False|False|False|  
  
 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] verwendet die folgenden Regeln für die Konvertierung nicht boolescher Werte in boolesche Werte:  
  
-   Alle Objekte gelten als "true".  
  
-   Zeichenfolgen werden als "false" betrachtet, wenn sie leer sind.  
  
-   `null`und undefinierte gelten als "false".  
  
-   Zahlen sind, false, wenn und nur bei, sie sind 0.  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Siehe auch  
 [Operatorrangfolge](../../javascript/operator-subtractprecedence-javascript.md)   
 [Zusammenfassung der Operatoren (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)