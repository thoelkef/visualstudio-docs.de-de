---
title: "Math.clz32-Funktion (JavaScript) | Microsoft Docs"
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
ms.assetid: 34615d7a-6d88-4ab5-a696-7e496caa51db
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# Math.clz32-Funktion (JavaScript)
Gibt die Anzahl führender Nullbits in der 32\-Bit\-Binärdarstellung einer Zahl zurück.  
  
## Syntax  
  
```  
  
Math.clz32(  
number  
)   
```  
  
## Hinweise  
 Wenn `number` 0 ist, lautet das Ergebnis 32.  Wenn das wichtigste Bit der 32\-Bit\-Binärverschlüsselung von `number` 1 ist, lautet das Ergebnis 0.  
  
## Anforderungen  
 [!INCLUDE[jsv12](../../includes/jsv12-md.md)]  
  
 **Gilt für**: [Math\-Objekt](../../javascript/reference/math-object-javascript.md)