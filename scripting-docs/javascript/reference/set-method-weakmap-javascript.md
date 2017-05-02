---
title: "set-Methode (WeakMap) (JavaScript) | Microsoft Docs"
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
ms.assetid: 29fc72b1-224f-4f19-8c06-5d926d695b03
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# set-Methode (WeakMap) (JavaScript)
Fügt einem `WeakMap`\-Objekt ein neues Element hinzu.  
  
## Syntax  
  
```javascript  
weakmapObj.set(key, value)  
```  
  
#### Parameter  
 `weakmapObj`  
 Erforderlich.  Ein `WeakMap`\-Objekt.  
  
 `key`  
 Erforderlich.  Ein Objekt, das den Schlüssel des hinzuzufügenden Elements darstellt.  Dies muss ein Objektverweis sein.  
  
 `value`  
 Erforderlich.  Der Wert des hinzuzufügenden Elements.  
  
## Eigenschaftswert\/Rückgabewert  
 Gibt das `WeakMap`\-Objekt zurück, das das neue Schlüssel\-Wert\-Paar enthält.  
  
## Hinweise  
 Wenn Sie einen Wert mithilfe eines vorhandenen Schlüssels zur Auflistung hinzufügen, ersetzt der neue Wert den alten Wert.  
  
## Beispiel  
 Im folgenden Beispiel wird veranschaulicht, wie einem `WeakMap`\-Objekt Member hinzugefügt werden.  
  
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
```  
  
## Anforderungen  
 [!INCLUDE[jsv11](../../includes/jsv11-md.md)]