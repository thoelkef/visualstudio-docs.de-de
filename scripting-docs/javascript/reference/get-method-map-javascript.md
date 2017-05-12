---
title: "get-Methode (Map) (JavaScript) | Microsoft Docs"
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
ms.assetid: bebbd6bc-6e61-4674-8196-7e907798973f
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# get-Methode (Map) (JavaScript)
Gibt ein angegebenes Element aus einer Zuordnung zurück.  
  
## Syntax  
  
```javascript  
mapObj.get(key)  
```  
  
#### Parameter  
 `mapObj`  
 Erforderlich.  Ein `Map`\-Objekt.  
  
 `key`  
 Erforderlich.  Der Schlüssel eines Elements in der `Map`.  
  
## Eigenschaftswert\/Rückgabewert  
 Gibt das Objekt zurück, das dem Schlüssel zugeordnet ist.  Wenn die `Map` den Schlüssel nicht enthält, gibt diese Methode einen `undefined`\-Wert zurück.  
  
## Beispiel  
 Das folgende Beispiel zeigt, wie ein Element aus einem `Map`\-Objekt abgerufen wird.  
  
```javascript  
var m = new Map();  
m.set(1, "black");  
m.set(2, "red");  
m.set("colors", 2);  
  
document.write(m.get(2));  
  
// Output:  
// red  
  
```  
  
## Anforderungen  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]