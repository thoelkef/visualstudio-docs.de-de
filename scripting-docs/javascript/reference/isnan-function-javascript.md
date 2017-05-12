---
title: "isNaN-Funktion (JavaScript) | Microsoft Docs"
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
  - "isNaN"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "isNaN-Methode"
ms.assetid: 5af4eb29-72f6-484f-93bd-04ae1261f849
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# isNaN-Funktion (JavaScript)
Gibt einen booleschen Wert zurück, der angibt, ob ein Wert der reservierte Wert `NaN` \(Not a Number\) ist.  
  
## Syntax  
  
```  
isNaN(numValue)   
```  
  
## Rückgabewert  
 `true`, wenn der in den `Number`\-Typ konvertierte Wert gleich `NaN` ist, andernfalls `false`.  
  
## Hinweise  
 Die erforderliche `numValue`\-Angabe ist der auf `NaN` zu testende Wert.  
  
 Diese Methode wird in der Regel verwendet, um Rückgabewerte der Methoden `parseInt` und `parseFloat` zu testen.  
  
 Alternativ kann eine Variable, die `NaN` oder einen anderen Wert enthält, mit sich selbst verglichen werden.  Ergibt der Vergleich eine Ungleichheit, so hat die Variable den Wert `NaN`.  Dies liegt daran, dass `NaN` der einzige Wert ist, der nicht mit sich selbst gleich ist.  
  
## Anforderungen  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Gilt für**: [Global\-Objekt](../../javascript/reference/global-object-javascript.md)  
  
## Beispiel  
  
```javascript  
// Returns false.  
isNaN(100);  
  
// Returns false.  
isNaN("100");  
  
// Returns true.  
isNaN("ABC");  
  
// Returns true.  
isNaN("10C");  
  
// Returns true.  
isNaN("abc123");  
  
// Returns true.  
isNaN(Math.sqrt(-1));           
```  
  
## Siehe auch  
 [isFinite\-Funktion](../../javascript/reference/isfinite-function-javascript.md)   
 [NaN\-Konstante](../../javascript/reference/nan-constant-javascript.md)   
 [parseFloat\-Funktion](../../javascript/reference/parsefloat-function-javascript.md)   
 [parseInt\-Funktion](../../javascript/reference/parseint-function-javascript.md)