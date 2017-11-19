---
title: Rightshiftzuweisungsoperator (&gt;&gt;=) (JavaScript) | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: '>>='
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- '>>= operator [JavaScript]'
- right shift operators [JavaScript]
- assignment operators, JavaScript
ms.assetid: 8c1f7f90-e3ac-42ee-94f2-5ccc47d7aef6
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cb93d146ad00bd19c09fb4cfca3af776a11f245d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="right-shift-assignment-operator-gtgt-javascript"></a>Rightshiftzuweisungsoperator (&gt;&gt;=) (JavaScript)
Verschiebt den Wert einer Variablen um die Anzahl der Bits, die im Wert eines Ausdrucks angegeben sind, unter Beibehaltung des Vorzeichens nach rechts und weist das Ergebnis der Variablen zu.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
result >>= expression  
```  
  
## <a name="parameters"></a>Parameter  
 *Ergebnis*  
 Beliebige Variable.  
  
 *Ausdruck*  
 Beliebiger Ausdruck.  
  
## <a name="remarks"></a>Hinweise  
 Mithilfe der  **>>=**  Operator ist derselbe, als wenn:  
  
```JavaScript  
result = result >> expression  
```  
  
 Die  **>>=**  Operator verschiebt die Bits eines *Ergebnis* nach rechts um die Anzahl der Bits, die im angegebenen *Ausdruck*. Das Vorzeichenbit von *Ergebnis* wird verwendet, um die Ziffern von Links zu füllen. Ziffern rechts verschobene werden verworfen. Nach der Auswertung des folgenden Codes beispielsweise *Temp* verfügt über einen Wert von – 4: 14 (binär 11110010) verschoben, zwei Bits entspricht-4 (11111100 binär).  
  
```JavaScript  
var temp  
temp = -14  
temp >>= 2  
```  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Siehe auch  
 [Bitweiser Linksschiebeoperator (<\<)](../../javascript/reference/bitwise-left-shift-operator-decrement-javascript.md)   
 [Bitweiser Rechtsschiebeoperator (>>)](../../javascript/reference/bitwise-right-shift-operator-decrement-javascript.md)   
 [Vorzeichenloser Rechtsschiebeoperator (>>>)](../../javascript/reference/unsigned-right-shift-operator-decrement-javascript.md)   
 [Operatorrangfolge](../../javascript/operator-subtractprecedence-javascript.md)   
 [Zusammenfassung der Operatoren (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)