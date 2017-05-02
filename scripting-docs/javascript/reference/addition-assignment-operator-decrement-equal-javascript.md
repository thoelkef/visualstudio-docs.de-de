---
title: "Additionszuweisungsoperator (+=) (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "+="
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Additionszuweisungsoperator (+=)"
  - "+=-Operator"
  - "Zuweisungsoperatoren, JavaScript"
ms.assetid: 8517d05c-38b0-4107-bea4-253eb420f438
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# Additionszuweisungsoperator (+=) (JavaScript)
Fügt dem Wert einer Variablen den Wert eines Ausdrucks hinzu und weist das Ergebnis der Variablen zu.  
  
## Syntax  
  
```  
  
result += expression   
```  
  
## Parameter  
 `result`  
 Beliebige Variable.  
  
 `expression`  
 Ein beliebiger Ausdruck.  
  
## Hinweise  
 Die Verwendung dieses Operators entspricht genau der folgenden Angabe: `result = result + expression`.  
  
 Die Typen der beiden Ausdrücke bestimmen das Verhalten des Operators `+=`.  
  
|Wenn|Dann|  
|----------|----------|  
|Beide Ausdrücke sind numerische oder boolesche Werte|Hinzufügen|  
|Beide Ausdrücke sind Zeichenfolgen|Verketten|  
|Ein Ausdruck ist numerisch, der andere eine Zeichenfolge|Verketten|  
  
## Anforderungen  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## Siehe auch  
 [Additionsoperator \(\+\)](../../javascript/reference/addition-operator-decrement-javascript.md)   
 [Operatorrangfolge](../../javascript/operator-subtractprecedence-javascript.md)   
 [Zusammenfassung der Operatoren \(JavaScript\)](../../javascript/misc/operator-subtractsummary-javascript.md)