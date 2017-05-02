---
title: "Inkrementoperator&#160;(++) und Dekrementoperator&#160;(--) (JavaScript) | Microsoft Docs"
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
  - "--"
  - "++"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Inkrementoperatoren, Syntax"
  - "++-Operator"
  - "++-Operator, Informationen über den ++-Operator"
  - "Dekrementoperatoren, Syntax"
  - "-- (Operator)"
ms.assetid: 49eaf4cf-8818-478d-a429-cdd2ece20811
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# Inkrementoperator&#160;(++) und Dekrementoperator&#160;(--) (JavaScript)
Der Inkrementoperator \(\+\+\) erhöht den Wert einer Variablen in Einerschritten, der Dekrementoperator \(\-\-\) verringert den Wert einer Variablen in Einerschritten.  
  
## Syntax  
  
```  
  
      result = ++variable  
result = --variable  
result = variable++  
result = variable--  
```  
  
## Parameter  
 `result`  
 Beliebige Variable.  
  
 `variable`  
 Beliebige Variable.  
  
## Hinweise  
 Wenn der Operator vor der Variablen steht, wird der Wert geändert, bevor der Ausdruck ausgewertet wird.  Wenn der Operator hinter der Variablen steht, wird der Wert geändert, nachdem der Ausdruck ausgewertet wurde.  Das heißt, bei `j = ++k;` wäre der Wert von `j` der ursprüngliche Wert von `k` plus eins; bei `j = k++;` wäre der Wert von `j` der ursprüngliche Wert von `k`, der erst erhöht wird, nachdem er `j` zugewiesen wurde.  
  
## Anforderungen  
 [!INCLUDE[jsv1](../../includes/jsv1-md.md)]  
  
## Siehe auch  
 [Operatorrangfolge](../../javascript/operator-subtractprecedence-javascript.md)   
 [Zusammenfassung der Operatoren \(JavaScript\)](../../javascript/misc/operator-subtractsummary-javascript.md)