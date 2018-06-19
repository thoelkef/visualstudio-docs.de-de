---
title: Bitweiser Operator OR (||) (JavaScript) | Microsoft Docs
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
- '|'
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- bitwise operators, OR operator
- OR operator
- '| operator'
ms.assetid: ffc8f758-3151-478e-bafb-fc78f1c469a0
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a91c616c84b9d38154bf936f61fb856a4ebad0f7
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
ms.locfileid: "24633750"
---
# <a name="bitwise-or-operator--javascript"></a>Bitweiser OR-Operator (|) (JavaScript)
Führt eine bitweise OR-Operation für zwei Ausdrücke durch.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
result = expression1 | expression2  
```  
  
## <a name="parameters"></a>Parameter  
 *Ergebnis*  
 Beliebige Variable.  
  
 *expression1*  
 Beliebiger Ausdruck.  
  
 *expression2*  
 Beliebiger Ausdruck.  
  
## <a name="remarks"></a>Hinweise  
 Die **&#124;** Operator die binäre Darstellung der Werte von zwei Ausdrücken und führt eine bitweise OR-Operation auf diese. Das Ergebnis dieses Vorgangs verhält sich wie folgt:  
  
```JavaScript  
0101   (expression1)  
1100   (expression2)  
----  
1101   (result)  
```  
  
 Jedes Mal, wenn entweder der Ausdrücke eine "1" wurde in eine Ziffer, das Ergebnis wird an dieser Stelle eine 1 aufweisen. Andernfalls wird das Ergebnis 0 an dieser Stelle müssen.  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Siehe auch  
 [Bitweiser OR -Zuweisungsoperator (&#124; =)](../../javascript/reference/bitwise-or-assignment-operator-decrement-equal-javascript.md)   
 [Operatorrangfolge](../../javascript/operator-subtractprecedence-javascript.md)   
 [Zusammenfassung der Operatoren (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)