---
title: "Proxy-Objekt (JavaScript) | Microsoft Docs"
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
ms.assetid: 2b89abee-04fa-47e6-9676-980016cff5f8
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# Proxy-Objekt (JavaScript)
Aktiviert das benutzerdefinierte Verhalten eines Objekts.  
  
## Syntax  
  
```  
proxyObj = new Proxy(target, handler)  
```  
  
#### Parameter  
 `target`  
 Erforderlich.  Ein Objekt oder eine Funktion, das\/die vom Proxy virtualisiert werden soll.  
  
 `handler`  
 Erforderlich.  Ein Objekt mit Methoden \(Traps\), die das benutzerdefinierte Verhalten implementieren.  
  
## Hinweise  
 Ein `Proxy`\-Objekt wird verwendet, um interne hardwarenahe Vorgänge für ein anderes Objekt abzufangen.  Proxy\-Objekte können zum Abfangen, für die Objektvirtualisierung, Protokollierung\/Profilerstellung und andere Zwecke verwendet werden.  
  
 Wenn ein Trap für einen bestimmten Vorgang nicht im Handler für den Proxy definiert wurde, wird der Vorgang zum Ziel weitergeleitet.  
  
 Das Handlerobjekt definiert die folgenden Methoden \(Traps\), um benutzerdefiniertes Verhalten zu implementieren.  Die hier dargestellten Beispiele sind nicht vollständig.  Verwenden Sie zur Unterstützung bedingter Standardverhalten in der Handlermethode Methoden von [Reflect\-Objekt](../../javascript/reference/reflect-object-javascript.md).  
  
|Syntax der Handlermethode \(Trap\)|Beispiele der Verwendung|  
|----------------------------------------|------------------------------|  
|`apply: function(target, thisArg, args)`|Ein Trap für einen Funktionsaufruf.|  
|`construct: function(target, args)`|Ein Trap für einen Konstruktor.|  
|`defineProperty: function(target, propertyName, descriptor)`|Ein Trap für [Object.defineProperty\-Funktion](../../javascript/reference/object-defineproperty-function-javascript.md).|  
|`deleteProperty: function(target, propertyName)`|Ein Trap für die `delete`\-Anweisung.|  
|`enumerate: function(target)`|Ein Trap für die [for... in](../../javascript/reference/for-dot-dot-dot-in-statement-javascript.md)\-Anweisung [Object.getOwnPropertySymbols](../../javascript/reference/object-getownpropertysymbols-function-javascript.md), [Object.keys](../../javascript/reference/object-keys-function-javascript.md)\-Funktion und [JSON.stringify](../../javascript/reference/json-stringify-function-javascript.md).|  
|`get: function(target, propertyName, receiver)`|Ein Trap für alle [getter](../../javascript/creating-objects-javascript.md)\-Eigenschaften.|  
|`getOwnPropertyDescriptor: function(target, propertyName)`|Ein Trap für [Object.getOwnPropertyDescriptor\-Funktion](../../javascript/reference/object-getownpropertydescriptor-function-javascript.md).|  
|`getPrototypeOf: function(target)`|Ein Trap für [Object.getPrototypeOf\-Funktion](../../javascript/reference/object-getprototypeof-function-javascript.md).|  
|`has: function(target, propertyName)`|Ein Trap für den `in`\-Operator, [hasOwnProperty\-Methode \(Objekt\)](../../javascript/reference/hasownproperty-method-object-javascript.md) und andere Methoden.|  
|`isExtensible: function(target)`|Ein Trap für [Object.isExtensible\-Funktion](../../javascript/reference/object-isextensible-function-javascript.md).|  
|`ownKeys: function(target)`|Ein Trap für [Object.getOwnPropertyNames\-Funktion](../../javascript/reference/object-getownpropertynames-function-javascript.md).|  
|`preventExtensions: function(target)`|Ein Trap für [Object.preventExtensions\-Funktion](../../javascript/reference/object-preventextensions-function-javascript.md).|  
|`set: function(target, propertyName, value, receiver)`|Ein Trap für [setter](../../javascript/creating-objects-javascript.md)\-Eigenschaften.|  
|`setPrototypeOf: function(target, prototype)`|Ein Trap für [Object.setPrototypeOf](../../javascript/reference/object-setprototypeof-function-javascript.md).|  
  
## Beispiel  
 Im folgenden Codebeispiel wird veranschaulicht, wie ein Proxy für ein Objektliteral mit dem Trap `get` erstellt wird.  
  
```javascript  
var target = {};  
var handler = {  
  get: function (receiver, name) {  
    // This example includes a template string.  
    return `Hello, ${name}!`;  
  }  
};  
  
var p = new Proxy(target, handler);  
console.log(p.world);  
  
// Output:  
// Hello, world!  
  
```  
  
## Beispiel  
 Im folgenden Codebeispiel wird veranschaulicht, wie ein Proxy für eine Funktion mit dem Trap `apply` erstellt wird.  
  
```javascript  
var target = function () { return 'I am the target'; };  
var handler = {  
  // This example includes a rest parameter.  
  apply: function (receiver, ...args) {  
    return 'I am the proxy';  
  }  
};  
  
var p = new Proxy(target, handler);  
console.log(target()):  
console.log(p()):  
  
// Output:  
// I am the target  
// I am the proxy  
```  
  
## Anforderungen  
 [!INCLUDE[jsv12](../../includes/jsv12-md.md)]