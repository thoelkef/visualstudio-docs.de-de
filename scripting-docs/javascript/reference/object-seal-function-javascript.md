---
title: Object.Seal-Funktion (JavaScript) | Microsoft Docs
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
helpviewer_keywords:
- Object.seal function
- seal function
ms.assetid: e72c804a-4dab-4ec9-b9df-9c9c908aa12d
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2dca9066be9a557b97a52ae749cecfb218504509
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
ms.locfileid: "24641150"
---
# <a name="objectseal-function-javascript"></a>Object.seal-Funktion (JavaScript)
Verhindert die Änderung von Attributen vorhandener Eigenschaften und verhindert die Hinzufügung neuer Eigenschaften.  
  
## <a name="syntax"></a>Syntax  
  
```JavaScript  
Object.seal(object)  
```  
  
#### <a name="parameters"></a>Parameter  
 `object`  
 Erforderlich. Das Objekt auf dem die Attribute zu sperren.  
  
## <a name="return-value"></a>Rückgabewert  
 Das Objekt, das an die Funktion übergeben wird.  
  
## <a name="exceptions"></a>Ausnahmen  
 Wenn die `object` Argument ist ein Objekt, das eine `TypeError` Ausnahme wird ausgelöst.  
  
## <a name="remarks"></a>Hinweise  
 Die `Object.seal` Funktion enthält die folgenden beiden:  
  
-   Wird das Objekt nicht erweiterbar, sodass neue Eigenschaften hinzugefügt werden können nicht.  
  
-   Legt die `configurable` -Attribut `false` für alle Eigenschaften des Objekts.  
  
 Wenn die `configurable` -Attribut ist `false`Eigenschaftenattribute können nicht geändert werden, und die Eigenschaft kann nicht gelöscht werden. Wenn `configurable` ist `false` und `writable` ist `true`, `value` und `writable` Attribute geändert werden können.  
  
 Die `Object.seal` Funktion ändert nicht die `writable` Attribut.  
  
 Weitere Informationen zum Festlegen von Eigenschaftenattribute finden Sie unter [Object.defineProperty-Funktion](../../javascript/reference/object-defineproperty-function-javascript.md). Um die Attribute einer Eigenschaft abzurufen, können Sie die [Object.getOwnPropertyDescriptor-Funktion](../../javascript/reference/object-getownpropertydescriptor-function-javascript.md).  
  
## <a name="related-functions"></a>Verwandte Funktionen  
 Die folgenden verwandten Funktionen zu verhindern, dass die Änderung von Objektattributen.  
  
|Funktion|Objekt ist nicht erweiterbar gemacht.|`configurable`wird festgelegt, um `false` für jede Eigenschaft|`writable`wird festgelegt, um `false` für jede Eigenschaft|  
|--------------|------------------------------------|--------------------------------------------------------|----------------------------------------------------|  
|[Object.preventExtensions](../../javascript/reference/object-preventextensions-function-javascript.md)|Ja|Nein|Nein|  
|`Object.seal`|Ja|Ja|Nein|  
|[Object.Freeze](../../javascript/reference/object-freeze-function-javascript.md)|Ja|Ja|Ja|  
  
 Die folgenden Funktionen zurückgeben `true` Wenn alle Bedingungen in der folgenden Tabelle markiert erfüllt sind.  
  
|Funktion|Objekt ist erweiterbar?|`configurable`ist `false` für alle Eigenschaften?|`writable`ist `false` für alle Dateneigenschaften?|  
|--------------|---------------------------|---------------------------------------------------|----------------------------------------------------|  
|[Object.isExtensible](../../javascript/reference/object-isextensible-function-javascript.md)|Ja|Nein|Nein|  
|[Object.isSealed](../../javascript/reference/object-issealed-function-javascript.md)|Nein|Ja|Nein|  
|[Object.isFrozen](../../javascript/reference/object-isfrozen-function-javascript.md)|Nein|Ja|Ja|  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel veranschaulicht die Verwendung der `Object.seal`-Funktion.  
  
```JavaScript  
// Create an object that has two properties.  
var obj = { pasta: "spaghetti", length: 10 };  
// Seal the object.  
Object.seal(obj);  
document.write(Object.isSealed(obj));  
document.write("<br/>");  
  
// Try to add a new property, and then verify that it is not added.   
obj.newProp = 50;  
document.write(obj.newProp);  
document.write("<br/>");  
  
// Try to delete a property, and then verify that it is still present.   
delete obj.length;  
document.write(obj.length);  
  
// Output:  
// true  
// undefined  
// 10  
  
```  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## <a name="see-also"></a>Siehe auch  
 [Object.preventExtensions-Funktion](../../javascript/reference/object-preventextensions-function-javascript.md)   
 [Object.Freeze-Funktion](../../javascript/reference/object-freeze-function-javascript.md)   
 [Object.isExtensible-Funktion](../../javascript/reference/object-isextensible-function-javascript.md)   
 [Object.isSealed-Funktion](../../javascript/reference/object-issealed-function-javascript.md)   
 [Object.isFrozen-Funktion](../../javascript/reference/object-isfrozen-function-javascript.md)