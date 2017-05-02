---
title: "get-Methode (WeakMap) (JavaScript) | Microsoft Docs"
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
ms.assetid: d922c55d-486d-4feb-aedc-1f4867c417d2
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# get-Methode (WeakMap) (JavaScript)
Gibt ein angegebenes Element aus einem `WeakMap`\-Objekt zurück.  
  
## Syntax  
  
```javascript  
weakmapObj.get(key)  
```  
  
#### Parameter  
 `weakmapObj`  
 Erforderlich.  Ein `WeakMap`\-Objekt.  
  
 `key`  
 Erforderlich.  Der Schlüssel eines Elements in der `WeakMap`.  
  
## Eigenschaftswert\/Rückgabewert  
 Gibt das Objekt zurück, das dem Schlüssel zugeordnet ist.  Wenn die `WeakMap` den Schlüssel nicht enthält, gibt diese Methode einen `undefined`\-Wert zurück.  
  
## Beispiel  
 Im folgenden Beispiel wird veranschaulicht, wie Member aus einem `WeakMap`\-Objekt abgerufen werden.  
  
```javascript  
var dog = {  
    breed: "yorkie"  
}  
  
var cat = {  
    breed: "burmese"  
}  
  
var wm = new WeakMap();  
wm.set(dog, "fido");  
wm.set(cat, "pepper");  
  
document.write(wm.get(dog) + ": ");  
document.write(dog.breed);  
document.write("<br />");  
document.write(wm.get(cat) + ": ");  
document.write(cat.breed);  
  
// Output:  
// fido: yorkie  
// pepper: burmese  
  
```  
  
## Anforderungen  
 [!INCLUDE[jsv11](../../includes/jsv11-md.md)]