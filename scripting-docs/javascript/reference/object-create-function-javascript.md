---
title: "Object.create-Funktion (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "create-Funktion [JavaScript]"
  - "Object.create-Funktion [JavaScript]"
ms.assetid: 0ad31f36-a9ee-444e-b0fe-c87843d03196
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# Object.create-Funktion (JavaScript)
Erstellt ein Objekt, das den angegebenen Prototyp besitzt und das optional die angegebenen Eigenschaften enthält.  
  
## Syntax  
  
```  
Object.create(prototype, descriptors)  
```  
  
#### Parameter  
 `prototype`  
 Erforderlich.  Das als Prototyp zu verwendende Objekt.  Kann `null` sein.  
  
 `descriptors`  
 Optional.  Ein [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]\-Objekt, das eine oder mehrere Eigenschaftendeskriptoren enthält.  
  
 Eine *Dateneigenschaft* ist eine Eigenschaft, die einen Wert abrufen und festlegen kann.  Ein Dateneigenschaftendeskriptor enthält ein `value`\-Attribut sowie die Attribute `writable`, `enumerable` und `configurable`.  Werden die letzten drei Attribute nicht angegeben, werden sie standardmäßig auf `false` festgelegt.  Eine *Accessoreigenschaft* ruft immer dann eine vom Benutzer bereitgestellte Funktion auf, wenn der Wert abgerufen oder festgelegt wird.  Ein Accessoreigenschaftendeskriptor enthält ein `set`\-Attribut, ein `get`\-Attribut oder beides.  Weitere Informationen finden Sie unter [Object.defineProperty\-Funktion](../../javascript/reference/object-defineproperty-function-javascript.md).  
  
## Rückgabewert  
 Ein neues Objekt, das den angegebenen internen Prototyp besitzt und die angegebenen Eigenschaften enthält, sofern vorhanden.  
  
## Ausnahmen  
 Eine `TypeError`\-Ausnahme wird ausgelöst, wenn eine der folgenden Bedingungen zutrifft:  
  
-   Das `prototype`\-Argument ist kein Objekt und nicht `null`.  
  
-   Ein Deskriptor im `descriptors`\-Argument verfügt über ein `value`\- oder `writable`\-Attribut sowie über ein `get`\- oder `set`\-Attribut.  
  
-   Ein Deskriptor im `descriptors`\-Argument verfügt über ein `get`\- oder `set`\-Attribut, das keine Funktion ist.  
  
## Hinweise  
 Sie können diese Funktion mithilfe eines `null` `prototype`\-Parameters verwenden, um die Prototypenkette zu beenden.  Das erstellte Objekt hat keinen Prototyp.  
  
## Beispiel  
 Im folgenden Beispiel wird ein Objekt mit einem `null`\-Prototyp erstellt und es werden zwei aufzählbare Eigenschaften hinzugefügt.  
  
```javascript  
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
  
## Beispiel  
 Im folgenden Beispiel wird ein Objekt erstellt, das den gleichen internen Prototyp wie das Object\-Objekt besitzt.  Wie Sie sehen, hat es den gleichen Prototyp wie ein Objekt, das mit einem Objektliteral erstellt wird.  Die [Object.getPrototypeOf](../../javascript/reference/object-getprototypeof-function-javascript.md)\-Funktion ruft den Prototyp des ursprünglichen Objekts ab.  Um den Eigenschaftendeskriptor des Objekts abzurufen, können Sie [Object.getOwnPropertyDescriptor\-Funktion](../../javascript/reference/object-getownpropertydescriptor-function-javascript.md) verwenden.  
  
```javascript  
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
  
## Beispiel  
 Im folgenden Beispiel wird ein Objekt erstellt, das den gleichen internen Prototyp wie das Shape\-Objekt besitzt.  
  
```javascript  
  
// Create the shape object.  
var Shape = { twoDimensional: true, color: undefined, hasLineSegments: undefined };  
  
var Square = Object.create(Object.getPrototypeOf(Shape));  
  
```  
  
## Anforderungen  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## Siehe auch  
 [Object.getPrototypeOf\-Funktion](../../javascript/reference/object-getprototypeof-function-javascript.md)   
 [isPrototypeOf\-Methode \(Objekt\)](../../javascript/reference/isprototypeof-method-object-javascript.md)   
 [Erstellen von Objekten](../../javascript/creating-objects-javascript.md)