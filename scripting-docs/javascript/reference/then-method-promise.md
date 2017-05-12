---
title: "then-Methode (Promise) | Microsoft Docs"
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
ms.assetid: c7f3259d-78f7-4ca7-8bdf-99fbd3f41e8d
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# then-Methode (Promise)
Ermöglicht Ihnen das Angeben des Verfahrens, das bei Erfüllung einer Zusage durchzuführen ist.  
  
## Syntax  
  
```  
  
promise.then(onCompleted, onRejected);  
```  
  
#### Parameter  
 `promise`  
 Erforderlich.  Das Promise\-Objekt.  
  
 `onCompleted`  
 Erforderlich.  Die Erfüllungshandlerfunktion, die ausgeführt werden soll, wenn die Zusage erfolgreich abgeschlossen wurde.  
  
 `onRejected`  
 Optional.  Die Fehlerhandlerfunktion, die bei Ablehnung der Zusage auszuführen ist.  
  
## Hinweise  
 Eine Zusage muss entweder mit einem Wert abgeschlossen werden, oder sie muss mit einem Grund abgelehnt werden.  Die `then`\-Methode des Promise\-Objekts wird ausgeführt, wenn die Zusage abgeschlossen oder abgelehnt wird, je nachdem, welches Ereignis zuerst eintritt.  Wenn die Zusage erfolgreich abgeschlossen wird, wird die Erfüllungshandlerfunktion der `then`\-Methode ausgeführt.  Wenn die Zusage abgelehnt wird, wird die Fehlerhandlerfunktion der `then`\-Methode \(oder der `catch`\-Methode\) ausgeführt.  
  
## Beispiel  
 Im folgenden Beispiel wird das Aufrufen einer Funktion \(`timeout`\) gezeigt, die eine Zusage zurückgibt.  Der Erfüllungshandler der `then`\-Methode wird ausgeführt, nachdem das Zeitlimit von 5000 ms abgelaufen ist.  
  
```javascript  
function timeout(duration) {  
    return new Promise(function(resolve, reject) {  
        setTimeout(resolve, duration);  
    });  
}  
  
// Note: This code uses arrow function syntax  
var m = timeout(5000).then(() => {  
    console.log("done!");  
})  
  
// Output (after 5 seconds):  
// done!  
```  
  
## Anforderungen  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]  
  
## Siehe auch  
 [Promise\-Objekt](../../javascript/reference/promise-object-javascript.md)