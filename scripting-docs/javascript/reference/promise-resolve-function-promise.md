---
title: Promise.Resolve-Funktion (Promise) | Microsoft Docs
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
ms.assetid: 0fb6bff9-54ab-41be-97d7-04f7e6fe9cff
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6d815c9c23da48c877f7f1d995df8991429375e1
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="promiseresolve-function-promise"></a>Promise.resolve-Funktion (Promise)
Erstellt eine neue aufgelöste Zusage mit einem Ergebnis, das seinem Argument entspricht.  
  
## <a name="syntax"></a>Syntax  
  
```  
Promise.resolve(x)  
```  
  
#### <a name="parameters"></a>Parameter  
 `x`  
 Erforderlich. Der mit der abgeschlossenen Zusage zurückgegebene Wert.  
  
## <a name="remarks"></a>Hinweise  
 Die Funktion zur Behandlung der Erfüllung der `then`-Methode wird ausgeführt, wenn das abgeschlossene Promise-Objekt zurückgegeben wird.  
  
## <a name="example"></a>Beispiel  
  
```JavaScript  
var p = Promise.resolve('success');  
p.then(function(result) {  
    console.log(result);  
});  
  
// Output:  
// success  
```  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]  
  
## <a name="see-also"></a>Siehe auch  
 [Promise-Objekt](../../javascript/reference/promise-object-javascript.md)