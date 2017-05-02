---
title: "Kommaoperator (,) (JavaScript) | Microsoft Docs"
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
  - "%2C"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Kommaoperator"
ms.assetid: 699fa0bf-cd0a-45ee-a291-2fbed4ecd470
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# Kommaoperator (,) (JavaScript)
Bewirkt die sequenzielle Ausführung von zwei Ausdrücken.  
  
## Syntax  
  
```  
  
expression1, expression2  
```  
  
## Parameter  
 `expression1`  
 Ein beliebiger Ausdruck.  
  
 `expression2`  
 Ein beliebiger Ausdruck.  
  
## Hinweise  
 Der `,`\-Operator bewirkt, dass die Ausdrücke von links nach rechts ausgeführt werden.  Der `,`\-Operator wird häufig im Inkrementausdruck einer `for`\-Schleife verwendet.  Beispiel:  
  
```javascript  
j=25;  
for (i = 0; i < 10; i++, j++)  
{  
   k = i + j;  
}  
```  
  
 Die `for`\-Anweisung lässt nur die Ausführung eines einzigen Ausdrucks am Ende jedes Schleifendurchlaufs zu.  Der `,`\-Operator kann mehrere Ausdrücke zu einem Ausdruck zusammenfassen, sodass beide Variablen inkrementiert werden können.  
  
## Anforderungen  
 [!INCLUDE[jsv1](../../includes/jsv1-md.md)]  
  
## Siehe auch  
 [for\-Anweisung](../../javascript/reference/for-statement-javascript.md)   
 [Operatorrangfolge](../../javascript/operator-subtractprecedence-javascript.md)   
 [Zusammenfassung der Operatoren \(JavaScript\)](../../javascript/misc/operator-subtractsummary-javascript.md)