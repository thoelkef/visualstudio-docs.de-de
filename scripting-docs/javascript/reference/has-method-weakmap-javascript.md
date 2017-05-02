---
title: "has-Methode (WeakMap) (JavaScript) | Microsoft Docs"
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
ms.assetid: 12bedca1-bde7-413a-a4e2-06c03559044f
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# has-Methode (WeakMap) (JavaScript)
Gibt `true` zurück, wenn das `WeakMap`\-Objekt das angegebene Element enthält.  
  
## Syntax  
  
```javascript  
weakmapObj.has(key)  
```  
  
#### Parameter  
 `weakmapObj`  
 Erforderlich.  Ein `WeakMap`\-Objekt.  
  
 `key`  
 Erforderlich.  Der Schlüssel des zu testenden Elements.  
  
## Eigenschaftswert\/Rückgabewert  
 `true`, wenn `WeakMap` den angegebenen Schlüssel enthält.  
  
## Beispiel  
 Im folgenden Beispiel wird gezeigt, wie Sie einer `WeakMap` ein Member hinzufügen und dann mit `has` prüfen, ob es vorhanden ist.  
  
```javascript  
var dog = {  
    breed: "yorkie"  
}  
  
var wm = new WeakMap();  
wm.set(dog, "fido");  
  
document.write(wm.has(dog));  
  
// Output:  
// true  
```  
  
## Anforderungen  
 [!INCLUDE[jsv11](../../includes/jsv11-md.md)]