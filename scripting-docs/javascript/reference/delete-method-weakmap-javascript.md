---
title: "delete-Methode (WeakMap) (JavaScript) | Microsoft Docs"
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
ms.assetid: 7d54ae55-e514-45ba-b403-d1eee46837d2
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# delete-Methode (WeakMap) (JavaScript)
Entfernt das angegebene Element aus einem `WeakMap`\-Objekt.  
  
## Syntax  
  
```javascript  
weakmapObj.delete(key)  
```  
  
#### Parameter  
 `weakmapObj`  
 Erforderlich.  Ein `WeakMap`\-Objekt.  
  
 `key`  
 Erforderlich.  Der Schlüssel des zu entfernenden Elements.  
  
## Eigenschaftswert\/Rückgabewert  
 `true`, wenn das Element entfernt wurde.  
  
## Beispiel  
 Im folgenden Beispiel wird gezeigt, wie Sie einer `WeakMap` ein Member hinzufügen und es dann löschen.  
  
```javascript  
function Dog(breed) {  
    this.breed = breed;  
}  
  
var dog = new Dog("yorkie");  
  
var wm = new WeakMap();  
wm.set(dog, "fido");  
wm.delete(dog);  
```  
  
## Anforderungen  
 [!INCLUDE[jsv11](../../includes/jsv11-md.md)]