---
title: "Bitweiser NOT-Operator (~) (JavaScript) | Microsoft Docs"
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
  - "~"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Bitweise Operatoren, NOT-Operator"
  - "NOT-Operator"
ms.assetid: 39f92474-fe05-4a8b-9ad8-caca93f82bca
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# Bitweiser NOT-Operator (~) (JavaScript)
Führt eine bitweise NOT\-Operation \(Negation\) für einen Ausdruck durch.  
  
## Syntax  
  
```  
  
result = ~ expression  
```  
  
## Parameter  
 *Ergebnis*  
 Beliebige Variable.  
  
 *expression*  
 Ein beliebiger Ausdruck.  
  
## Hinweise  
 Alle unären Operatoren, wie z. B. der `~`\-Operator, werten Ausdrücke wie folgt aus:  
  
-   Wenn der Operator auf die Ausdrücke "undefined" oder `null` angewendet wird, entsteht ein Laufzeitfehler.  
  
-   Objekte werden in Zeichenfolgen konvertiert.  
  
-   Zeichenfolgen werden, sofern möglich, in Zahlen konvertiert.  Andernfalls wird ein Laufzeitfehler generiert.  
  
-   Boolesche Werte werden wie Zahlen behandelt \(0 \= false, 1 \= true\).  
  
 Der Operator wird auf die resultierende Zahl angewendet.  
  
 Der bitweise `~`\-Operator liest die Binärdaten der Ausdruckswerte und führt eine bitweise Negationsoperation durch.  
  
 Jede Stelle, für die im Ausdruck eine 1 steht, wird im Ergebnis zu einer 0.  Jede Stelle, für die im Ausdruck eine 0 steht, wird im Ergebnis zu einer 1.  
  
 Das folgende Beispiel veranschaulicht die Verwendung des bitweisen NOT \(~\)\-Operators.  
  
```  
var temp = ~5;  
```  
  
 Der resultierende Wert beträgt \-6 \(siehe folgende Tabelle\).  
  
|Ausdruck|Binärwert \(Zweierkomplement\)|Dezimalwert|  
|--------------|------------------------------------|-----------------|  
|5|00000000 00000000 00000000 00000101|5|  
|~5|11111111 11111111 11111111 11111010|\-6|  
  
## Anforderungen  
 [!INCLUDE[jsv1](../../includes/jsv1-md.md)]  
  
## Siehe auch  
 [Logischer NOT\-Operator \(\!\)](../../javascript/reference/logical-not-operator-decrement-exclpt-javascript.md)   
 [Operatorrangfolge](../../javascript/operator-subtractprecedence-javascript.md)   
 [Zusammenfassung der Operatoren \(JavaScript\)](../../javascript/misc/operator-subtractsummary-javascript.md)