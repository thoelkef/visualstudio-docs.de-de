---
title: "Number.isSafeInteger (Zahl) (JavaScript) | Microsoft Docs"
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
ms.assetid: c7ef6ce8-fe71-4e53-be44-4dd440aef21d
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# Number.isSafeInteger (Zahl) (JavaScript)
Gibt einen booleschen Wert zurück, der angibt, ob eine Zahl gefahrlos in JavaScript dargestellt werden kann.  
  
## Syntax  
  
```  
Number.isSafeInteger(numValue)   
```  
  
## Rückgabewert  
 `true`, wenn die Zahl zwischen `Number.MIN_SAFE_INTEGER` und `Number.MAX_SAFE_INTEGER` \(einschließlich\) liegt, andernfalls `false`.  
  
## Hinweise  
 Eine sichere ganze Zahl in JavaScript ist eine IEEE 754\-Zahl mit doppelter Genauigkeit vor Anwenden einer Rundung.  
  
## Beispiel  
  
```javascript  
// Returns true  
Number.isSafeInteger(-100)  
Number.isSafeInteger(9007199254740991)  
  
// Returns false  
Number.isSafeInteger(Number.NaN)  
Number.isSafeInteger(Infinity)  
Number.isSafeInteger("100")  
Number.isSafeInteger(9007199254740992);  
```  
  
## Anforderungen  
 [!INCLUDE[jsv12](../../includes/jsv12-md.md)]  
  
 **Gilt für**: [Number\-Objekt](../../javascript/reference/number-object-javascript.md)