---
title: Object.getOwnPropertyNames-Funktion (JavaScript) | Microsoft Docs
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
- getOwnPropertyNames method [JavaScript]
- Object.getOwnPropertyNames method [JavaScript]
ms.assetid: 59f4b6b1-02be-44b3-a06c-a5ca8f70c3d8
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 76ca0036b9dedf7b4cee7b543469939e35dfe8d1
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
ms.locfileid: "24639930"
---
# <a name="objectgetownpropertynames-function-javascript"></a>Object.getOwnPropertyNames-Funktion (JavaScript)
Gibt den Namen der eigenen Eigenschaften eines Objekts zurück. Die eigenen Eigenschaften eines Objekts sind diejenigen, die direkt für dieses Objekt definiert sind, und nicht vom Prototyp des Objekts geerbt werden. Die Eigenschaften eines Objekts enthalten Felder (Objekte) und Funktionen.  
  
## <a name="syntax"></a>Syntax  
  
```JavaScript  
Object.getOwnPropertyNames(object)  
```  
  
#### <a name="parameters"></a>Parameter  
  
|Parameter|Definition|  
|---------------|----------------|  
|`object`|Erforderlich. Das Objekt, das die eigenen Eigenschaften enthält.|  
  
## <a name="return-value"></a>Rückgabewert  
 Ein Array, das die Namen der eigenen Eigenschaften des Objekts enthält.  
  
## <a name="exceptions"></a>Ausnahmen  
 Wenn der Wert für die angegebene der `object` Argument ist nicht der Name eines Objekts ein `TypeError` Ausnahme wird ausgelöst.  
  
## <a name="remarks"></a>Hinweise  
 Die `getOwnPropertyNames` Methode gibt die Namen von enumerable-Typs und nicht aufzählbare Eigenschaften und Methoden zurück. Damit nur die Namen der aufzählbaren Eigenschaften und Methoden zurückgegeben werden, können Sie die [Object.keys-Funktion](../../javascript/reference/object-keys-function-javascript.md).  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel erstellt ein Objekt, das drei Eigenschaften und eine Methode verfügt. Es verwendet dann die `getOwnPropertyNames` Methode, um die eigenen Eigenschaften (einschließlich der Methode) des Objekts abzurufen.  
  
```JavaScript  
function Pasta(grain, width, shape) {  
    // Define properties.  
    this.grain = grain;  
    this.width = width;  
    this.shape = shape;  
    this.toString = function () {  
        return (this.grain + ", " + this.width + ", " + this.shape);  
    }  
}  
  
// Create an object.  
var spaghetti = new Pasta("wheat", 0.2, "circle");  
  
// Get the own property names.  
var arr = Object.getOwnPropertyNames(spaghetti);  
document.write (arr);  
  
// Output:  
//   grain,width,shape,toString  
```  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel zeigt die Namen von Eigenschaften, die mit dem Buchstaben beginnen "in einem **Spaghetti** Objekt erstellt, mit der **Nudeln** Konstruktor.  
  
```JavaScript  
function Pasta(grain, size, shape) {  
    this.grain = grain;   
    this.size = size;   
    this.shape = shape;   
}  
  
var spaghetti = new Pasta("wheat", 2, "circle");  
  
var names = Object.getOwnPropertyNames(spaghetti).filter(CheckKey);  
document.write(names);   
  
// Check whether the first character of a string is 's'.   
function CheckKey(value) {  
    var firstChar = value.substr(0, 1);   
    if (firstChar.toLowerCase() == 's')  
        return true;   
    else  
         return false;   
}  
// Output:  
// size,shape  
```  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## <a name="see-also"></a>Siehe auch  
 [Object.keys-Funktion](../../javascript/reference/object-keys-function-javascript.md)