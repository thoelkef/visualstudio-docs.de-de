---
title: "constructor-Eigenschaft (WeakMap) | Microsoft Docs"
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
ms.assetid: 1e3f9333-ce75-4d32-9b14-fbe81fd73dfb
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# constructor-Eigenschaft (WeakMap)
Gibt die Funktion an, durch die ein `WeakMap`\-Objekt erstellt wird.  
  
## Syntax  
  
```javascript  
weakmap.constructor  
```  
  
## Hinweise  
 Der erforderliche `weakmap`\-Parameter ist der Name des `WeakMap`\-Objekts.  
  
 Die `constructor`\-Eigenschaft ist ein Member des Prototyps eines jeden Objekts, das einen Prototyp besitzt.  Dies schließt alle systeminternen JavaScript\-Objekte mit Ausnahme der Objekte `Global` und `Math` ein.  Die `constructor`\-Eigenschaft enthält einen Verweis auf die Funktion, mit der die Instanzen des betreffenden Objekts erstellt werden.  
  
## Anforderungen  
 [!INCLUDE[jsv11](../../includes/jsv11-md.md)]