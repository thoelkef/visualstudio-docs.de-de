---
title: "Bitweiser XOR-Operator (^) (JavaScript) | Microsoft Docs"
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
  - "^"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Bitweise Operatoren, XOR-Operator"
  - "XOR-Operator"
ms.assetid: 44ef0d18-abb5-4d83-9e77-6394635b3f48
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# Bitweiser XOR-Operator (^) (JavaScript)
Führt eine bitweise XOR\-Operation für zwei Ausdrücke durch.  
  
## Syntax  
  
```  
  
result = expression1 ^ expression2  
```  
  
## Parameter  
 *Ergebnis*  
 Beliebige Variable.  
  
 *expression1*  
 Ein beliebiger Ausdruck.  
  
 *expression2*  
 Ein beliebiger Ausdruck.  
  
## Hinweise  
 Der **^**‑Operator liest die Binärdaten der Werte zweier Ausdrücke und führt eine bitweise XOR‑Operation mit diesen durch.  Diese Operation zeigt folgendes Verhalten:  
  
```javascript  
0101   (expression1)  
1100   (expression2)  
----  
1001   (result)  
```  
  
 Wenn einer \(nicht beide\) der Ausdrücke eine 1 an einer Stelle aufweist, hat auch das Ergebnis an dieser Stelle eine 1.  Andernfalls enthält das Ergebnis eine 0 an dieser Stelle.  
  
## Anforderungen  
 [!INCLUDE[jsv1](../../includes/jsv1-md.md)]  
  
## Siehe auch  
 [Bitweiser XOR\-Zuweisungsoperator \(^\=\)](../../javascript/reference/bitwise-xor-assignment-operator-decrement-hat-equal-javascript.md)   
 [Operatorrangfolge](../../javascript/operator-subtractprecedence-javascript.md)   
 [Zusammenfassung der Operatoren \(JavaScript\)](../../javascript/misc/operator-subtractsummary-javascript.md)