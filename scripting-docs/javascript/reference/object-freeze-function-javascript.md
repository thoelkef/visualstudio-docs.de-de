---
title: Object.Freeze-Funktion (JavaScript) | Microsoft Docs
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
- Object.freeze function
- freeze function
ms.assetid: 83ffe193-0a37-4e0c-9b66-44c422765fb3
caps.latest.revision: "20"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ec08b34c3c8b32245928e6e75f5df1fbdfe2d4a6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="objectfreeze-function-javascript"></a>Object.freeze-Funktion (JavaScript)
Verhindert die Änderung von vorhandenen Eigenschaftenattributen und -werten und verhindert die Einführung von neuen Eigenschaften.  
  
## <a name="syntax"></a>Syntax  
  
```JavaScript  
Object.freeze(object)  
```  
  
#### <a name="parameters"></a>Parameter  
 `object`  
 Erforderlich. Das Objekt auf dem die Attribute zu sperren.  
  
## <a name="return-value"></a>Rückgabewert  
 Das Objekt, das an die Funktion übergeben wird.  
  
## <a name="exceptions"></a>Ausnahmen  
 Wenn die `object` Argument ist ein Objekt, das eine `TypeError` Ausnahme wird ausgelöst.  
  
## <a name="remarks"></a>Hinweise  
 Die `Object.freeze` Funktion bewirkt Folgendes:  
  
-   Wird das Objekt nicht erweiterbar, sodass neue Eigenschaften hinzugefügt werden können nicht.  
  
-   Legt die `configurable` -Attribut `false` für alle Eigenschaften des Objekts. Wenn `configurable` ist `false`, die Eigenschaftenattribute können nicht geändert werden, und die Eigenschaft kann nicht gelöscht werden.  
  
-   Legt die `writable` -Attribut `false` für alle Data-Eigenschaften des Objekts. Wenn `writable` lautet "false", der Daten-Eigenschaftswert kann nicht geändert werden.  
  
 Weitere Informationen zum Festlegen von Eigenschaftenattribute finden Sie unter [Object.defineProperty-Funktion](../../javascript/reference/object-defineproperty-function-javascript.md). Um die Attribute einer Eigenschaft zu erhalten, können Sie die [Object.getOwnPropertyDescriptor-Funktion](../../javascript/reference/object-getownpropertydescriptor-function-javascript.md).  
  
## <a name="related-functions"></a>Verwandte Funktionen  
 Die folgenden verwandten Funktionen zu verhindern, dass die Änderung von Objektattributen.  
  
|Funktion|Objekt ist nicht erweiterbar gemacht.|`configurable`wird festgelegt, um `false` für jede Eigenschaft|`writable`wird festgelegt, um `false` für jede Eigenschaft|  
|--------------|------------------------------------|--------------------------------------------------------|----------------------------------------------------|  
|[Object.preventExtensions](../../javascript/reference/object-preventextensions-function-javascript.md)|Ja|Nein|Nein|  
|[Object.Seal](../../javascript/reference/object-seal-function-javascript.md)|Ja|Ja|Nein|  
|`Object.freeze`|Ja|Ja|Ja|  
  
 Die folgenden Funktionen zurückgeben `true` Wenn alle Bedingungen in der folgenden Tabelle markiert erfüllt sind.  
  
|Funktion|Objekt ist erweiterbar?|`configurable`ist `false` für alle Eigenschaften?|`writable`ist `false` für alle Dateneigenschaften?|  
|--------------|---------------------------|---------------------------------------------------|----------------------------------------------------|  
|[Object.isExtensible](../../javascript/reference/object-isextensible-function-javascript.md)|Ja|Nein|Nein|  
|[Object.isSealed](../../javascript/reference/object-issealed-function-javascript.md)|Nein|Ja|Ja|  
|[Object.isFrozen](../../javascript/reference/object-isfrozen-function-javascript.md)|Nein|Ja|Ja|  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel veranschaulicht die Verwendung der `Object.freeze`-Funktion.  
  
```JavaScript  
// Create an object that has two properties.  
var obj = { pasta: "spaghetti", length: 10 };  
  
// Freeze the object.  
Object.freeze(obj);  
  
// Try to add a new property, and then verify that it is not added.   
    obj.newProp = 50;  
    document.write(obj.newProp);  
    document.write("<br/>");  
  
// Try to delete a property, and then verify that it is still present.   
delete obj.length;  
document.write(obj.length);  
document.write("<br/>");  
  
// Try to change a property value, and then verify that it is not changed.   
obj.pasta = "linguini";  
document.write(obj.pasta);  
  
// Output:  
// undefined  
// 10  
// spaghetti  
  
```  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## <a name="see-also"></a>Siehe auch  
 [Object.preventExtensions-Funktion](../../javascript/reference/object-preventextensions-function-javascript.md)   
 [Object.Seal-Funktion](../../javascript/reference/object-seal-function-javascript.md)   
 [Object.isExtensible-Funktion](../../javascript/reference/object-isextensible-function-javascript.md)   
 [Object.isSealed-Funktion](../../javascript/reference/object-issealed-function-javascript.md)   
 [Object.isFrozen-Funktion](../../javascript/reference/object-isfrozen-function-javascript.md)