---
title: "Promise.reject-Funktion (Promise) | Microsoft Docs"
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
ms.assetid: 9746e15b-9717-4e36-bf6b-910dcc6cd667
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# Promise.reject-Funktion (Promise)
Erstellt ein neues abgelehntes Versprechen mit einem Ergebnis, das dem übergebenen Argument entspricht.  
  
## Syntax  
  
```  
Promise.reject(r);  
```  
  
#### Parameter  
 `r`  
 Erforderlich.  Der Grund, warum das Versprechen abgelehnt wurde.  
  
## Hinweise  
 Die Fehlerbehandlungsfunktion der `then`\- oder `catch`\-Methode wird ausgeführt, wenn das abgelehnte Versprechen zurückgegeben wird.  
  
## Beispiel  
  
```javascript  
var p = Promise.reject('failure');  
p.catch(function(result) {  
    console.log(result);  
});  
  
// Output:  
// failure  
```  
  
## Anforderungen  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]  
  
## Siehe auch  
 [Promise\-Objekt](../../javascript/reference/promise-object-javascript.md)