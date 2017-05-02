---
title: "Logischer NOT-Operator (!) (JavaScript) | Microsoft Docs"
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
  - "!"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "! Operator"
  - "! Operator, Informationen über den !-Operator"
  - "Logischer NOT-Operator"
ms.assetid: 68c3dc71-ae95-4293-9155-67405846d71d
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# Logischer NOT-Operator (!) (JavaScript)
Führt eine logische Negation für einen Ausdruck durch.  
  
## Syntax  
  
```  
  
result = !expression  
```  
  
## Parameter  
 *Ergebnis*  
 Beliebige Variable.  
  
 *expression*  
 Ein beliebiger Ausdruck.  
  
## Hinweise  
 Die folgende Tabelle veranschaulicht, wie *result* berechnet wird:  
  
|Wenn `expression` folgenden Wert hat|dann hat `result` den Wert|  
|------------------------------------------|--------------------------------|  
|True|False|  
|False|True|  
  
 Alle unären Operatoren, wie der **\!**\-Operator, werten Ausdrücke wie folgt aus:  
  
-   Wenn der Operator auf die Ausdrücke "undefined" oder `null` angewendet wird, entsteht ein Laufzeitfehler.  
  
-   Objekte werden in Zeichenfolgen konvertiert.  
  
-   Zeichenfolgen werden, sofern möglich, in Zahlen konvertiert.  Andernfalls wird ein Laufzeitfehler generiert.  
  
-   Boolesche Werte werden wie Zahlen behandelt \(0 \= false, 1 \= true\).  
  
 Der Operator wird auf die resultierende Zahl angewendet.  
  
 Für den logischen Operator **\!** gilt: Ist *expression* ungleich Null, so ist *result* gleich Null.  Ist *expression* gleich Null, so ist *result* gleich 1.  
  
## Anforderungen  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## Siehe auch  
 [Bitweiser NOT\-Operator \(~\)](../../javascript/reference/bitwise-not-operator-decrement-tilde-javascript.md)   
 [Operatorrangfolge](../../javascript/operator-subtractprecedence-javascript.md)   
 [Zusammenfassung der Operatoren \(JavaScript\)](../../javascript/misc/operator-subtractsummary-javascript.md)