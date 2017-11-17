---
title: Object.isExtensible-Funktion (JavaScript) | Microsoft Docs
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
helpviewer_keywords:
- Object.isExtensible function [JavaScript]
- isExtensible function [JavaScript]
ms.assetid: a7d10beb-0d01-4e2d-8263-59ff07ac4352
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f88a61917811a5c6b5583e6c30539efc682296df
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="objectisextensible-function-javascript"></a>Object.isExtensible-Funktion (JavaScript)
Gibt einen Wert zurück, der angibt, ob neue Eigenschaften einem Objekt hinzugefügt werden können.  
  
## <a name="syntax"></a>Syntax  
  
```JavaScript  
Object.isExtensible(object)  
```  
  
#### <a name="parameters"></a>Parameter  
 `object`  
 Erforderlich. Das zu überprüfende Objekt.  
  
## <a name="return-value"></a>Rückgabewert  
 `true`Wenn das Objekt erweiterbar ist, der angibt, dass das Objekt neue Eigenschaften hinzugefügt werden können; andernfalls `false`.  
  
## <a name="exceptions"></a>Ausnahmen  
 Wenn die `object` Argument ist ein Objekt, das eine `TypeError` Ausnahme wird ausgelöst.  
  
## <a name="remarks"></a>Hinweise  
 Informationen zur Einrichtung Eigenschaftenattribute finden Sie unter [Object.defineProperty-Funktion](../../javascript/reference/object-defineproperty-function-javascript.md). Um die Attribute einer Eigenschaft zu erhalten, können Sie die [Object.getOwnPropertyDescriptor-Funktion](../../javascript/reference/object-getownpropertydescriptor-function-javascript.md).  
  
## <a name="related-functions"></a>Verwandte Funktionen  
 Die folgenden verwandten Funktionen zu verhindern, dass die Änderung von Objektattributen.  
  
|Funktion|Objekt ist nicht erweiterbar gemacht.|`configurable`wird festgelegt, um `false` für jede Eigenschaft|`writable`wird festgelegt, um `false` für jede Eigenschaft|  
|--------------|------------------------------------|--------------------------------------------------------|----------------------------------------------------|  
|[Object.preventExtensions](../../javascript/reference/object-preventextensions-function-javascript.md)|Ja|Nein|Nein|  
|[Object.Seal](../../javascript/reference/object-seal-function-javascript.md)|Ja|Ja|Nein|  
|[Object.Freeze](../../javascript/reference/object-freeze-function-javascript.md)|Ja|Ja|Ja|  
  
 Die folgenden Funktionen zurückgeben `true` Wenn alle Bedingungen in der folgenden Tabelle markiert erfüllt sind.  
  
|Funktion|Objekt ist erweiterbar?|`configurable`ist `false` für alle Eigenschaften?|`writable`ist `false` für alle Dateneigenschaften?|  
|--------------|---------------------------|---------------------------------------------------|----------------------------------------------------|  
|`Object.isExtensible`|Ja|Nein|Nein|  
|[Object.isSealed](../../javascript/reference/object-issealed-function-javascript.md)|Nein|Ja|Nein|  
|[Object.isFrozen](../../javascript/reference/object-isfrozen-function-javascript.md)|Nein|Ja|Ja|  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel veranschaulicht die Verwendung der `Object.isExtensible`-Funktion.  
  
```JavaScript  
// Create an object that has two properties.  
var obj = { pasta: "spaghetti", length: 10 };  
  
// Make the object non-extensible.  
Object.preventExtensions(obj);  
  
// Try to add a new property, and then verify that it is not added.  
obj.newProp = 50;  
document.write(obj.newProp);  
  
// Output:  
undefined  
  
```  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## <a name="see-also"></a>Siehe auch  
 [Object.preventExtensions-Funktion](../../javascript/reference/object-preventextensions-function-javascript.md)   
 [Object.Seal-Funktion](../../javascript/reference/object-seal-function-javascript.md)   
 [Object.Freeze-Funktion](../../javascript/reference/object-freeze-function-javascript.md)   
 [Object.isSealed-Funktion](../../javascript/reference/object-issealed-function-javascript.md)   
 [Object.isFrozen-Funktion](../../javascript/reference/object-isfrozen-function-javascript.md)