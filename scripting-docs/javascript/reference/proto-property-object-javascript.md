---
title: __Proto__ -Eigenschaft (Objekt) (JavaScript) | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- __proto__
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 97c3f84d-125e-4905-b921-b021264964ee
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f8659c7a4ece5e30378838f20341ec6712f77ca3
ms.sourcegitcommit: e01ccb5ca4504a327d54f33589911f5d8be9c35c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/15/2018
---
# <a name="proto-property-object-javascript"></a>__Proto__ -Eigenschaft (Objekt) (JavaScript)
Enthält einen Verweis auf den internen Prototyp des angegebenen Objekts.  

> [!WARNING]
> Die `__proto__` Eigenschaft ist eine ältere Funktion. Verwendung [Object.getPrototypeOf](../reference/object-getprototypeof-function-javascript.md) stattdessen.
  
## <a name="syntax"></a>Syntax  
  
```  
object.__proto__  
```  
  
#### <a name="parameters"></a>Parameter  
 `object`  
 Erforderlich. Das Objekt, für das der Prototyp festgelegt werden soll.  
  
## <a name="remarks"></a>Hinweise  
 Mit der `__proto__`-Eigenschaft kann der Prototyp für ein Objekt festgelegt werden.  
  
 Das Objekt oder die Funktion erbt alle Methoden und Eigenschaften des neuen Prototyps und alle Methoden und Eigenschaften in der Prototypenkette neuen des Prototyps. Ein Objekt kann nur einen einzigen Prototypen aufweisen (geerbte Prototypen in der Prototypenkette zählen nicht), wenn Sie daher die `__proto__`-Eigenschaft aufrufen, ersetzen Sie den vorherigen Prototypen.  
  
 Sie können den Prototyp nur für ein erweiterbares Objekt festlegen. Weitere Informationen finden Sie unter [Object.preventExtensions-Funktion](../../javascript/reference/object-preventextensions-function-javascript.md).  
  
> [!NOTE]
>  Der `__proto__`-Eigenschaftenname beginnt und endet mit zwei Unterstrichen.  
  
## <a name="example"></a>Beispiel  
 Das folgende Codebeispiel veranschaulicht, wie der Prototyp für ein Objekt festgelegt wird.  
  
```JavaScript  
function Rectangle() {  
}  
  
var rec = new Rectangle();  
  
if (console && console.log) {  
    console.log(rec.__proto__ === Rectangle.prototype);  // Returns true  
    rec.__proto__ = Object.prototype;  
    console.log(rec.__proto__ === Rectangle.prototype);  // Returns false  
}  
```  
  
## <a name="example"></a>Beispiel  
 Im folgenden Codebeispiel wird veranschaulicht, wie Eigenschaften einem Objekt hinzugefügt werden, indem sie dem Prototypen hinzugefügt werden.  
  
```JavaScript  
var proto = { y: 2 };  
  
var obj = { x: 10 };  
obj.__proto__ = proto;  
  
proto.y = 20;  
proto.z = 40;  
  
if (console && console.log) {  
    console.log(obj.x === 10);  // Returns true  
    console.log(obj.y === 20);  // Returns true  
    console.log(obj.z === 40);  // Returns true  
}  
```  
  
## <a name="example"></a>Beispiel  
 Im folgenden Codebeispiel werden dem `String`-Objekt Eigenschaften hinzugefügt, indem ein neuer Prototyp dafür festgelegt wird.  
  
```JavaScript  
var stringProp = { desc: "description" };  
  
String.__proto__ = stringProp;  
var s1 = "333";  
var s2 = new String("333");  
  
if (console && console.log) {  
  
    console.log(String.desc === "description"); // Returns true  
    console.log(s1.desc === "description");     // Returns false  
    console.log(s2.desc === "description");     // Returns false  
  
    s1.__proto__ = String;  // Can't be set.  
    s2.__proto__ = String;  
  
    console.log(s1.desc === "description"); // Returns false  
    console.log(s2.desc === "description"); // Returns true  
}  
```  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## <a name="see-also"></a>Siehe auch  
 [Prototypen und Prototypvererbung](../../javascript/advanced/prototypes-and-prototype-inheritance.md)