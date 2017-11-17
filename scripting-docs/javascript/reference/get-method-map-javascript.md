---
title: Get-Methode (Map) (JavaScript) | Microsoft Docs
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
ms.assetid: bebbd6bc-6e61-4674-8196-7e907798973f
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 243d5aa93289cb7a13b34567b7824d028151bad3
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="get-method-map-javascript"></a>get-Methode (Map) (JavaScript)
Gibt ein angegebenes Element aus einer Zuordnung zurück.  
  
## <a name="syntax"></a>Syntax  
  
```JavaScript  
mapObj.get(key)  
```  
  
#### <a name="parameters"></a>Parameter  
 `mapObj`  
 Erforderlich. Ein `Map`-Objekt.  
  
 `key`  
 Erforderlich. Der Schlüssel eines Elements in der `Map`.  
  
## <a name="property-valuereturn-value"></a>Eigenschaftswert/Rückgabewert  
 Gibt das Objekt zurück, das dem Schlüssel zugeordnet ist. Wenn die `Map` den Schlüssel nicht enthält, gibt diese Methode einen `undefined`-Wert zurück.  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel zeigt, wie ein Element aus einem `Map`-Objekt abgerufen wird.  
  
```JavaScript  
var m = new Map();  
m.set(1, "black");  
m.set(2, "red");  
m.set("colors", 2);  
  
document.write(m.get(2));  
  
// Output:  
// red  
  
```  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]