---
title: Object.isFrozen-Funktion (JavaScript) | Microsoft Docs
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
- isFrozen function [JavaScript]
- Object.isFrozen function [JavaScript]
ms.assetid: 6cf1bbc6-56e8-429b-8e2c-0024fa614acc
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3e1ccd11d5b4ef3b5f24dbfc8e815f0e3e156347
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="objectisfrozen-function-javascript"></a>Object.isFrozen-Funktion (JavaScript)
Gibt `true` Wenn vorhandenen Eigenschaftenattributen und-Werten können nicht in ein Objekt geändert werden, und neue Eigenschaften nicht auf das Objekt hinzugefügt werden.  
  
## <a name="syntax"></a>Syntax  
  
```JavaScript  
Object.isFrozen(object)  
```  
  
#### <a name="parameters"></a>Parameter  
 `object`  
 Erforderlich. Das zu überprüfende Objekt.  
  
## <a name="return-value"></a>Rückgabewert  
 `true`Wenn alle der folgenden erfüllt sind:  
  
-   Das Objekt ist nicht erweiterbar und gibt an, dass das Objekt neue Eigenschaften hinzugefügt werden können.  
  
-   Die `configurable` -Attribut ist `false` für alle vorhandenen Eigenschaften.  
  
-   Die `writable` -Attribut ist `false` für alle vorhandenen Dateneigenschaften.  
  
 Wenn das Objekt keine vorhandenen Eigenschaften aufweist, gibt die Funktion `true` , wenn das Objekt nicht erweiterbar ist.  
  
## <a name="exceptions"></a>Ausnahmen  
 Wenn die `object` Argument ist ein Objekt, das eine `TypeError` Ausnahme wird ausgelöst.  
  
## <a name="remarks"></a>Hinweise  
 Wenn die `configurable` Attribut einer Eigenschaft ist `false`, die Eigenschaftenattribute können nicht geändert werden, und die Eigenschaft kann nicht gelöscht werden. Wenn `writable` ist `false`, der Daten-Eigenschaftswert kann nicht geändert werden. Wenn `configurable` ist `false` und `writable` ist `true`, `value` und `writable` Attribute geändert werden können.  
  
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
|[Object.isExtensible](../../javascript/reference/object-isextensible-function-javascript.md)|Ja|Nein|Nein|  
|[Object.isSealed](../../javascript/reference/object-issealed-function-javascript.md)|Nein|Ja|Nein|  
|`Object.isFrozen`|Nein|Ja|Ja|  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel veranschaulicht die Verwendung der `Object.isFrozen`-Funktion.  
  
```JavaScript  
// Create an object that has two properties.  
var obj = { pasta: "spaghetti", length: 10 };  
  
// Freeze the object, and verify that it is frozen.  
Object.freeze(obj);  
document.write(obj.isFrozen());  
  
// Try to add a new property, and then verify that it is not added.   
obj.newProp = 50;  
document.write (obj.newProp);  
document.write ("<br/>");  
  
// Try to delete a property, and then verify that it is still present.  
delete obj.length;  
document.write (obj.length);  
document.write ("<br/> ");  
  
// Try to change a property value, and then verify that it is not changed.  
obj.pasta = "linguini";  
document.write (obj.pasta);  
  
// Output:  
// true  
// undefined  
// 10  
// spaghetti  
  
```  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## <a name="see-also"></a>Siehe auch  
 [Object.preventExtensions-Funktion](../../javascript/reference/object-preventextensions-function-javascript.md)   
 [Object.Seal-Funktion](../../javascript/reference/object-seal-function-javascript.md)   
 [Object.Freeze-Funktion](../../javascript/reference/object-freeze-function-javascript.md)   
 [Object.isExtensible-Funktion](../../javascript/reference/object-isextensible-function-javascript.md)   
 [Object.isSealed-Funktion](../../javascript/reference/object-issealed-function-javascript.md)   
 [Object.defineProperty-Funktion](../../javascript/reference/object-defineproperty-function-javascript.md)   
 [Object.getOwnPropertyDescriptor-Funktion](../../javascript/reference/object-getownpropertydescriptor-function-javascript.md)   
 [Object.getOwnPropertyNames-Funktion](../../javascript/reference/object-getownpropertynames-function-javascript.md)