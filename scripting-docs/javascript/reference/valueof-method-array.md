---
title: "valueOf-Methode (Array) | Microsoft Docs"
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
ms.assetid: b694fe65-1297-4580-8af2-406932c06454
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# valueOf-Methode (Array)
Gibt den einfachen Wert des angegebenen Objekts zurück.  
  
## Syntax  
  
```  
  
array.valueOf()  
```  
  
#### Parameter  
 Diese Methode hat keine Parameter.  
  
## Rückgabewert  
 Gibt die Arrayinstanz zurück.  
  
## Hinweise  
 Im folgenden Beispiel ist das instanziierte Arrayobjekt mit dem Rückgabewert dieser Methode identisch.  
  
```javascript  
var arr = [1, 2, 3, 4];  
var s = arr.valueOf();  
  
if (arr === s)  
document.write("same");  
else  
document.write("different");  
  
// Output:  
// same  
  
```  
  
## Anforderungen  
 [!INCLUDE[jsv2](../../includes/jsv2-md.md)]