---
title: "Promise.race-Funktion (Promise) | Microsoft Docs"
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
ms.assetid: 9236eced-d313-4d03-8c3e-d89d762b3084
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# Promise.race-Funktion (Promise)
Erstellt eine neue Zusage, die mit dem gleichen Ergebniswert wie die erste Zusage, die unter den übergebenen Argumenten aufzulösen oder abzulehnen war, aufgelöst oder abgelehnt wird.  
  
## Syntax  
  
```  
Promise.race(iterable)  
  
```  
  
#### Parameter  
 `iterable`  
 Erforderlich.  Eine oder mehrere Zusagen.  
  
## Hinweise  
 Wenn sich eine der Zusagen in `iterable` bereits in einem gelösten oder abgelehnten Zustand befindet, gibt `Promise.race` eine aufgelöste oder zurückgewiesene Zusage auf die gleiche Weise mit dem Ergebniswert zurück, der dem Wert zum Auflösen \(oder Ablehnen\) der Zusage entspricht.  Wenn mehrere Zusagen in `iterable` bereits aufgelöst oder abgelehnt wurden, gibt `Promise.race` eine aufgelöste Zusage auf die gleiche Weise wie die erste durchlaufene Zusage zurück.  Wenn in iterable keine Zusage ausfelöst oder abgelehnt wird, wird die von `Promise.race` zurückgegebene Zusage ebenfalls nicht aufgelöst oder abgelehnt.  
  
## Beispiel  
  
```javascript  
var p1 = new Promise(function(resolve, reject) {  
    setTimeout(resolve, 0, 'success');  
});  
var p2 = new Promise(function(resolve, reject) { });  
var p2 = new Promise(function(resolve, reject) { });  
  
var race = Promise.race( [p1, p2, p3] );  
race.then(function(result) {  
    console.log(result);  
});  
  
// Output:  
// success  
  
var race = Promise.race( [Promise.reject('failure'),  
    Promise.resolve('success')] );  
race.catch(function(result) {  
    console.log(result);  
});  
  
// Output:  
// failure  
  
```  
  
## Anforderungen  
 [!INCLUDE[jsv12](../../includes/jsv12-md.md)]  
  
## Siehe auch  
 [Promise\-Objekt](../../javascript/reference/promise-object-javascript.md)