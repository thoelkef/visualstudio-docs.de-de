---
title: Vorzeichenloser Rechtsschiebeoperator (&gt;&gt;&gt;) (JavaScript) | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: '>>>'
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- unsigned right shift operator (>>>)
- '>>> operator'
ms.assetid: df48bdfc-8741-46ab-b681-449da57ac95c
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: efb873bedc0a64089c7ec892d6378b4869c0ca21
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="unsigned-right-shift-operator-gtgtgt-javascript"></a>Vorzeichenloser Rechtsschiebeoperator (&gt;&gt;&gt;) (JavaScript)
Rechts verschiebt die Bits eines Ausdrucks ohne das Vorzeichen beizubehalten.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
result = expression1 >>> expression2  
```  
  
## <a name="parameters"></a>Parameter  
 *Ergebnis*  
 Beliebige Variable.  
  
 *expression1*  
 Beliebiger Ausdruck.  
  
 *expression2*  
 Beliebiger Ausdruck.  
  
## <a name="remarks"></a>Hinweise  
 Die  **>>>**  Operator verschiebt die Bits eines *expression1* nach rechts um die Anzahl der Bits, die im angegebenen *expression2*. Nullen (0) werden von der linken Seite ausgefüllt. Ziffern rechts verschobene werden verworfen. Zum Beispiel:  
  
```JavaScript  
var temp  
temp = -14 >>> 2  
```  
  
 Die Variable *Temp* hat einen Anfangswert-14 (11111111 11111111 11111111 11110010 zwei des Komplement binär). Wenn es verschoben zwei Bits ist, entspricht dem Wert 1073741820 (00111111 11111111 11111111 11111100 binär).  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Siehe auch  
 [Vorzeichenloser Right Shift-Zuweisungsoperator (>>> =)](../../javascript/reference/unsigned-right-shift-assignment-operator-decrement-equal-javascript.md)   
 [Bitweiser Linksschiebeoperator (<\<)](../../javascript/reference/bitwise-left-shift-operator-decrement-javascript.md)   
 [Bitweiser Rechtsschiebeoperator (>>)](../../javascript/reference/bitwise-right-shift-operator-decrement-javascript.md)   
 [Operatorrangfolge](../../javascript/operator-subtractprecedence-javascript.md)   
 [Zusammenfassung der Operatoren (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)