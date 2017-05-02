---
title: "constructor-Eigenschaft (Array) | Microsoft Docs"
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
ms.assetid: b78d517b-cb56-4866-b30f-ef8121a27843
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# constructor-Eigenschaft (Array)
Gibt die Funktion an, mit der ein Array erstellt wird.  
  
## Syntax  
  
```  
  
array.constructor  
```  
  
## Hinweise  
 Der erforderliche `array`\-Parameter enthält den Namen eines Arrays.  
  
 Die `constructor`\-Eigenschaft ist ein Member des Prototyps eines jeden Objekts, das einen Prototyp besitzt.  Dies schließt alle systeminternen [!INCLUDE[javascript](../../includes/javascript-md.md)]\-Objekte mit Ausnahme der Objekte `Global` und `Math` ein.  Die `constructor`\-Eigenschaft enthält einen Verweis auf die Funktion, mit der die Instanzen des betreffenden Objekts erstellt werden.  
  
## Beispiel  
 Das folgende Beispiel veranschaulicht die Verwendung der constructor\-Eigenschaft.  
  
```javascript  
var x = new Array();  
  
if (x.constructor == Array)  
    document.write("Object is an Array.");  
else  
    document.write("Object is not an Array.");  
  
// Output:  
// Object is an Array.  
  
```  
  
## Anforderungen  
 [!INCLUDE[jsv2](../../includes/jsv2-md.md)]