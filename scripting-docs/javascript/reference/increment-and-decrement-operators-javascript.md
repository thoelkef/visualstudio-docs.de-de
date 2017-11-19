---
title: Inkrementoperator (++) und Dekrementoperator (--) (JavaScript) | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- --
- ++
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- increment operators, syntax
- ++ operator
- ++ operator, about ++ operator
- decrement operators, syntax
- -- operator
ms.assetid: 49eaf4cf-8818-478d-a429-cdd2ece20811
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 806bd321bb1f81d585a6595b8cf2842571164921
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="increment--and-decrement----operators-javascript"></a>Inkrementoperator (++) und Dekrementoperator (--) (JavaScript)
Die Schrittweite Operator Inkremente und Dekrement-Operator-dekrementiert den Wert einer Variablen um eins.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
      result = ++variable  
result = --variable  
result = variable++  
result = variable--  
```  
  
## <a name="parameters"></a>Parameter  
 `result`  
 Beliebige Variable.  
  
 `variable`  
 Beliebige Variable.  
  
## <a name="remarks"></a>Hinweise  
 Wenn der Operator vor dem die Variable angegeben wird, wird der Wert geändert, damit der Ausdruck ausgewertet wird. Wenn der Operator nach der Variable angezeigt wird, ist der Wert geändert, nachdem der Ausdruck ausgewertet wird.  Also erhält `j = ++k;`, den Wert der `j` ist der ursprüngliche Wert der `k` plus eins; angegebenen `j = k++;`, den Wert des `j` ist der ursprüngliche Wert der `k`, dem wird erhöht, nachdem der Wert zugewiesen wird `j`.  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Siehe auch  
 [Operatorrangfolge](../../javascript/operator-subtractprecedence-javascript.md)   
 [Zusammenfassung der Operatoren (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)