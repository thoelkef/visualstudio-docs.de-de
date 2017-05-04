---
title: "unshift-Methode (Array) (JavaScript) | Microsoft Docs"
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
  - "unshift"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "unshift-Methode"
ms.assetid: 8c6a39ed-bab3-4ca4-9350-571a9427ec94
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# unshift-Methode (Array) (JavaScript)
Fügt am Anfang eines Arrays neue Elemente ein.  
  
## Syntax  
  
```  
  
arrayObj.unshift([item1[, item2 [, . . . [, itemN]]]])  
```  
  
## Parameter  
 `arrayObj`  
 Erforderlich.  Ein `Array`\-Objekt.  
  
 `item1, item2,. . ., itemN`  
 Optional.  Elemente, die am Anfang des `Array`\-Objekts eingefügt werden sollen.  
  
## Hinweise  
 Die `unshift`\-Methode fügt Elemente am Anfang eines Arrays ein, sodass sie in der gleichen Reihenfolge wie in der Argumentliste erscheinen.  
  
## Beispiel  
 Im folgenden Beispiel wird die Verwendung der `unshift`\-Methode veranschaulicht.  
  
```javascript  
var ar = new Array();  
ar.unshift(10, 11);  
ar.unshift(12, 13, 14);  
document.write(ar.toString());  
  
// Output: 12,13,14,10,11  
```  
  
## Anforderungen  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## Siehe auch  
 [shift\-Methode \(Array\)](../../javascript/reference/shift-method-array-javascript.md)