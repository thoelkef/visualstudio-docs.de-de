---
title: has-Methode (WeakMap) (JavaScript) | Microsoft Docs
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
ms.assetid: 12bedca1-bde7-413a-a4e2-06c03559044f
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e9a1706a1b96b5273ec280c4cef2be47a3bc6e17
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="has-method-weakmap-javascript"></a>has-Methode (WeakMap) (JavaScript)
Gibt `true` zurück, wenn das `WeakMap`-Objekt das angegebene Element enthält.  
  
## <a name="syntax"></a>Syntax  
  
```JavaScript  
weakmapObj.has(key)  
```  
  
#### <a name="parameters"></a>Parameter  
 `weakmapObj`  
 Erforderlich. Ein `WeakMap`-Objekt.  
  
 `key`  
 Erforderlich. Der Schlüssel des zu testenden Elements.  
  
## <a name="property-valuereturn-value"></a>Eigenschaftswert/Rückgabewert  
 `true`, wenn `WeakMap` den angegebenen Schlüssel enthält.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird gezeigt, wie Sie einer `WeakMap` ein Member hinzufügen und dann mit `has` prüfen, ob es vorhanden ist.  
  
```JavaScript  
var dog = {  
    breed: "yorkie"  
}  
  
var wm = new WeakMap();  
wm.set(dog, "fido");  
  
document.write(wm.has(dog));  
  
// Output:  
// true  
```  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]