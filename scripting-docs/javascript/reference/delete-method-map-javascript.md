---
title: "delete-Methode (Map) (JavaScript) | Microsoft Docs"
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
ms.assetid: a073e1a1-5862-485b-b2bd-26c66a3aff51
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# delete-Methode (Map) (JavaScript)
Entfernt das angegebene Element aus einer Zuordnung.  
  
## Syntax  
  
```javascript  
mapObj.delete(key)  
```  
  
#### Parameter  
 `mapObj`  
 Erforderlich.  Ein `Map`\-Objekt.  
  
 `key`  
 Erforderlich.  Der Schlüssel des zu entfernenden Elements.  
  
## Eigenschaftswert\/Rückgabewert  
 `true`, wenn das Element entfernt wurde.  
  
## Beispiel  
 Im folgenden Beispiel wird gezeigt, wie Sie einer `Map` Member hinzufügen und dann ein Member löschen.  
  
```javascript  
var m = new Map();  
m.set(1, "black");  
m.set(2, "red");  
m.set("colors", 2);  
m.delete(1);  
  
m.forEach(function (item) {  
    document.write(item.toString() + "<br />");  
});  
  
// Output:  
// red  
// 2  
```  
  
## Anforderungen  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]