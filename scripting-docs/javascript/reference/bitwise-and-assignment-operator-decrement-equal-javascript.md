---
title: "Bitweiser AND-Zuweisungsoperator&#160;(&amp;=) (JavaScript) | Microsoft Docs"
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
  - "&="
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "&= (Operator)"
  - "Zuweisungsoperatoren, Bitweise [JavaScript]"
  - "AND-Operator"
  - "Bitweise Operatoren, AND-Operator"
ms.assetid: e7e2eabb-4fc1-4fdc-9dd8-1e6d715371fa
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# Bitweiser AND-Zuweisungsoperator&#160;(&amp;=) (JavaScript)
Legt das Ergebnis einer bitweisen AND\-Operation auf den Wert einer Variablen und den Wert eines Ausdrucks fest.  Die Variable und der Ausdruck werden als 32\-Bit\-Ganzzahlen behandelt.  
  
## Syntax  
  
```  
  
result &= expression  
```  
  
## Parameter  
 `result`  
 Beliebige Variable.  
  
 `expression`  
 Ein beliebiger Ausdruck.  
  
## Hinweise  
 Die Verwendung dieses Operators entspricht genau der folgenden Angabe:  
  
```javascript  
result = result & expression  
```  
  
 Der [Bitweiser AND\-Operator \(&\)](../../javascript/reference/bitwise-and-operator-decrement-javascript.md) liest die binäre Darstellung der Werte von `result` und `expression` und führt mit ihnen eine bitweise AND‑Operation durch.  Diese Operation zeigt folgendes Verhalten:  
  
```javascript  
// 9 is 00000000000000000000000000001001  
var expr1 = 9;  
  
// 5 is 00000000000000000000000000000101  
var expr2 = 5;  
  
// 1 is 00000000000000000000000000000001  
expr1 &= expr2;  
  
document.write(expr1);  
  
```  
  
 Jedes Mal, wenn beide Ausdrücke eine 1 an einer Stelle aufweisen, hat auch das Ergebnis an dieser Stelle eine 1.  Andernfalls enthält das Ergebnis eine 0 an dieser Stelle.  
  
## Anforderungen  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## Siehe auch  
 [Bitweiser AND\-Operator \(&\)](../../javascript/reference/bitwise-and-operator-decrement-javascript.md)   
 [Operatorrangfolge](../../javascript/operator-subtractprecedence-javascript.md)   
 [Zusammenfassung der Operatoren \(JavaScript\)](../../javascript/misc/operator-subtractsummary-javascript.md)