---
title: Set-Methode (WeakMap) (JavaScript) | Microsoft Docs
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
ms.assetid: 29fc72b1-224f-4f19-8c06-5d926d695b03
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c916bda13c7bd973b37c4e4cb6b81e327ee5de54
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
ms.locfileid: "24639600"
---
# <a name="set-method-weakmap-javascript"></a>set-Methode (WeakMap) (JavaScript)
Fügt einem `WeakMap`-Objekt ein neues Element hinzu.  
  
## <a name="syntax"></a>Syntax  
  
```JavaScript  
weakmapObj.set(key, value)  
```  
  
#### <a name="parameters"></a>Parameter  
 `weakmapObj`  
 Erforderlich. Ein `WeakMap`-Objekt.  
  
 `key`  
 Erforderlich. Ein Objekt, das den Schlüssel des hinzuzufügenden Elements darstellt. Dies muss ein Objektverweis sein.  
  
 `value`  
 Erforderlich. Der Wert des hinzuzufügenden Elements.  
  
## <a name="property-valuereturn-value"></a>Eigenschaftswert/Rückgabewert  
 Gibt das `WeakMap`-Objekt zurück, das das neue Schlüssel-Wert-Paar enthält.  
  
## <a name="remarks"></a>Hinweise  
 Wenn Sie einen Wert mithilfe eines vorhandenen Schlüssels zur Auflistung hinzufügen, ersetzt der neue Wert den alten Wert.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird veranschaulicht, wie einem `WeakMap`-Objekt Member hinzugefügt werden.  
  
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
```  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]