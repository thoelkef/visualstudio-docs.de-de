---
title: "Promise.resolve-Funktion (Promise) | Microsoft Docs"
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
ms.assetid: 0fb6bff9-54ab-41be-97d7-04f7e6fe9cff
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# Promise.resolve-Funktion (Promise)
Erstellt eine neue aufgelöste Zusage mit einem Ergebnis, das seinem Argument entspricht.  
  
## Syntax  
  
```  
Promise.resolve(x)  
```  
  
#### Parameter  
 `x`  
 Erforderlich.  Der mit der abgeschlossenen Zusage zurückgegebene Wert.  
  
## Hinweise  
 Die Funktion zur Behandlung der Erfüllung der `then`\-Methode wird ausgeführt, wenn das abgeschlossene Promise\-Objekt zurückgegeben wird.  
  
## Beispiel  
  
```javascript  
var p = Promise.resolve('success');  
p.then(function(result) {  
    console.log(result);  
});  
  
// Output:  
// success  
```  
  
## Anforderungen  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]  
  
## Siehe auch  
 [Promise\-Objekt](../../javascript/reference/promise-object-javascript.md)