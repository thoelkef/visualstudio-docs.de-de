---
title: "Promise.all-Funktion (Promise) | Microsoft Docs"
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
ms.assetid: 02a7b90c-96f6-4484-9466-d261efa1b494
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# Promise.all-Funktion (Promise)
Verknüpft zwei oder mehr Zusagen und kehrt nur zurück, wenn alle angegebenen Zusagen abgeschlossen oder abgelehnt wurden.  
  
## Syntax  
  
```  
Promise.all(func1, func2 [,funcN])  
```  
  
#### Parameter  
 `func1`  
 Erforderlich.  Eine Funktion, die eine Zusage zurückgibt.  
  
 `func2`  
 Erforderlich.  Eine Funktion, die eine Zusage zurückgibt.  
  
 `funcN`  
 Optional.  Mindestens eine Funktion, die eine Zusage zurückgibt.  
  
## Hinweise  
 Das zurückgegebene Ergebnis ist ein Array von Werten, die von den abgeschlossenen Zusagen zurückgegeben werden.  Wenn eine der verknüpften Zusagen abgelehnt wird, kehrt `Promise.all` unmittelbar mit dem Grund für die Ablehnung der Zusage zurück \(alle anderen Werte werden verworfen\).  
  
## Beispiel  
 In diesem Code wird der erste ablaufende Aufruf nach 5000 ms zurückgegeben.  Der Abschlusshandler ruft `Promise.all` auf, die nur zurückkehrt, wenn beide ablaufenden Aufrufe abgeschlossen sind oder abgelehnt wurden.  
  
```javascript  
function timeout(duration) {  
    return new Promise(function(resolve, reject) {  
        setTimeout(resolve, duration);  
    });  
}  
  
var p = timeout(5000).then(() => {  
    return Promise.all([timeout(100), timeout(200)]);  
})  
```  
  
## Anforderungen  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]  
  
## Siehe auch  
 [Promise\-Objekt](../../javascript/reference/promise-object-javascript.md)