---
title: "constructor-Eigenschaft (Fehler) | Microsoft Docs"
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
ms.assetid: 18aea278-2bd5-457b-83a5-d8d8f1226e0c
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# constructor-Eigenschaft (Fehler)
Gibt die Funktion an, durch die ein Fehler erstellt wird.  
  
## Syntax  
  
```  
  
error.constructor  
```  
  
## Hinweise  
 Der erforderliche `error`\-Parameter ist der Name eines Fehlerobjekts.  
  
 Die `constructor`\-Eigenschaft ist ein Member des Prototyps eines jeden Objekts, das einen Prototyp besitzt.  Die `constructor`\-Eigenschaft enthält einen Verweis auf die Funktion, mit der die Instanzen des betreffenden Objekts erstellt werden.  
  
## Beispiel  
 Das folgende Beispiel veranschaulicht die Verwendung der constructor\-Eigenschaft.  
  
```javascript  
var x = new Error("This is an error");  
  
if (x.constructor == Error)  
    document.write("Object is an error.");  
  
// Output:  
// Object is an error.  
  
```  
  
## Anforderungen  
 [!INCLUDE[jsv2](../../includes/jsv2-md.md)]