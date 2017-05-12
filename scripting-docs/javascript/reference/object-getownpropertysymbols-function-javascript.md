---
title: "Object.getOwnPropertySymbols-Funktion (JavaScript) | Microsoft Docs"
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
ms.assetid: 68dd69b9-5a33-44c2-ba5f-21a4ae6c0879
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# Object.getOwnPropertySymbols-Funktion (JavaScript)
Gibt die eigenen Symboleigenschaften eines Objekts zurück.  Die eigenen Symboleigenschaften eines Objekts sind diejenigen, die direkt für dieses Objekt definiert sind und nicht vom Prototyp des Objekts geerbt werden.  
  
## Syntax  
  
```  
Object.getOwnPropertySymbols(object);  
```  
  
#### Parameter  
 `object`  
 Erforderlich.  Das Objekt, das die eigenen Symbole enthält.  
  
## Rückgabewert  
 Ein Array, das die eigenen Symbolen des Objekts enthält.  
  
## Hinweise  
 Sie müssen `Object.getOwnPropertySymbols` verwenden, um die Symboleigenschaften eines Objekts abzurufen.  `Object.getOwnPropertyNames` gibt die Symboleigenschaften nicht zurück.  
  
## Beispiel  
 Das folgende Codebeispiel zeigt, wie die Symboleigenschaften eines Objekts abgerufen werden.  
  
```javascript  
var obj = {};  
var key = Symbol('description');  
  
obj[key] = 'data';  
  
var symbols = Object.getOwnPropertySymbols(obj);  
  
console.log(s[0].toString());  
  
// Output:  
// undefined  
// Symbol(description)  
```  
  
## Anforderungen  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]