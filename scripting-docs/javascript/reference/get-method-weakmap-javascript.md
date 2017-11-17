---
title: Get-Methode (WeakMap) (JavaScript) | Microsoft Docs
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
ms.assetid: d922c55d-486d-4feb-aedc-1f4867c417d2
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 29decb7e6a050188b75639eb7cf4f27494b31da2
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="get-method-weakmap-javascript"></a>get-Methode (WeakMap) (JavaScript)
Gibt ein angegebenes Element aus einem `WeakMap`-Objekt zurück.  
  
## <a name="syntax"></a>Syntax  
  
```JavaScript  
weakmapObj.get(key)  
```  
  
#### <a name="parameters"></a>Parameter  
 `weakmapObj`  
 Erforderlich. Ein `WeakMap`-Objekt.  
  
 `key`  
 Erforderlich. Der Schlüssel eines Elements in der `WeakMap`.  
  
## <a name="property-valuereturn-value"></a>Eigenschaftswert/Rückgabewert  
 Gibt das Objekt zurück, das dem Schlüssel zugeordnet ist. Wenn die `WeakMap` den Schlüssel nicht enthält, gibt diese Methode einen `undefined`-Wert zurück.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird veranschaulicht, wie Member aus einem `WeakMap`-Objekt abgerufen werden.  
  
```JavaScript  
var dog = {  
    breed: "yorkie"  
}  
  
var cat = {  
    breed: "burmese"  
}  
  
var wm = new WeakMap();  
wm.set(dog, "fido");  
wm.set(cat, "pepper");  
  
document.write(wm.get(dog) + ": ");  
document.write(dog.breed);  
document.write("<br />");  
document.write(wm.get(cat) + ": ");  
document.write(cat.breed);  
  
// Output:  
// fido: yorkie  
// pepper: burmese  
  
```  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]