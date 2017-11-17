---
title: Logischer AND-Operator (&amp;&amp;) (JavaScript) | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: '&&'
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- logical AND operator
- '&& operator'
ms.assetid: 4714dea9-1999-444a-8acd-72f0851e4f65
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2107eb89c5ca964cf08172050b49307cb150590f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="logical-and-operator-ampamp-javascript"></a>Logischer AND-Operator (&amp;&amp;) (JavaScript)
Erzeugt eine logische Verbindung zwischen zwei Ausdrücken.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
result = expression1 && expression2   
```  
  
## <a name="parameters"></a>Parameter  
 `result`  
 Beliebige Variable.  
  
 `expression1`  
 Beliebiger Ausdruck.  
  
 `expression2`  
 Beliebiger Ausdruck.  
  
## <a name="remarks"></a>Hinweise  
 Wenn `expression1` `false` ergibt, lautet `result` `expression1`. Andernfalls lautet `result` `expression2`. Der Vorgang gibt daher `true` zurück, wenn beide true sind; andernfalls wird `false` zurückgegeben.  
  
 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] verwendet die folgenden Regeln für die Konvertierung nicht boolescher Werte in boolesche Werte:  
  
-   Alle Objekte gelten als `true`.  
  
-   Zeichenfolgen gelten als `false`, wenn sie leer sind.  
  
-   `null` und `undefined` gelten als `false`.  
  
-   Eine Zahl `false`, wenn Sie Null lautet.  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Siehe auch  
 [Operatorrangfolge](../../javascript/operator-subtractprecedence-javascript.md)   
 [Zusammenfassung der Operatoren (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)