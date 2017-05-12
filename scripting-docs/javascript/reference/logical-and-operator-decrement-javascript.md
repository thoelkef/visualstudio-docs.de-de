---
title: "Logischer AND-Operator (&amp;&amp;) (JavaScript) | Microsoft Docs"
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
  - "&&"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "&&-Operator"
  - "Logischer AND-Operator"
ms.assetid: 4714dea9-1999-444a-8acd-72f0851e4f65
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# Logischer AND-Operator (&amp;&amp;) (JavaScript)
Erzeugt eine logische Verbindung zwischen zwei Ausdrücken.  
  
## Syntax  
  
```  
  
result = expression1 && expression2   
```  
  
## Parameter  
 `result`  
 Beliebige Variable.  
  
 `expression1`  
 Beliebiger Ausdruck.  
  
 `expression2`  
 Beliebiger Ausdruck.  
  
## Hinweise  
 Wenn `expression1` `false` ergibt, lautet `result` `expression1`.  Andernfalls lautet `result` `expression2`.  Der Vorgang gibt daher `true` zurück, wenn beide true sind; andernfalls wird `false` zurückgegeben.  
  
 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] verwendet die folgenden Regeln für die Konvertierung nicht boolescher Werte in boolesche Werte:  
  
-   Alle Objekte gelten als `true`.  
  
-   Zeichenfolgen gelten als `false`, wenn sie leer sind.  
  
-   `null` und `undefined` gelten als `false`.  
  
-   Eine Zahl `false`, wenn Sie Null lautet.  
  
## Anforderungen  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## Siehe auch  
 [Operatorrangfolge](../../javascript/operator-subtractprecedence-javascript.md)   
 [Zusammenfassung der Operatoren \(JavaScript\)](../../javascript/misc/operator-subtractsummary-javascript.md)