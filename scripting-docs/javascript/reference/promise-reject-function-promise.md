---
title: Promise.Reject-Funktion (Promise) | Microsoft Docs
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
ms.assetid: 9746e15b-9717-4e36-bf6b-910dcc6cd667
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0711bdd8a478d4ea07ee40ea6822af3c8c4ac610
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="promisereject-function-promise"></a>Promise.reject-Funktion (Promise)
Erstellt ein neues abgelehntes Versprechen mit einem Ergebnis, das dem übergebenen Argument entspricht.  
  
## <a name="syntax"></a>Syntax  
  
```  
Promise.reject(r);  
```  
  
#### <a name="parameters"></a>Parameter  
 `r`  
 Erforderlich. Der Grund, warum das Versprechen abgelehnt wurde.  
  
## <a name="remarks"></a>Hinweise  
 Die Fehlerbehandlungsfunktion der `then`- oder `catch`-Methode wird ausgeführt, wenn das abgelehnte Versprechen zurückgegeben wird.  
  
## <a name="example"></a>Beispiel  
  
```JavaScript  
var p = Promise.reject('failure');  
p.catch(function(result) {  
    console.log(result);  
});  
  
// Output:  
// failure  
```  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]  
  
## <a name="see-also"></a>Siehe auch  
 [Promise-Objekt](../../javascript/reference/promise-object-javascript.md)