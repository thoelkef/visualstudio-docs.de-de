---
title: Promise.All-Funktion (Promise) | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 02a7b90c-96f6-4484-9466-d261efa1b494
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 997a419a990b407ae018f7da39fd75673ea28b6d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="promiseall-function-promise"></a>Promise.all-Funktion (Promise)
Verknüpft zwei oder mehr Zusagen und wird nur zurückgegeben, wenn alle angegebenen Zusagen abgeschlossen oder abgelehnt wurden.  
  
## <a name="syntax"></a>Syntax  
  
```  
Promise.all(func1, func2 [,funcN])  
```  
  
#### <a name="parameters"></a>Parameter  
 `func1`  
 Erforderlich. Eine Funktion, die eine Zusage zurückgibt.  
  
 `func2`  
 Erforderlich. Eine Funktion, die eine Zusage zurückgibt.  
  
 `funcN`  
 Dies ist optional. Mindestens eine Funktion, die eine Zusage zurückgibt.  
  
## <a name="remarks"></a>Hinweise  
 Das zurückgegebene Ergebnis ist ein Array von Werten, die von den abgeschlossenen Zusagen zurückgegeben werden. Wenn eine der verknüpften Zusagen abgelehnt wird, kehrt `Promise.all` unmittelbar mit dem Grund für die Ablehnung der Zusage zurück (alle anderen Werte werden verworfen).  
  
## <a name="example"></a>Beispiel  
 In diesem Code wird der erste ablaufende Aufruf nach 5000 ms zurückgegeben. Der Abschlusshandler ruft `Promise.all` auf, die nur zurückkehrt, wenn beide ablaufenden Aufrufe abgeschlossen sind oder abgelehnt wurden.  
  
```JavaScript  
function timeout(duration) {  
    return new Promise(function(resolve, reject) {  
        setTimeout(resolve, duration);  
    });  
}  
  
var p = timeout(5000).then(() => {  
    return Promise.all([timeout(100), timeout(200)]);  
})  
```  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]  
  
## <a name="see-also"></a>Siehe auch  
 [Promise-Objekt](../../javascript/reference/promise-object-javascript.md)