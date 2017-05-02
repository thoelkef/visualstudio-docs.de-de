---
title: "has-Methode (Map) (JavaScript) | Microsoft Docs"
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
ms.assetid: 876df854-2941-4db2-92c6-1b497840b169
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# has-Methode (Map) (JavaScript)
Gibt `true` zurück, wenn die Zuordnung das angegebene Element enthält.  
  
## Syntax  
  
```javascript  
mapObj.has(key)  
```  
  
#### Parameter  
 `mapObj`  
 Erforderlich.  Ein `Map`\-Objekt.  
  
 `key`  
 Erforderlich.  Der Schlüssel des zu testenden Elements.  
  
## Eigenschaftswert\/Rückgabewert  
 `true`, wenn die Zuordnung das angegebene Element enthält.  
  
## Beispiel  
 Im folgenden Beispiel wird gezeigt, wie Sie einer `Map` ein Member hinzufügen und anschließend überprüfen, ob die Zuordnung es enthält.  
  
```javascript  
var m = new Map();  
m.set(2, "red");  
  
document.write(m.has(2));  
  
// Output:  
// true  
```  
  
## Anforderungen  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]