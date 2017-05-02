---
title: "Modulus-Operator (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "%"
dev_langs: 
  - "JavaScript"
  - "DHTML"
helpviewer_keywords: 
  - "Modulus-Operator, JavaScript"
  - "%-Operator [JavaScript]"
  - "Modulo-Funktion [JavaScript]"
ms.assetid: 087d654f-623b-498d-95ff-596d26bf674d
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Modulus-Operator (JavaScript)
Dividiert den Wert eines Ausdrucks durch den Wert eines anderen und gibt den Restwert zurück.  
  
## Syntax  
  
```  
  
result = number1 % number2  
```  
  
## Argumente  
 `result`  
 Beliebige Variable.  
  
 `number1`  
 Beliebiger numerischer Ausdruck.  
  
 `number2`  
 Beliebiger numerischer Ausdruck.  
  
## Hinweise  
 Der Modulo\- oder Restoperator dividiert `number1` durch `number2` und gibt nur den Rest als `result` zurück.  Das Vorzeichen des `result` ist mit dem Vorzeichen von `number1` identisch.  Der Wert von `result` liegt zwischen 0 und dem absoluten Wert von `number2`.  
  
 Im folgenden Code wird die Verwendung des Modulo\-Operators gezeigt:  
  
```  
var modResult = 19 % 6.7;  
document.write(modResult);  
  
// Output: 5.6  
  
```  
  
## Anforderungen  
 [!INCLUDE[jsv1](../../includes/jsv1-md.md)]  
  
## Siehe auch  
 [Operatorrangfolge](../../javascript/operator-subtractprecedence-javascript.md)   
 [Zusammenfassung der Operatoren \(JavaScript\)](../../javascript/misc/operator-subtractsummary-javascript.md)