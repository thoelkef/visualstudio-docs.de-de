---
title: "Object.keys-Funktion (JavaScript) | Microsoft Docs"
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
  - "keys-Methode [JavaScript]"
  - "Object.keys-Methode [JavaScript]"
ms.assetid: cf4a7daf-cf28-4467-bc6b-f7f106ec3876
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# Object.keys-Funktion (JavaScript)
Gibt die Namen der aufzählbaren Eigenschaften und Methoden eines Objekts zurück.  
  
## Syntax  
  
```javascript  
Object.keys(object)  
```  
  
#### Parameter  
  
|Parameter|Definition|  
|---------------|----------------|  
|`object`|Erforderlich.  Das Objekt, das die Eigenschaften und Methoden enthält.  Dies kann ein von Ihnen erstelltes Objekt oder ein vorhandenes Objekt des Dokumentobjektmodells \(Document Object Model, DOM\) sein.|  
  
## Rückgabewert  
 Ein Array, das die Namen der aufzählbaren Eigenschaften und Methoden des Objekts enthält.  
  
## Ausnahmen  
 Wenn der Wert, der für das `object`\-Argument angegeben wird, nicht der Name eines Objekts ist, wird eine Ausnahme vom Typ `TypeError` ausgelöst.  
  
## Hinweise  
 Die `keys`\-Methode gibt nur die Namen von aufzählbaren Eigenschaften und Methoden zurück.  Um die Namen von aufzählbaren und nicht aufzählbaren Eigenschaften und Methoden zurückzugeben, können Sie [Object.getOwnPropertyNames\-Funktion](../../javascript/reference/object-getownpropertynames-function-javascript.md) verwenden.  
  
 Informationen zum `enumerable`\-Attribut einer Eigenschaft finden Sie unter [Object.defineProperty\-Funktion](../../javascript/reference/object-defineproperty-function-javascript.md) und [Object.getOwnPropertyDescriptor\-Funktion](../../javascript/reference/object-getownpropertydescriptor-function-javascript.md).  
  
## Beispiel  
 Im folgenden Beispiel wird ein Objekt erstellt, das drei Eigenschaften und eine Methode verfügt.  Sie verwendet anschließend die `keys`\-Methode, um die Eigenschaften und Methoden des Objekts abzurufen.  
  
```javascript  
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
  
## Beispiel  
 Im folgenden Beispiel werden die Namen aller aufzählbaren Eigenschaften angezeigt, die mit dem Buchstaben "g" im Pasta\-Objekt beginnen.  
  
```javascript  
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
  
## Anforderungen  
 [!INCLUDE[jsv9](../../includes/jsv9-md.md)]  
  
## Siehe auch  
 [Object.getOwnPropertyNames\-Funktion](../../javascript/reference/object-getownpropertynames-function-javascript.md)