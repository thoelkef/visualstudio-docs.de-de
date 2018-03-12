---
title: Rest-Operator (JavaScript) | Microsoft Docs
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
- '%'
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- remainder operator, JavaScript
- '% operator [JavaScript]'
- Remainder function [JavaScript]
ms.assetid: 087d654f-623b-498d-95ff-596d26bf674d
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ce74b8512b25cfe215d294873102b274623b42a2
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="remainder-operator-javascript"></a>Restoperator (JavaScript)
Dividiert den Wert eines Ausdrucks durch den Wert eines anderen und gibt den Restwert zurück.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
result = number1 % number2  
```  
  
## <a name="arguments"></a>Argumente  
 `result`  
 Beliebige Variable.  
  
 `number1`  
 Ein beliebiger numerischer Ausdruck.  
  
 `number2`  
 Ein beliebiger numerischer Ausdruck.  
  
## <a name="remarks"></a>Hinweise  
 Teilt dem Restoperator `number1` von `number2`und gibt nur den Rest als `result`. Das Vorzeichen des `result` entspricht dem Zeichen des `number1`. Der Wert der `result` liegt zwischen 0 und den absoluten Wert des `number2`.  
  
 Der folgende Code zeigt, wie den Restoperator verwendet wird.  
  
```  
var modResult = 19 % 6.7;  
document.write(modResult);  
  
// Output: 5.6  
  
```  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Siehe auch  
 [Operatorrangfolge](../../javascript/operator-subtractprecedence-javascript.md)   
 [Zusammenfassung der Operatoren (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)
