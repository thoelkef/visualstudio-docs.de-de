---
title: "Bitweiser OR-Zuweisungsoperator&#160;(|=) (JavaScript) | Microsoft Docs"
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
  - "|="
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "|= (Operator)"
  - "Zuweisungsoperatoren, bitweise [JavaScript]"
  - "Bitweise Operatoren, OR-Operator"
  - "OR-Operator"
ms.assetid: 9b424ff6-4442-4621-b3b6-83e7fd1e5cd5
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# Bitweiser OR-Zuweisungsoperator&#160;(|=) (JavaScript)
Führt eine bitweise OR\-Operation für den Wert einer Variablen und den Wert eines Ausdrucks durch und weist das Ergebnis der Variablen zu.  
  
## Syntax  
  
```  
  
result |= expression  
```  
  
## Parameter  
 *Ergebnis*  
 Beliebige Variable.  
  
 *expression*  
 Ein beliebiger Ausdruck.  
  
## Hinweise  
 Die Verwendung dieses Operators entspricht genau der folgenden Angabe:  
  
```javascript  
result = result | expression  
```  
  
 Der **&#124;\=**\-Operator liest die binäre Darstellung der Werte von *result* und *expression* und führt eine bitweise OR\-Operation an diesen Werten durch.  Dieser Vorgang zeigt folgendes Verhalten:  
  
```javascript  
0101    (result)  
1100    (expression)  
----  
1101    (output)  
```  
  
 Jedes Mal, wenn einer der Ausdrücke eine 1 an einer Stelle aufweist, hat auch das Ergebnis an dieser Stelle eine 1.  Andernfalls enthält das Ergebnis eine 0 an dieser Stelle.  
  
## Anforderungen  
 [!INCLUDE[jsv1](../../includes/jsv1-md.md)]  
  
## Siehe auch  
 [Bitweiser OR\-Operator \(&#124;\)](../../javascript/reference/bitwise-or-operator-decrement-javascript.md)   
 [Operatorrangfolge](../../javascript/operator-subtractprecedence-javascript.md)   
 [Zusammenfassung der Operatoren \(JavaScript\)](../../javascript/misc/operator-subtractsummary-javascript.md)