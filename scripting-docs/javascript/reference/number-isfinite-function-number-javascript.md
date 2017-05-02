---
title: "Number.isFinite-Funktion (Zahl) (JavaScript) | Microsoft Docs"
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
ms.assetid: 41a91408-09d1-49f2-b7a0-6da105e2ed8e
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# Number.isFinite-Funktion (Zahl) (JavaScript)
Gibt einen booleschen Wert zurück, der angibt, ob ein Wert eine endliche Zahl ist.  
  
## Syntax  
  
```  
Number.isFinite(numValue)   
```  
  
## Rückgabewert  
 `false`, wenn der Wert `NaN`, `+∞` oder `-∞` ist; andernfalls `true`.  
  
## Hinweise  
  
## Beispiel  
  
```javascript  
// Returns true  
Number.isFinite(100)  
Number.isFinite(-100)  
Number.isFinite(100 / 3)  
  
// Returns false  
Number.isFinite(Number.NaN)  
Number.isFinite(Infinity)  
Number.isFinite("100")  
```  
  
## Anforderungen  
 [!INCLUDE[jsv12](../../includes/jsv12-md.md)]  
  
 **Gilt für**: [Number\-Objekt](../../javascript/reference/number-object-javascript.md)