---
title: Bitweiser NOT-Operator (~) (JavaScript) | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: ~
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- NOT operator
- bitwise operators, NOT operator
ms.assetid: 39f92474-fe05-4a8b-9ad8-caca93f82bca
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: aec64b055b260efb7a4b0d952aed9b3a5d7ddc82
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="bitwise-not-operator--javascript"></a>Bitweiser NOT-Operator (~) (JavaScript)
Führt eine bitweise NOT-Operation (Negation) für einen Ausdruck durch.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
result = ~ expression  
```  
  
## <a name="parameters"></a>Parameter  
 *Ergebnis*  
 Beliebige Variable.  
  
 *Ausdruck*  
 Beliebiger Ausdruck.  
  
## <a name="remarks"></a>Hinweise  
 Alle unäre Operatoren, wie z. B. die `~` Operator Auswerten von Ausdrücken wie folgt:  
  
-   Wenn undefined zugewiesen oder `null` Ausdrücke ein Laufzeitfehler ausgelöst wird.  
  
-   Objekte werden in Zeichenfolgen konvertiert.  
  
-   Zeichenfolgen werden nach Möglichkeit in Zahlen konvertiert. Wenn dies nicht der Fall ist, wird ein Laufzeitfehler ausgelöst.  
  
-   Boolesche Werte werden als Zahlen (0, wenn "false", 1, wenn "true") behandelt.  
  
 Der Operator wird auf die daraus resultierende Zahl angewendet.  
  
 Die `~` Operator prüft die binäre Darstellung der Werte des Ausdrucks und führt eine bitweise Negation-Operation.  
  
 Eine beliebige Ziffer, die 1 im Ausdruck ist, wird eine 0 im Ergebnis. Eine beliebige Ziffer, das 0 im Ausdruck wird einer im Ergebnis 1.  
  
 Das folgende Beispiel veranschaulicht die Verwendung des bitweisen NOT-Operator (~).  
  
```  
var temp = ~5;  
```  
  
 Der resultierende Wert ist-6, wie in der folgenden Tabelle gezeigt.  
  
|Ausdruck|Binärwert (Zweierkomplement)|Dezimalwert|  
|----------------|---------------------------------------|-------------------|  
|5|00000000 00000000 00000000 00000101|5|  
|~5|11111111 11111111 11111111 11111010|-6|  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Siehe auch  
 [Logischer NOT-Operator (!)](../../javascript/reference/logical-not-operator-decrement-exclpt-javascript.md)   
 [Operatorrangfolge](../../javascript/operator-subtractprecedence-javascript.md)   
 [Zusammenfassung der Operatoren (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)