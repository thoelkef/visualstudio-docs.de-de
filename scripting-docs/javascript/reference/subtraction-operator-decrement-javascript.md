---
title: "Subtraktionsoperator (-) (JavaScript) | Microsoft Docs"
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
  - "-"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "--Operator"
  - "--Operator, Informationen über den --Operator"
  - "Arithmetische Operatoren, Subtraktion"
  - "Negationsoperator"
  - "Operatoren, Subtraktion"
  - "Subtraktionsoperator, Syntax"
ms.assetid: cd0681d3-15cd-49fe-b4dd-e087de55d778
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# Subtraktionsoperator (-) (JavaScript)
Subtrahiert den Wert eines Ausdrucks von einem anderen oder bewirkt die unäre Negation eines einzelnen Ausdrucks.  
  
## Syntax  
  
```  
  
result = number1 - number2;  
  
```  
  
## Parameter  
 *Ergebnis*  
 Beliebige numerische Variable.  
  
 `number`  
 Beliebiger numerischer Ausdruck.  
  
 `number1`  
 Beliebiger numerischer Ausdruck.  
  
 `number2`  
 Beliebiger numerischer Ausdruck.  
  
## Hinweise  
 In Syntax 1 wird der Subtraktionsoperator \(**\-**\) verwendet, um die Differenz zweier Zahlen durch arithmetische Subtraktion zu bestimmen.  In Syntax 2 wird der Subtraktionsoperator \(**\-**\) als unärer Negationsoperator verwendet, um den negativen Wert eines Ausdrucks anzugeben.  
  
 In Syntax 2 werden Ausdrücke wie bei allen anderen unären Operatoren wie folgt ausgewertet:  
  
-   Wenn der Operator auf die Ausdrücke "undefined" oder `null` angewendet wird, entsteht ein Laufzeitfehler.  
  
-   Objekte werden in Zeichenfolgen konvertiert.  
  
-   Zeichenfolgen werden, sofern möglich, in Zahlen konvertiert.  Andernfalls wird ein Laufzeitfehler generiert.  
  
-   Boolesche Werte werden wie Zahlen behandelt \(0 \= false, 1 \= true\).  
  
 Der Operator wird auf die resultierende Zahl angewendet.  Wenn das Ergebnis in Syntax 2 ungleich Null ist, entspricht *result* der resultierenden Zahl mit umgekehrtem Vorzeichen.  Wenn die resultierende Zahl Null ist, ist *result* gleich Null.  
  
## Anforderungen  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## Siehe auch  
 [Subtraktionszuweisungsoperator \(\-\=\)](../../javascript/reference/subtraction-assignment-operator-decrement-equal-javascript.md)   
 [Operatorrangfolge](../../javascript/operator-subtractprecedence-javascript.md)   
 [Zusammenfassung der Operatoren \(JavaScript\)](../../javascript/misc/operator-subtractsummary-javascript.md)