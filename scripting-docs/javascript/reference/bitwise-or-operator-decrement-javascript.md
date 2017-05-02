---
title: "Bitweiser OR-Operator (|) (JavaScript) | Microsoft Docs"
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
  - "|"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "| (Operator)"
  - "Bitweise Operatoren, OR-Operator"
  - "OR-Operator"
ms.assetid: ffc8f758-3151-478e-bafb-fc78f1c469a0
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# Bitweiser OR-Operator (|) (JavaScript)
Führt eine bitweise OR\-Operation für zwei Ausdrücke durch.  
  
## Syntax  
  
```  
  
result = expression1 | expression2  
```  
  
## Parameter  
 *Ergebnis*  
 Beliebige Variable.  
  
 *expression1*  
 Ein beliebiger Ausdruck.  
  
 *expression2*  
 Ein beliebiger Ausdruck.  
  
## Hinweise  
 Anschließend liest der          **&#124;** ‑Operator die Binärdaten der Werte zweier Ausdrücke und führt eine bitweise XOR‑Operation mit diesen durch.  Diese Operation zeigt folgendes Verhalten:  
  
```javascript  
0101   (expression1)  
1100   (expression2)  
----  
1101   (result)  
```  
  
 Jedes Mal, wenn einer der Ausdrücke eine 1 an einer Stelle aufweist, hat auch das Ergebnis an dieser Stelle eine 1.  Andernfalls enthält das Ergebnis eine 0 an dieser Stelle.  
  
## Anforderungen  
 [!INCLUDE[jsv1](../../includes/jsv1-md.md)]  
  
## Siehe auch  
 [Bitweiser OR\-Zuweisungsoperator \(&#124;\=\)](../../javascript/reference/bitwise-or-assignment-operator-decrement-equal-javascript.md)   
 [Operatorrangfolge](../../javascript/operator-subtractprecedence-javascript.md)   
 [Zusammenfassung der Operatoren \(JavaScript\)](../../javascript/misc/operator-subtractsummary-javascript.md)