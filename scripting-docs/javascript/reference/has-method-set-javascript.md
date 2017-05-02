---
title: "has-Methode (Set) (JavaScript) | Microsoft Docs"
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
ms.assetid: fb80f2e0-fc5e-4508-af14-1c3b3b833636
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# has-Methode (Set) (JavaScript)
Gibt `true` zurück, wenn der Satz das angegebene Element enthält.  
  
## Syntax  
  
```javascript  
setObj.has(value)  
```  
  
#### Parameter  
 `setObj`  
 Erforderlich.  Ein `Set`\-Objekt.  
  
 `value`  
 Erforderlich.  Das zu testende Element.  
  
## Eigenschaftswert\/Rückgabewert  
 `true`, wenn der Satz das angegebene Element enthält.  
  
## Beispiel  
 Im folgenden Beispiel wird gezeigt, wie Sie einem `Set` Member hinzufügen und anschließend überprüfen, ob der Satz einen bestimmten Member enthält.  
  
```javascript  
var s = new Set();  
s.add("Thomas Jefferson");  
s.add(1776);  
  
document.write(s.has(1776));  
document.write(s.has("1776"));  
  
// Output:  
// true  
// false  
  
```  
  
## Anforderungen  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]