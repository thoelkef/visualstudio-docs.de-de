---
title: "keys-Methode (Array) (JavaScript) | Microsoft Docs"
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
ms.assetid: fc5b6a30-642c-4bd7-ad31-a42667af2f3f
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# keys-Methode (Array) (JavaScript)
Gibt einen Iterator zurück, der die Indexwerte des Arrays zurückgibt.  
  
## Syntax  
  
```  
arrayObj.keys();  
```  
  
#### Parameter  
 `arrayObj`  
 Erforderlich.  Das Arrayobjekt.  
  
## Hinweise  
  
## Beispiel  
 Das folgende Beispiel zeigt, wie die Schlüsselwerte eines Arrays abgerufen werden.  
  
```javascript  
var k = ["a", "b", "c"].keys();  
// k.next().value == 0  
// k.next().value == 1  
// k.next().value == 2   
```  
  
## Anforderungen  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]