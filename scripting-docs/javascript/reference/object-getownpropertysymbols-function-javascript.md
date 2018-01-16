---
title: Object.getOwnPropertySymbols-Funktion (JavaScript) | Microsoft Docs
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
ms.assetid: 68dd69b9-5a33-44c2-ba5f-21a4ae6c0879
caps.latest.revision: "2"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2cc47ae365841332f11cb02da1469a4c9fff80c3
ms.sourcegitcommit: abae48f476832f79cc2c5bac43bb1226d3fe4e48
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/16/2018
---
# <a name="objectgetownpropertysymbols-function-javascript"></a>Object.getOwnPropertySymbols-Funktion (JavaScript)
Gibt die eigenen Symboleigenschaften eines Objekts zurück. Die eigenen Symboleigenschaften eines Objekts sind diejenigen, die direkt für dieses Objekt definiert sind und nicht vom Prototyp des Objekts geerbt werden.  
  
## <a name="syntax"></a>Syntax  
  
```  
Object.getOwnPropertySymbols(object);  
```  
  
#### <a name="parameters"></a>Parameter  
 `object`  
 Erforderlich. Das Objekt, das die eigenen Symbole enthält.  
  
## <a name="return-value"></a>Rückgabewert  
 Ein Array, das die eigenen Symbolen des Objekts enthält.  
  
## <a name="remarks"></a>Hinweise  
 Sie müssen `Object.getOwnPropertySymbols` verwenden, um die Symboleigenschaften eines Objekts abzurufen. `Object.getOwnPropertyNames` gibt die Symboleigenschaften nicht zurück.  
  
## <a name="example"></a>Beispiel  
 Das folgende Codebeispiel zeigt, wie die Symboleigenschaften eines Objekts abgerufen werden.  
  
```JavaScript  
var obj = {};  
var key = Symbol('description');  
  
obj[key] = 'data';  
  
var symbols = Object.getOwnPropertySymbols(obj);  
  
console.log(symbols[0].toString());  
  
// Output:  
// undefined  
// Symbol(description)  
```  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]