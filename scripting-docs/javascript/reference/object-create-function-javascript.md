---
title: Object.Create-Funktion (JavaScript) | Microsoft Docs
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
- create function [JavaScript]
- Object.create function [JavaScript]
ms.assetid: 0ad31f36-a9ee-444e-b0fe-c87843d03196
caps.latest.revision: "14"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f359908c5c836743e22390580f542df27d7b98e7
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="objectcreate-function-javascript"></a>Object.create-Funktion (JavaScript)
Erstellt ein Objekt, das den angegebenen Prototyp besitzt und das optional die angegebenen Eigenschaften enthält.  
  
## <a name="syntax"></a>Syntax  
  
```  
Object.create(prototype, descriptors)  
```  
  
#### <a name="parameters"></a>Parameter  
 `prototype`  
 Erforderlich. Das als Prototyp zu verwendende Objekt. Kann `null` sein.  
  
 `descriptors`  
 Dies ist optional. Ein [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]-Objekt, das eine oder mehrere Eigenschaftendeskriptoren enthält.  
  
 Eine *Dateneigenschaft* ist eine Eigenschaft, die einen Wert abrufen und festlegen kann. Ein Dateneigenschaftendeskriptor enthält ein `value`-Attribut sowie die Attribute `writable`, `enumerable` und `configurable`. Werden die letzten drei Attribute nicht angegeben, werden sie standardmäßig auf `false` festgelegt. Ein *Accessoreigenschaft* eine vom Benutzer bereitgestellte Funktion aufruft, jedes Mal, wenn der Wert abgerufen oder festgelegt wird. Ein Accessoreigenschaftendeskriptor enthält ein `set`-Attribut, ein `get`-Attribut oder beides. Weitere Informationen finden Sie unter [Object.defineProperty-Funktion](../../javascript/reference/object-defineproperty-function-javascript.md).  
  
## <a name="return-value"></a>Rückgabewert  
 Ein neues Objekt, das den angegebenen internen Prototyp besitzt und die angegebenen Eigenschaften enthält, sofern vorhanden.  
  
## <a name="exceptions"></a>Ausnahmen  
 Eine `TypeError`-Ausnahme wird ausgelöst, wenn eine der folgenden Bedingungen zutrifft:  
  
-   Das `prototype`-Argument ist kein Objekt und nicht `null`.  
  
-   Ein Deskriptor im `descriptors`-Argument verfügt über ein `value`- oder `writable`-Attribut sowie über ein `get`- oder `set`-Attribut.  
  
-   Ein Deskriptor im `descriptors`-Argument verfügt über ein `get`- oder `set`-Attribut, das keine Funktion ist.  
  
## <a name="remarks"></a>Hinweise  
 Sie können diese Funktion mit einer `null``prototype` Parameter zum Beenden der Prototypenkette. Das erstellte Objekt hat keinen Prototyp.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird ein Objekt mit einem `null`-Prototyp erstellt und es werden zwei aufzählbare Eigenschaften hinzugefügt.  
  
```JavaScript  
var newObj = Object.create(null, {  
            size: {  
                value: "large",  
                enumerable: true  
            },  
            shape: {  
                value: "round",  
                enumerable: true  
            }  
        });  
  
document.write(newObj.size + "<br/>");  
document.write(newObj.shape + "<br/>");  
document.write(Object.getPrototypeOf(newObj));  
  
// Output:  
// large  
// round  
// null  
  
```  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird ein Objekt erstellt, das den gleichen internen Prototyp wie das Object-Objekt besitzt. Wie Sie sehen, hat es den gleichen Prototyp wie ein Objekt, das mit einem Objektliteral erstellt wird. Die [Object.getPrototypeOf](../../javascript/reference/object-getprototypeof-function-javascript.md) Funktion ruft den Prototyp des ursprünglichen Objekts ab. Um das Objekt Eigenschaftendeskriptor zu erhalten, können Sie [Object.getOwnPropertyDescriptor-Funktion](../../javascript/reference/object-getownpropertydescriptor-function-javascript.md).  
  
```JavaScript  
var firstLine = { x: undefined, y: undefined };  
  
var secondLine = Object.create(Object.prototype, {  
        x: {  
                value: undefined,   
                writable: true,   
                configurable: true,   
                enumerable: true  
            },  
            y: {  
                value: undefined,   
                writable: true,   
                configurable: true,   
                enumerable: true  
            }  
});  
  
document.write("first line prototype = " + Object.getPrototypeOf(firstLine));  
document.write("<br/>");  
document.write("second line prototype = " + Object.getPrototypeOf(secondLine));  
  
// Output:  
// first line prototype = [object Object]  
// second line prototype = [object Object]  
```  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird ein Objekt erstellt, das den gleichen internen Prototyp wie das Shape-Objekt besitzt.  
  
```JavaScript  
  
// Create the shape object.  
var Shape = { twoDimensional: true, color: undefined, hasLineSegments: undefined };  
  
var Square = Object.create(Object.getPrototypeOf(Shape));  
  
```  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## <a name="see-also"></a>Siehe auch  
 [Object.getPrototypeOf-Funktion](../../javascript/reference/object-getprototypeof-function-javascript.md)   
 [IsPrototypeOf-Methode (Objekt)](../../javascript/reference/isprototypeof-method-object-javascript.md)   
 [Erstellen von Objekten](../../javascript/creating-objects-javascript.md)