---
title: "add-Methode (Set) (JavaScript) | Microsoft Docs"
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
ms.assetid: b4eea447-fd5b-4380-978e-1b95f6dbc438
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# add-Methode (Set) (JavaScript)
Fügt einem Satz ein neues Element hinzu.  
  
## Syntax  
  
```javascript  
setObj.add(value)  
```  
  
#### Parameter  
 `setObj`  
 Erforderlich.  Ein `Set`\-Objekt.  
  
 `value`  
 Erforderlich.  Neues Element des `Set`\-Objekts.  
  
## Hinweise  
 Das neue Element kann einem beliebigen Typ angehören und muss eindeutig sein.  Wenn Sie einem `Set` ein nicht eindeutiges Element hinzufügen, wird das neue Element der Auflistung nicht hinzugefügt.  
  
## Beispiel  
 Im folgenden Beispiel wird gezeigt, wie Sie einem Satz Member hinzufügen und sie dann abrufen.  
  
```javascript  
var s = new Set();  
s.add("Thomas Jefferson");  
s.add(1776);  
s.add("founding father");  
  
s.forEach(function (item) {  
    document.write(item.toString() + ", ");  
});  
  
// Output:  
// Thomas Jefferson, 1776, founding father,  
  
```  
  
## Anforderungen  
 [!INCLUDE[jsv11](../../includes/jsv11-md.md)]