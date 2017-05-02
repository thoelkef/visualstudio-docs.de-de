---
title: "Bitweiser AND-Operator (&amp;) (JavaScript) | Microsoft Docs"
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
  - "&"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Zuweisungsoperatoren, bitweise [JavaScript]"
  - "&-Operator, Informationen über den &-Operator"
  - "AND-Operator"
  - "& (Operator)"
  - "Bitweise Operatoren, AND-Operator"
  - "&-Operator, bitweise Operatoren"
ms.assetid: a8c17a55-2599-4518-98d7-671699f4d5f3
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# Bitweiser AND-Operator (&amp;) (JavaScript)
Führt eine bitweise AND\-Operation für zwei 32\-Bit\-Ausdrücke durch.  
  
## Syntax  
  
```  
  
result = expression1 & expression2  
```  
  
## Parameter  
 `result`  
 Das Ergebnis der Operation.  
  
 `expression1`  
 Ein beliebiger Ausdruck.  
  
 `expression2`  
 Ein beliebiger Ausdruck.  
  
## Hinweise  
 Der Operator `&` führt eine bitweise AND\-Operation mit jedem der Bits von zwei 32\-Bit\-Ausdrücken aus.  Wenn beide der Bits 1 sind, ist das Ergebnis 1.  Andernfalls ist das Ergebnis 0.  
  
|Bit1|Bit2|mit AND verknüpfter Wert|  
|----------|----------|------------------------------|  
|0|0|0|  
|1|1|1|  
|1|0|0|  
|0|1|0|  
  
 Im den folgenden Beispielen wird die Verwendung des `&`\-Operators gezeigt.  
  
```javascript  
// 9 is 00000000000000000000000000001001  
var expr1 = 9;  
  
// 5 is 00000000000000000000000000000101  
var expr2 = 5;  
  
// 1 is 00000000000000000000000000000001  
var result = expr1 & expr2;  
  
document.write(result);  
// Output: 1  
```  
  
## Anforderungen  
 [!INCLUDE[jsv1](../../includes/jsv1-md.md)]  
  
## Siehe auch  
 [Bitweiser AND\-Zuweisungsoperator \(&\=\)](../../javascript/reference/bitwise-and-assignment-operator-decrement-equal-javascript.md)   
 [Operatorrangfolge](../../javascript/operator-subtractprecedence-javascript.md)   
 [Zusammenfassung der Operatoren \(JavaScript\)](../../javascript/misc/operator-subtractsummary-javascript.md)