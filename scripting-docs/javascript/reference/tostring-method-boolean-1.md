---
title: "toString-Methode (Boolesch) | Microsoft Docs"
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
ms.assetid: c46b43c0-6946-407a-b0e0-49cba90e226a
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# toString-Methode (Boolesch)
Gibt eine Zeichenfolgendarstellung eines Objekts zurück.  
  
## Syntax  
  
```  
  
boolean.toString()  
```  
  
## Parameter  
 `boolean`  
 Erforderlich.  Ein Objekt, für das eine Zeichenfolgendarstellung abgerufen wird.  
  
## Rückgabewert  
 Ist der Boolesche Wert `true`, wird "true" zurückgegeben.  Andernfalls wird "false" zurückgegeben.  
  
## Hinweise  
  
## Beispiel  
 Das folgende Beispiel veranschaulicht die Verwendung der **toString**\-Methode.  
  
```javascript  
var s = new Boolean(0);  
document.write(s.toString());  
  
// Output: false;  
  
```  
  
## Anforderungen  
 [!INCLUDE[jsv2](../../includes/jsv2-md.md)]