---
title: "has-Methode (WeakSet) (JavaScript) | Microsoft Docs"
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
ms.assetid: e24f0876-26bd-4007-b12a-360bb6fa0951
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# has-Methode (WeakSet) (JavaScript)
Gibt `true` zurück, wenn `WeakSet` das angegebene Element enthält.  
  
## Syntax  
  
```javascript  
setObj.has(obj)  
```  
  
#### Parameter  
 `setObj`  
 Erforderlich.  Ein `WeakSet`\-Objekt.  
  
 `obj`  
 Erforderlich.  Das zu testende Element.  
  
## Eigenschaftswert\/Rückgabewert  
 `true`, wenn der Satz das angegebene Element enthält.  
  
## Beispiel  
 Im folgenden Beispiel wird gezeigt, wie Sie einem `WeakSet` Member hinzufügen und anschließend überprüfen, ob der Satz einen bestimmten Member enthält.  
  
```javascript  
var ws = new WeakSet();  
  
var str = new String("Thomas Jefferson");  
var num = new Number(1776);  
  
ws.add(str);  
ws.add(num);  
  
console.log(ws.has(str));  
console.log(ws.has(num));  
  
ws.delete(str);  
console.log(ws.has(str));  
  
// Output:  
// true  
// true  
// false  
  
```  
  
## Anforderungen  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]