---
title: Bitweiser Rechtsschiebeoperator (&gt;&gt;) (JavaScript) | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: '>>'
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- '>> operator'
- '>> operator, about >> operator'
- '>> operator, bitsets'
- bitwise operators, right shift operator
ms.assetid: 89dc57e0-0b0d-49a4-a8ed-56d8bb20f3e3
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 70db0c176b475886a26cfe4c06f7f2f0c9d4fc2a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="bitwise-right-shift-operator-gtgt-javascript"></a>Bitweiser Rechtsschiebeoperator (&gt;&gt;) (JavaScript)
Rechts verschiebt die Bits eines Ausdrucks Vorzeichen beizubehalten.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
result = expression1 >> expression2  
```  
  
## <a name="parameters"></a>Parameter  
 *Ergebnis*  
 Beliebige Variable.  
  
 *expression1*  
 Beliebiger Ausdruck.  
  
 *expression2*  
 Beliebiger Ausdruck.  
  
## <a name="remarks"></a>Hinweise  
 Die >> Operator verschiebt die Bits eines *expression1* nach rechts um die Anzahl der Bits, die im angegebenen *expression2*. Das Vorzeichenbit von *expression1* wird verwendet, um die Ziffern von Links zu füllen. Ziffern rechts verschobene werden verworfen. Beispiel: Nachdem der Auswertung des folgenden Codes *Temp* hat den Wert in-4:-14 (11110010 in binären Komplement) verschoben, zwei Bits entspricht-4 (11111100 in binären Komplement).  
  
```JavaScript  
var temp  
temp = -14 >> 2  
```  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Siehe auch  
 [Bitweiser Linksschiebeoperator (<\<)](../../javascript/reference/bitwise-left-shift-operator-decrement-javascript.md)   
 [Rightshiftzuweisungsoperator (>> =)](../../javascript/reference/right-shift-assignment-operator-decrement-equal-javascript.md)   
 [Vorzeichenloser Rechtsschiebeoperator (>>>)](../../javascript/reference/unsigned-right-shift-operator-decrement-javascript.md)   
 [Operatorrangfolge](../../javascript/operator-subtractprecedence-javascript.md)   
 [Zusammenfassung der Operatoren (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)