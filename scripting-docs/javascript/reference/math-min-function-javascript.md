---
title: "Math.min-Funktion (JavaScript) | Microsoft Docs"
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
  - "min"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "min-Methode"
ms.assetid: a1d7dd85-27ef-45cd-aa2a-f8e80f0b2898
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# Math.min-Funktion (JavaScript)
Gibt den kleineren einer Gruppe von numerischen Ausdrücken zurück.  
  
## Syntax  
  
```  
Math.min([number1[, number2[... [,numberN]]]])  
```  
  
## Hinweise  
 Die optionalen `number1, number2, ..., numberN`\-Argumente sind die numerischen Ausdrücke, die ausgewertet werden sollen.  
  
 Wenn keine Argumente bereitgestellt werden, ist der Rückgabewert gleich [Number.POSITIVE\_INFINITY](../../javascript/reference/number-constants-javascript.md).  Wenn ein Argument den Wert `NaN` hat, ist auch der Rückgabewert `NaN`.  
  
## Beispiel  
 Der folgende Code zeigt, wie der kleinere von zwei Ausdrücken abgerufen wird.  
  
```javascript  
var x = Math.min(107 - 3, 48 * 90);  
document.write(x);  
  
// Output:  
// 104  
```  
  
## Anforderungen  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## Siehe auch  
 [Math.max\-Funktion](../../javascript/reference/math-max-function-javascript.md)