---
title: "constructor-Eigenschaft (Zahl) | Microsoft Docs"
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
ms.assetid: a348fe53-1b4a-42f5-964b-53d57342c906
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# constructor-Eigenschaft (Zahl)
Gibt die Funktion an, mit der ein Number\-Objekt erstellt wird.  
  
## Syntax  
  
```  
  
number.constructor  
```  
  
## Hinweise  
 Der erforderliche `number`\-Parameter ist der Name einer Zeichenfolge.  
  
 Die `constructor`\-Eigenschaft ist ein Member des Prototyps eines jeden Objekts, das einen Prototyp besitzt.  Dies schließt alle systeminternen [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]\-Objekte mit Ausnahme der Objekte `Global` und `Math` ein.  Die `constructor`\-Eigenschaft enthält einen Verweis auf die Funktion, mit der die Instanzen des betreffenden Objekts erstellt werden.  
  
## Beispiel  
 Das folgende Beispiel veranschaulicht die Verwendung der constructor\-Eigenschaft.  
  
```javascript  
var num = new Number();  
  
if (num.constructor == Number)  
    document.write("Object is a Number.");  
else  
    document.write("Object is not a Number.");  
  
// Output:  
// Object is a Number.  
  
```  
  
## Anforderungen  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]