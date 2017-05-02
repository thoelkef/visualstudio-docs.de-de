---
title: "Math.hypot-Funktion (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: 31488f5a-2230-4114-911e-b6d854c7b0a0
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# Math.hypot-Funktion (JavaScript)
Gibt die Quadratwurzel der Summe der Quadrate der Argumente zurück.  
  
## Syntax  
  
```  
Math.hypot ( value1[, value2[, ...values] );  
```  
  
#### Parameter  
 `value1`  
 Erforderlich.  Die erste Zahl.  
  
 `value2`  
 Optional.  Die zweite Zahl.  
  
 `values`  
 Optional.  Eine oder mehrere Zahlen.  
  
## Hinweise  
 Wenn ein Argument NaN lautet, gibt die Funktion NaN zurück.  Wenn keine Argumente angegeben sind, gibt die Funktion 0 zurück.  
  
## Beispiel  
 Das folgende Beispiel zeigt, wie die `Math.hypot`\-Funktion verwendet wird.  
  
```javascript  
Math.hypot(3, 4);  
// Returns 5  
  
Math.hypot(3, "4");  
// Returns 5  
  
Math.hypot(3, "four");  
// Returns NaN   
  
Math.hypot(3, 4, 10);  
// Returns 11.180339887498949  
  
```  
  
## Anforderungen  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]