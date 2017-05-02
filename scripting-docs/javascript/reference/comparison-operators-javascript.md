---
title: "Vergleichsoperatoren (JavaScript) | Microsoft Docs"
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
  - "Comparison"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Vergleichsoperatoren, Skript"
  - "Greater Than-Operator"
  - "Vergleichsoperatoren"
  - "Greater Than- oder Equals-Operator"
  - "Ungleichheitsoperator"
  - "Identitätsoperator"
ms.assetid: 084f90f0-d010-47cf-96dd-13d637fc9b68
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# Vergleichsoperatoren (JavaScript)
Geben einen booleschen Wert zurück, der das Ergebnis des Vergleichs angibt.  
  
## Syntax  
  
```  
  
expression1 comparisonoperator expression2  
```  
  
## Parameter  
 `expression1`  
 Ein beliebiger Ausdruck.  
  
 `comparisonoperator`  
 Beliebiger Vergleichsoperator.  
  
 `expression2`  
 Ein beliebiger Ausdruck.  
  
## Hinweise  
 Beim Vergleich von Zeichenfolgen verwendet [!INCLUDE[javascript](../../includes/javascript-md.md)] den Unicodezeichenwert des Zeichenfolgenausdrucks.  
  
 Im Folgenden wird beschrieben, wie sich die verschiedenen Operatorgruppen abhängig von Typ und Wert der beiden Ausdrücke `expression1` und `expression2` verhalten:  
  
 Relationale Operatoren: `<`, `>`, `<=`, `>=`  
  
-   Es wird versucht, sowohl `expression1` als auch `expression2` in Zahlen zu konvertieren.  
  
-   Wenn beide Ausdrücke Zeichenfolgen sind, wird ein Zeichenfolgenvergleich durchgeführt.  
  
-   Wenn einer der Ausdrücke den Wert `NaN` hat, wird `false` zurückgegeben.  
  
-   Die negative Null entspricht der positiven Null.  
  
-   Die negative Unendlichkeit ist kleiner als jede Zahl, einschließlich ihrer selbst.  
  
-   Die positive Unendlichkeit ist größer als jede Zahl, einschließlich ihrer selbst.  
  
 equality\-Operatoren: `==`, `!=`  
  
-   Wenn die beiden Ausdrücke unterschiedlichen Typs sind, wird versucht, diese in Zeichenfolgen, Zahlen oder boolesche Werte zu konvertieren.  
  
-   `NaN` entspricht keiner Zahl, einschließlich ihrer selbst.  
  
-   Die negative Null entspricht der positiven Null.  
  
-   `null` ist sowohl gleich `null` als auch gleich `undefined`.  
  
-   Werte werden als gleich betrachtet, wenn es sich dabei um identische Zeichenfolgen, numerisch äquivalente Zahlen, das gleiche Objekt oder identische boolesche Werte handelt. Bei unterschiedlichen Datentypen kann die Konvertierung in eines dieser Elemente erzwungen werden.  
  
-   Bei jedem anderen Vergleich werden die Werte als ungleich angesehen.  
  
 Identity\-Operatoren: `===`, `!==`  
  
 Diese Operatoren verhalten sich genauso wie die equality\-Operatoren, außer dass keine Typkonvertierung ausgeführt wird.  Wenn die Typen beider Ausdrücke nicht identisch sind, geben diese Ausdrücke immer `false` zurück.  
  
## Anforderungen  
 [!INCLUDE[jsv1](../../includes/jsv1-md.md)]  
  
## Siehe auch  
 [Operatorrangfolge](../../javascript/operator-subtractprecedence-javascript.md)   
 [Zusammenfassung der Operatoren \(JavaScript\)](../../javascript/misc/operator-subtractsummary-javascript.md)