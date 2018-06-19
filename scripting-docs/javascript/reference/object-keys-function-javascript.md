---
title: Object.Keys-Funktion (JavaScript) | Microsoft Docs
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
- Object.keys method [JavaScript]
- keys method [JavaScript]
ms.assetid: cf4a7daf-cf28-4467-bc6b-f7f106ec3876
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0e725c3ab7206b04d9a900cb614b57c37dfc4351
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
ms.locfileid: "24639750"
---
# <a name="objectkeys-function-javascript"></a>Object.keys-Funktion (JavaScript)
Gibt die Namen der aufzählbaren Eigenschaften und Methoden eines Objekts zurück.  
  
## <a name="syntax"></a>Syntax  
  
```JavaScript  
Object.keys(object)  
```  
  
#### <a name="parameters"></a>Parameter  
  
|Parameter|Definition|  
|---------------|----------------|  
|`object`|Erforderlich. Das Objekt, das die Eigenschaften und Methoden enthält. Dies kann ein Objekt, das Sie erstellt haben oder ein vorhandenes (DOKUMENTOBJEKTMODELL)-Objekt sein.|  
  
## <a name="return-value"></a>Rückgabewert  
 Ein Array, das die Namen der aufzählbaren Eigenschaften und Methoden des Objekts enthält.  
  
## <a name="exceptions"></a>Ausnahmen  
 Wenn der Wert für die angegebene der `object` Argument ist nicht der Name eines Objekts ein `TypeError` Ausnahme wird ausgelöst.  
  
## <a name="remarks"></a>Hinweise  
 Die `keys` -Methode gibt nur die Namen der aufzählbaren Eigenschaften und Methoden zurück. Damit die Namen der enumerable-Typs und nicht aufzählbare Eigenschaften und Methoden zurückgegeben werden, können Sie [Object.getOwnPropertyNames-Funktion](../../javascript/reference/object-getownpropertynames-function-javascript.md).  
  
 Informationen zu den `enumerable` Attribut einer Eigenschaft finden Sie unter [Object.defineProperty-Funktion](../../javascript/reference/object-defineproperty-function-javascript.md) und [Object.getOwnPropertyDescriptor-Funktion](../../javascript/reference/object-getownpropertydescriptor-function-javascript.md).  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel erstellt ein Objekt, das drei Eigenschaften und eine Methode verfügt. Es verwendet dann die `keys` Methode, um die Eigenschaften und Methoden des Objekts abzurufen.  
  
```JavaScript  
// Create a constructor function.  
function Pasta(grain, width, shape) {  
    this.grain = grain;  
    this.width = width;  
    this.shape = shape;  
  
    // Define a method.  
    this.toString = function () {  
        return (this.grain + ", " + this.width + ", " + this.shape);  
    }  
}  
  
// Create an object.  
var spaghetti = new Pasta("wheat", 0.2, "circle");  
  
// Put the enumerable properties and methods of the object in an array.  
var arr = Object.keys(spaghetti);  
document.write (arr);  
  
// Output:  
// grain,width,shape,toString  
```  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel zeigt die Namen aller aufzählbare Eigenschaften, die mit dem Buchstaben "g" in dem Objekt Nudeln beginnen.  
  
```JavaScript  
// Create a constructor function.  
function Pasta(grain, width, shape) {  
    this.grain = grain;  
    this.width = width;  
    this.shape = shape;  
}  
  
var polenta = new Pasta("corn", 1, "mush");  
  
var keys = Object.keys(polenta).filter(CheckKey);  
document.write(keys);  
  
// Check whether the first character of a string is "g".  
function CheckKey(value) {  
    var firstChar = value.substr(0, 1);  
    if (firstChar.toLowerCase() == "g")  
        return true;  
    else  
        return false;  
}  
  
// Output:  
// grain  
```  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## <a name="see-also"></a>Siehe auch  
 [Object.getOwnPropertyNames-Funktion](../../javascript/reference/object-getownpropertynames-function-javascript.md)