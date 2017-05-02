---
title: "Math.max-Funktion (JavaScript) | Microsoft Docs"
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
  - "max"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "max-Methode"
ms.assetid: f3ea1b8a-5fd0-482a-971b-b7f8e2b9b7eb
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# Math.max-Funktion (JavaScript)
Gibt das größeren Ausdruck einer Reihe angegebener numerischer Ausdrücke zurück.  
  
## Syntax  
  
```  
Math.max([number1[, number2[... [, numberN]]]])   
```  
  
## Hinweise  
 Die optionalen `number1, number2, ..., numberN`\-Argumente sind die numerischen Ausdrücke, die ausgewertet werden sollen.  
  
 Wenn keine Argumente bereitgestellt werden, ist der Rückgabewert gleich [Number.NEGATIVE\_INFINITY](../../javascript/reference/number-constants-javascript.md).  Wenn ein Argument den Wert `NaN` hat, ist auch der Rückgabewert `NaN`.  
  
## Beispiel  
 Der folgende Code zeigt, wie der größere von zwei Ausdrücken abgerufen wird.  
  
```javascript  
var x = Math.max(107 - 3,  48 * 90);  
document.write(x);  
  
// Output:  
// 4320  
  
```  
  
## Anforderungen  
 [!INCLUDE[jsv1](../../includes/jsv1-md.md)]  
  
## Siehe auch  
 [Math.min\-Funktion](../../javascript/reference/math-min-function-javascript.md)