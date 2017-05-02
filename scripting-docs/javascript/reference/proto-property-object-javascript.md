---
title: "__proto__-Eigenschaft (Object) (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "__proto__"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: 97c3f84d-125e-4905-b921-b021264964ee
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# __proto__-Eigenschaft (Object) (JavaScript)
Enthält einen Verweis auf den internen Prototyp des angegebenen Objekts.  
  
## Syntax  
  
```  
object.__proto__  
```  
  
#### Parameter  
 `object`  
 Erforderlich.  Das Objekt, für das der Prototyp festgelegt werden soll.  
  
## Hinweise  
 Mit der `__proto__`\-Eigenschaft kann der Prototyp für ein Objekt festgelegt werden.  
  
 Das Objekt oder die Funktion erbt alle Methoden und Eigenschaften des neuen Prototyps und alle Methoden und Eigenschaften in der Prototypenkette neuen des Prototyps.  Ein Objekt kann nur einen einzigen Prototypen aufweisen \(geerbte Prototypen in der Prototypenkette zählen nicht\), wenn Sie daher die `__proto__`\-Eigenschaft aufrufen, ersetzen Sie den vorherigen Prototypen.  
  
 Sie können den Prototyp nur für ein erweiterbares Objekt festlegen.  Weitere Informationen hierzu finden Sie unter [Object.preventExtensions\-Funktion](../../javascript/reference/object-preventextensions-function-javascript.md).  
  
> [!NOTE]
>  Der `__proto__`\-Eigenschaftenname beginnt und endet mit zwei Unterstrichen.  
  
## Beispiel  
 Das folgende Codebeispiel veranschaulicht, wie der Prototyp für ein Objekt festgelegt wird.  
  
```javascript  
function Rectangle() {  
}  
  
var rec = new Rectangle();  
  
if (console && console.log) {  
    console.log(rec.__proto__ === Rectangle.prototype);  // Returns true  
    rec.__proto__ = Object.prototype;  
    console.log(rec.__proto__ === Rectangle.prototype);  // Returns false  
}  
```  
  
## Beispiel  
 Im folgenden Codebeispiel wird veranschaulicht, wie Eigenschaften einem Objekt hinzugefügt werden, indem sie dem Prototypen hinzugefügt werden.  
  
```javascript  
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
  
## Beispiel  
 Im folgenden Codebeispiel werden dem `String`\-Objekt Eigenschaften hinzugefügt, indem ein neuer Prototyp dafür festgelegt wird.  
  
```javascript  
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
  
## Anforderungen  
 [!INCLUDE[jsv11](../../includes/jsv11-md.md)]  
  
## Siehe auch  
 [Prototypen und Prototypvererbung](../../javascript/advanced/prototypes-and-prototype-inheritance.md)