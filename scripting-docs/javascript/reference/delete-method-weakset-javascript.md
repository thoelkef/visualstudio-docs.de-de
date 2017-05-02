---
title: "delete-Methode (WeakSet) (JavaScript) | Microsoft Docs"
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
ms.assetid: 19e93366-7d42-4abf-b7b9-fcf943fa17a3
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# delete-Methode (WeakSet) (JavaScript)
Entfernt das angegebene Element aus einem `WeakSet`.  
  
## Syntax  
  
```javascript  
weaksetObj.delete(obj)  
```  
  
#### Parameter  
 `weaksetObj`  
 Erforderlich.  Ein `WeakSet`\-Objekt.  
  
 `obj`  
 Erforderlich.  Das zu entfernende Element.  
  
## Eigenschaftswert\/Rückgabewert  
 `true`, wenn das Element entfernt wurde.  
  
## Beispiel  
 Im folgenden Beispiel wird gezeigt, wie Elemente einem `WeakSet` hinzugefügt und daraus gelöscht werden.  
  
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