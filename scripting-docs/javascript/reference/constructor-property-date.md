---
title: "constructor-Eigenschaft (Datum) | Microsoft Docs"
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
ms.assetid: 5db153a1-788b-4a61-bfc8-2d2ec38f36ea
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# constructor-Eigenschaft (Datum)
Gibt die Funktion an, mit der ein Datum erstellt wird.  
  
## Syntax  
  
```  
  
date.constructor  
```  
  
## Hinweise  
 Der erforderliche `date`\-Parameter ist der Name eines Datumsobjekts.  
  
 Die `constructor`\-Eigenschaft ist ein Member des Prototyps eines jeden Objekts, das einen Prototyp besitzt.  Die `constructor`\-Eigenschaft enthält einen Verweis auf die Funktion, mit der die Instanzen des betreffenden Objekts erstellt werden.  
  
## Beispiel  
 Das folgende Beispiel veranschaulicht die Verwendung der constructor\-Eigenschaft.  
  
```javascript  
var x = new Date("Hi");  
  
if (x.constructor == Date)  
    document.write("Object is a date.");  
  
// Output:  
// Object is a date.  
  
```  
  
## Anforderungen  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]