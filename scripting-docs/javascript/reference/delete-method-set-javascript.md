---
title: "delete-Methode (Set) (JavaScript) | Microsoft Docs"
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
ms.assetid: 052c409e-10c9-49f2-955d-5ad7e31c14f3
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# delete-Methode (Set) (JavaScript)
Entfernt das angegebene Element aus einem Satz.  
  
## Syntax  
  
```javascript  
setObj.delete(value)  
```  
  
#### Parameter  
 `setObj`  
 Erforderlich.  Ein `Set`\-Objekt.  
  
 `value`  
 Erforderlich.  Das zu entfernende Element.  
  
## Eigenschaftswert\/Rückgabewert  
 `true`, wenn das Element entfernt wurde.  
  
## Beispiel  
 Im folgenden Beispiel wird gezeigt, wie Sie einem `Set` Member hinzufügen und dann ein Member löschen.  
  
```javascript  
var s = new Set();  
s.add("Thomas Jefferson");  
s.add(1776);  
s.add("founding father");  
s.delete("founding father");  
  
s.forEach(function (item) {  
    document.write(item.toString() + ", ");  
});  
  
// Output:  
// Thomas Jefferson, 1776,  
```  
  
## Anforderungen  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]