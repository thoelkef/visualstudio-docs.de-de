---
title: "Bitweiser XOR-Zuweisungsoperator&#160;(^=) (JavaScript) | Microsoft Docs"
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
  - "^="
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "^= (Operator)"
  - "^= (Operator), Informationen über den ^=-Operator"
  - "Zuweisungsoperatoren, bitweise [JavaScript]"
  - "Bitweise Operatoren, XOR-Operator"
  - "XOR-Operator"
ms.assetid: a6ded216-27b6-4fc4-a51b-7d10cc6f820c
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# Bitweiser XOR-Zuweisungsoperator&#160;(^=) (JavaScript)
Führt eine bitweise XOR\-Operation für eine Variable und einen Ausdruck durch und weist das Ergebnis der Variablen zu.  
  
## Syntax  
  
```  
  
result ^= expression  
```  
  
## Parameter  
 *Ergebnis*  
 Beliebige Variable.  
  
 *expression*  
 Ein beliebiger Ausdruck.  
  
## Hinweise  
 Die Verwendung des **^\=**\-Operators entspricht genau der folgenden Angabe:  
  
```javascript  
result = result ^ expression  
```  
  
 Der **^\=**‑Operator liest die Binärdaten der Werte zweier Ausdrücke und führt eine bitweise XOR‑Operation mit diesen durch.  Diese Operation zeigt folgendes Verhalten:  
  
```javascript  
0101    (result)  
1100    (expression)  
----  
1001    (result)  
```  
  
 Wenn einer \(nicht beide\) der Ausdrücke eine 1 an einer Stelle aufweist, hat auch das Ergebnis an dieser Stelle eine 1.  Andernfalls enthält das Ergebnis eine 0 an dieser Stelle.  
  
## Anforderungen  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## Siehe auch  
 [Bitweiser XOR\-Operator \(^\)](../../javascript/reference/bitwise-xor-operator-decrement-hat-javascript.md)   
 [Operatorrangfolge](../../javascript/operator-subtractprecedence-javascript.md)   
 [Zusammenfassung der Operatoren \(JavaScript\)](../../javascript/misc/operator-subtractsummary-javascript.md)