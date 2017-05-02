---
title: "values-Methode (Array) (JavaScript) | Microsoft Docs"
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
ms.assetid: b20699d6-f8b1-4744-8551-9e81c82850dd
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# values-Methode (Array) (JavaScript)
Gibt einen Iterator zurück, der die Werte des Arrays zurückgibt.  
  
## Syntax  
  
```  
arrayObj.values();  
```  
  
#### Parameter  
 `arrayObj`  
 Erforderlich.  Das Arrayobjekt.  
  
## Hinweise  
  
## Beispiel  
 Das folgende Beispiel zeigt, wie die Werte eines Arrays abgerufen werden.  
  
```javascript  
var v = ["a", "b", "c"].values();  
// v.next().value == "a"  
// v.next().value == "b"  
// v.next().value == "c"   
```  
  
## Anforderungen  
 [!INCLUDE[jsv12](../../includes/jsv12-md.md)]