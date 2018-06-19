---
title: Promise-Objekt (JavaScript) | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 358ad98b-f7fa-448c-9ee0-ef1e2a45e9c6
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 61e5611dd0d455c7e7b704777cc2341ca43a2404
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
ms.locfileid: "24640630"
---
# <a name="promise-object-javascript"></a>Promise-Objekt (JavaScript)
Bietet einen Mechanismus zum Planen von Arbeit, die für einen noch nicht berechneten Wert auszuführen ist. Dies ist eine Abstraktion für das Verwalten von Interaktionen mit asynchronen APIs.  
  
## <a name="syntax"></a>Syntax  
  
```  
var promise = new Promise(function(resolve, reject) { ... });  
```  
  
#### <a name="parameters"></a>Parameter  
 `promise`  
 Erforderlich. Der Variablenname, dem die Zusage zugewiesen wird.  
  
 `resolve`  
 Erforderlich. Eine Funktion, die ausgeführt wird, um anzugeben, dass die Zusage erfolgreich abgeschlossen wurde.  
  
 `reject`  
 Dies ist optional. Eine Funktion, die ausgeführt wird, um anzugeben, dass die Zusage mit einem Fehler abgelehnt wurde.  
  
## <a name="remarks"></a>Hinweise  
 Eine Zusage muss entweder mit einem Wert abgeschlossen werden, oder sie muss mit einem Grund abgelehnt werden. Die `then`-Methode des Promise-Objekts wird ausgeführt, wenn die Zusage abgeschlossen oder abgelehnt wird, je nachdem, welches Ereignis zuerst eintritt. Wenn die Zusage erfolgreich abgeschlossen wird, wird die Erfüllungshandlerfunktion der `then`-Methode ausgeführt. Wenn die Zusage abgelehnt wird, wird die Fehlerhandlerfunktion der `then`-Methode (oder der `catch`-Methode) ausgeführt.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird das Aufrufen einer Funktion (`timeout`) gezeigt, die eine Zusage zurückgibt. Der Erfüllungshandler der `then`-Methode wird ausgeführt, nachdem das Zeitlimit von 5000 ms abgelaufen ist.  
  
```JavaScript  
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
  
## <a name="example"></a>Beispiel  
 Sie können Aufrufe an die `then`-Methode auch wie im folgenden Code gezeigt verketten. Jeder Vervollständigungshandler muss selbst eine Zusage zurückgeben, die Verkettung zu unterstützen. In diesem Code, durch den dieselbe `timeout`-Funktion aufgerufen wird, wird der erste Aufruf des Timeouts nach 1000 ms zurückgegeben. Der erste Vervollständigungshandler ruft `timeout` erneut auf, und diese Zusage wird nach 2000 ms zurückgegeben. Der Vervollständigungshandler löst dann einen Fehler aus. Der Fehlerhandler ruft `Promise.all` auf, was nur zurückgegeben wird, wenn beide Aufrufe von Timeouts abgeschlossen sind oder abgelehnt wurden.  
  
```JavaScript  
var p = timeout(1000).then(() => {  
    return timeout(2000);  
}).then(() => {  
    throw new Error("error");  
}).catch(err => {  
    return Promise.all([timeout(100), timeout(200)]);  
})  
```  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]  
  
## <a name="functions"></a>Funktionen  
 In der folgenden Tabelle werden die Funktionen des `Promise`-Objekts beschrieben.  
  
|Funktion|Beschreibung|  
|--------------|-----------------|  
|[Promise.All-Funktion](../../javascript/reference/promise-all-function-promise.md)|Verknüpft zwei oder mehr Zusagen und wird nur zurückgegeben, wenn alle angegebenen Zusagen abgeschlossen oder abgelehnt wurden.|  
|[Promise.Race-Funktion](../../javascript/reference/promise-race-function-promise.md)|Erstellt eine neue Zusage, die mit dem gleichen Ergebniswert wie die erste Zusage, die unter den übergebenen Argumenten aufzulösen oder abzulehnen war, aufgelöst oder abgelehnt wird.|  
|[Promise.Reject-Funktion](../../javascript/reference/promise-reject-function-promise.md)|Erstellt ein neues abgelehntes Versprechen mit einem Ergebnis, das dem übergebenen Argument entspricht.|  
|[Promise.Resolve-Funktion](../../javascript/reference/promise-resolve-function-promise.md)|Erstellt eine neue aufgelöste Zusage mit einem Ergebnis, das seinem Argument entspricht.|  
  
## <a name="methods"></a>Methoden  
 In der folgenden Tabelle werden die Methoden des `Promise`-Objekts beschrieben.  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[Catch-Methode](../../javascript/reference/catch-method-promise.md)|Ermöglicht Ihnen das Angeben des Verfahrens, das bei Ablehnung einer Zusage durchzuführen ist.|  
|[Then-Methode](../../javascript/reference/then-method-promise.md)|Ermöglicht Ihnen das Angeben des Verfahrens, das bei Erfüllung einer Zusage durchzuführen ist.|