---
title: "constructor-Eigenschaft (Objekt) (JavaScript) | Microsoft Docs"
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
  - "constructor"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "constructor-Eigenschaft"
ms.assetid: 6f5d0e9d-e85f-4fde-b558-744510483d69
caps.latest.revision: 17
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 17
---
# constructor-Eigenschaft (Objekt) (JavaScript)
Gibt die Funktion an, durch die ein Objekt erstellt wird.  
  
## Syntax  
  
```  
  
object.constructor  
```  
  
## Hinweise  
 Das erforderliche `object`\-Argument enthält den Namen eines Objekts oder einer Funktion.  
  
 Die `constructor`\-Eigenschaft ist ein Member des Prototyps eines jeden Objekts, das einen Prototyp besitzt.  Dies schließt alle systeminternen [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]\-Objekte mit Ausnahme der Objekte `Global` und `Math` ein.  Die `constructor`\-Eigenschaft enthält einen Verweis auf die Funktion, mit der die Instanzen des betreffenden Objekts erstellt werden.  
  
## Beispiel  
 Das folgende Beispiel veranschaulicht die Verwendung der constructor\-Eigenschaft.  
  
```javascript  
// A constructor function.  
function MyObj() {  
    this.number = 1;  
}  
  
var x = new String("Hi");  
  
if (x.constructor == String)  
    document.write("Object is a String.");  
document.write ("<br />");  
  
var y = new MyObj;  
if (y.constructor == MyObj)  
    document.write("Object constructor is MyObj.");  
  
// Output:  
// Object is a String.  
// Object constructor is MyObj.  
  
```  
  
## Anforderungen  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]  
  
## Siehe auch  
 [prototype\-Eigenschaft \(Objekt\)](../../javascript/reference/prototype-property-object-javascript.md)