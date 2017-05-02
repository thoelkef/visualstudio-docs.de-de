---
title: "add-Methode (WeakSet) (JavaScript) | Microsoft Docs"
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
ms.assetid: d35d0287-6b33-4720-b9d7-8954c428ce4e
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# add-Methode (WeakSet) (JavaScript)
Fügt `WeakSet` ein neues Element hinzu.  
  
## Syntax  
  
```javascript  
weaksetObj.add(obj)  
```  
  
#### Parameter  
 `weaksetObj`  
 Erforderlich.  Ein `WeakSet`\-Objekt.  
  
 `obj`  
 Erforderlich.  Neues Element des `WeakSet`\-Objekts.  
  
## Hinweise  
 Das neue Element muss ein eindeutiges Objekt und darf kein beliebiger Wert sein.  Wenn Sie einem `WeakSet` ein nicht eindeutiges Element hinzufügen, wird das neue Element der Auflistung nicht hinzugefügt.  
  
## Beispiel  
 Im folgenden Beispiel wird gezeigt, wie Sie einem Satz Member hinzufügen und anschließend prüfen, ob sie hinzugefügt wurden.  
  
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
 [!INCLUDE[jsv12](../../includes/jsv12-md.md)]