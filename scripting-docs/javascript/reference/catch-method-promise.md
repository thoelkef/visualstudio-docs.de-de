---
title: "catch-Methode (Promise) | Microsoft Docs"
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
ms.assetid: 55266f6a-db4d-4de8-857a-8bc7d35ed4b8
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# catch-Methode (Promise)
Ermöglicht Ihnen das Angeben des Verfahrens, das bei Ablehnung einer Zusage durchzuführen ist.  
  
## Syntax  
  
```  
  
promise.catch(onRejected)  
```  
  
#### Parameter  
 `promise`  
 Erforderlich.  Das Promise\-Objekt.  
  
 `onRejected`  
 Erforderlich.  Die Fehlerhandlerfunktion, die bei Ablehnung einer Zusage auszuführen ist.  
  
## Hinweise  
  
## Beispiel  
 In diesem Code wird der erste Aufruf des Timeouts nach 5000 ms zurückgegeben.  In diesem Code wird die Zusage abgelehnt, und die Fehlerhandlerfunktion wird ausgeführt.  
  
```javascript  
function timeout(duration) {  
    return new Promise(function(resolve, reject) {  
        setTimeout(reject, duration);  
    });  
}  
  
var p = timeout(5000).then(() => {  
    console.log("done!");  
}).catch(err => {  
    console.log("error!");  
})  
  
// Output (after five seconds):  
// error!  
```  
  
## Anforderungen  
 [!INCLUDE[jsv12](../../includes/jsv12-md.md)]