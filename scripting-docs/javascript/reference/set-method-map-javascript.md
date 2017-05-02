---
title: "set-Methode (Map) (JavaScript) | Microsoft Docs"
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
ms.assetid: 31ee71a0-b09d-442a-9e02-825accf94ffa
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# set-Methode (Map) (JavaScript)
Fügt einer Zuordnung ein neues Element hinzu.  
  
## Syntax  
  
```javascript  
mapObj.set(key, value)  
```  
  
#### Parameter  
 `mapObj`  
 Erforderlich.  Ein `Map`\-Objekt.  
  
 `key`  
 Erforderlich.  Der Schlüssel für das neue Element.  
  
 `value`  
 Erforderlich.  Der Wert des hinzuzufügenden Elements.  
  
## Eigenschaftswert\/Rückgabewert  
 Gibt das `Map`\-Objekt zurück, das das neue Schlüssel\-Wert\-Paar enthält.  
  
## Hinweise  
 Wenn Sie einen Wert mithilfe eines vorhandenen Schlüssels zur Auflistung hinzufügen, ersetzt der neue Wert den alten Wert.  
  
## Beispiel  
 Im folgenden Beispiel wird gezeigt, wie Sie einer `Map` Member hinzufügen und sie dann abrufen.  
  
```javascript  
var m = new Map();  
m.set(1, "black");  
m.set(2, "red");  
m.set("colors", 2);  
  
m.forEach(function (item) {  
    document.write(item.toString() + "<br />");  
});  
  
// Output:  
// black  
// red  
// 2  
```  
  
## Anforderungen  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]