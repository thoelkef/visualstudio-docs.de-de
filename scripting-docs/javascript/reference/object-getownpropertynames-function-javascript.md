---
title: "Object.getOwnPropertyNames-Funktion (JavaScript) | Microsoft Docs"
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
  - "getOwnPropertyNames-Methode [JavaScript]"
  - "Object.getOwnPropertyNames-Methode [JavaScript]"
ms.assetid: 59f4b6b1-02be-44b3-a06c-a5ca8f70c3d8
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# Object.getOwnPropertyNames-Funktion (JavaScript)
Gibt die Namen der dem Objekt eigenen Eigenschaften zurück.  Eigenschaften, die einem Objekt eigen sind, werden direkt für dieses Objekt definiert und nicht vom Prototyp des Objekts geerbt.  Zu den Eigenschaften eines Objekts gehören sowohl Felder \(Objekte\) als auch Funktionen.  
  
## Syntax  
  
```javascript  
Object.getOwnPropertyNames(object)  
```  
  
#### Parameter  
  
|Parameter|Definition|  
|---------------|----------------|  
|`object`|Erforderlich.  Das Objekt, dem die Eigenschaften eigen sind.|  
  
## Rückgabewert  
 Ein Array, das die Namen der Eigenschaften enthält, die dem Objekt eigen sind.  
  
## Ausnahmen  
 Wenn der Wert, der für das `object`\-Argument angegeben wird, nicht der Name eines Objekts ist, wird eine Ausnahme vom Typ `TypeError` ausgelöst.  
  
## Hinweise  
 Die `getOwnPropertyNames`\-Methode gibt die Namen von aufzählbaren und nicht aufzählbaren Eigenschaften und Methoden zurück.  Um nur die Namen von aufzählbaren Eigenschaften und Methoden zurückzugeben, können Sie [Object.keys\-Funktion](../../javascript/reference/object-keys-function-javascript.md) verwenden.  
  
## Beispiel  
 Im folgenden Beispiel wird ein Objekt erstellt, das drei Eigenschaften und eine Methode verfügt.  Dann wird die `getOwnPropertyNames`\-Methode verwendet, um die eigenen Eigenschaften \(einschließlich der Methode\) des Objekts zu erhalten.  
  
```javascript  
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
  
## Beispiel  
 Im folgenden Beispiel werden die Namen von Eigenschaften angezeigt, die in einem Spaghettiobjekt, das mit dem Pasta\-Konstruktor erstellt wird, mit dem Buchstaben"s" beginnen.  
  
```javascript  
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
  
## Anforderungen  
 [!INCLUDE[jsv9](../../includes/jsv9-md.md)]  
  
## Siehe auch  
 [Object.keys\-Funktion](../../javascript/reference/object-keys-function-javascript.md)