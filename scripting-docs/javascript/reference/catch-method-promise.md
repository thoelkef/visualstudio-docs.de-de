---
title: Catch-Methode (Promise) | Microsoft Docs
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
ms.assetid: 55266f6a-db4d-4de8-857a-8bc7d35ed4b8
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 307e5b2a501b038542a602df4538523a3fc6eccd
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="catch-method-promise"></a>catch-Methode (Promise)
Ermöglicht Ihnen das Angeben des Verfahrens, das bei Ablehnung einer Zusage durchzuführen ist.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
promise.catch(onRejected)  
```  
  
#### <a name="parameters"></a>Parameter  
 `promise`  
 Erforderlich. Das Promise-Objekt.  
  
 `onRejected`  
 Erforderlich. Die Fehlerhandlerfunktion, die bei Ablehnung einer Zusage auszuführen ist.  
  
## <a name="remarks"></a>Hinweise  
  
## <a name="example"></a>Beispiel  
 In diesem Code wird der erste Aufruf des Timeouts nach 5000 ms zurückgegeben. In diesem Code wird die Zusage abgelehnt, und die Fehlerhandlerfunktion wird ausgeführt.  
  
```JavaScript  
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
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]