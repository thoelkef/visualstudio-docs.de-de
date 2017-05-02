---
title: "constructor-Eigenschaft (Map) | Microsoft Docs"
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
ms.assetid: a90d6a29-bd64-4e01-8d2f-988b7e3e4a24
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# constructor-Eigenschaft (Map)
Gibt die Funktion an, durch die eine Zuordnung erstellt wird.  
  
## Syntax  
  
```javascript  
map.constructor  
```  
  
## Hinweise  
 Die erforderliche `map` ist der Name der Zuordnung.  
  
 Die `constructor`\-Eigenschaft ist ein Member des Prototyps eines jeden Objekts, das einen Prototyp besitzt.  Dies schließt alle systeminternen JavaScript\-Objekte mit Ausnahme der Objekte `Global` und `Math` ein.  Die `constructor`\-Eigenschaft enthält einen Verweis auf die Funktion, mit der die Instanzen des betreffenden Objekts erstellt werden.  
  
## Anforderungen  
 [!INCLUDE[jsv11](../../includes/jsv11-md.md)]