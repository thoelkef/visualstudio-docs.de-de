---
title: "Additionsoperator (+) (JavaScript) | Microsoft Docs"
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
  - "+"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Arithmetische Operatoren, Addition"
  - "Zeichenfolgen [Visual Studio], Verketten"
  - "Verkettungsoperatoren, Vergleich zum Additionsoperator"
  - "Additionsoperator"
  - "+-Operator"
ms.assetid: ec1237d3-e78b-4e77-bd7d-c0204cf03acd
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# Additionsoperator (+) (JavaScript)
Addiert den Wert eines numerischen Ausdrucks zu einem anderen oder verkettet zwei Zeichenfolgen.  
  
## Syntax  
  
```  
  
result = expression1 + expression2  
```  
  
## Parameter  
 `result`  
 Beliebige Variable.  
  
 `expression1`  
 Ein beliebiger Ausdruck.  
  
 `expression2`  
 Ein beliebiger Ausdruck.  
  
## Hinweise  
 Die Typen der beiden Ausdrücke bestimmen das Verhalten des Operators **\+**.  
  
|Wenn|Dann|  
|----------|----------|  
|Beide Ausdrücke sind numerische oder boolesche Werte|Hinzufügen|  
|Beide Ausdrücke sind Zeichenfolgen|Verketten|  
|Ein Ausdruck ist numerisch, der andere eine Zeichenfolge|Verketten|  
  
## Anforderungen  
 [!INCLUDE[jsv1](../../includes/jsv1-md.md)]  
  
## Siehe auch  
 [Additionszuweisungsoperator \(\+\=\)](../../javascript/reference/addition-assignment-operator-decrement-equal-javascript.md)   
 [Operatorrangfolge](../../javascript/operator-subtractprecedence-javascript.md)   
 [Zusammenfassung der Operatoren \(JavaScript\)](../../javascript/misc/operator-subtractsummary-javascript.md)