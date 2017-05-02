---
title: "Reflect-Objekt (JavaScript) | Microsoft Docs"
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
ms.assetid: 1df74f34-2eb4-42f1-a930-b943c86daa0e
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# Reflect-Objekt (JavaScript)
Stellt Methoden zur Verwendung in Vorgängen bereit, die abgefangen werden.  
  
## Syntax  
  
```  
Reflect.[method]  
```  
  
#### Parameter  
 `method`  
 Erforderlich.  Name einer der Methoden des `Reflect`\-Objekts.  
  
## Hinweise  
 Das Reflect\-Objekt kann nicht mit dem `new`\-Operator instanziiert werden.  
  
 Reflect\-Methoden werden häufig mit [Proxys](../../javascript/reference/proxy-object-javascript.md) verwendet, da sie Ihnen das Delegieren zu Standardverhalten ermöglichen, ohne das Standardverhalten in Ihrem Code zu implementieren.  
  
 Reflect stellt eine statische Methode mit dem gleichen Namen wie jedes Proxytrap bereit.  Die Beschreibungen in der Tabelle sind nicht vollständig.  
  
|Methode|Beschreibung|  
|-------------|------------------|  
|`Reflect.apply(target, thisArg, args)`|Ähnlich wie die [apply](../../javascript/reference/apply-method-function-javascript.md)\-Methode des Function\-Objekts.|  
|`Reflect.construct(target, args)`|Eine für den `new`\-Operator gleichwertige Funktion.|  
|`Reflect.defineProperty(target, propertyName, descriptor)`|Ähnlich wie [Object.defineProperty](../../javascript/reference/object-defineproperty-function-javascript.md).  Gibt einen booleschen Wert zurück, der angibt, ob der Aufruf erfolgreich war.|  
|`Reflect.deleteProperty(target, propertyName)`|Ähnelt der `delete`\-Anweisung.  Gibt einen booleschen Wert zurück, der angibt, ob der Aufruf erfolgreich war.|  
|`Reflect.enumerate(target)`|Ähnlich wie [for...in](../../javascript/reference/for-dot-dot-dot-in-statement-javascript.md)\-Anweisung, [Object.getOwnPropertySymbols](../../javascript/reference/object-getownpropertysymbols-function-javascript.md), [Object.keys](../../javascript/reference/object-keys-function-javascript.md)\-Funktion und [JSON.stringify](../../javascript/reference/json-stringify-function-javascript.md).|  
|`Reflect.get(target, propertyName, receiver)`|Eine für alle [getter](../../javascript/creating-objects-javascript.md)\-Eigenschaften gleichwertige Funktion.|  
|`Reflect.getOwnPropertyDescriptor(target, propertyName)`|Ähnlich wie [Object.getOwnPropertyDescriptor](../../javascript/reference/object-getownpropertydescriptor-function-javascript.md).  Gibt einen booleschen Wert zurück, der angibt, ob der Aufruf erfolgreich war.|  
|`Reflect.getPrototypeOf(target)`|Ähnlich wie [Object.getPrototypeOf](../../javascript/reference/object-getprototypeof-function-javascript.md).|  
|`Reflect.has(target, propertyName)`|Ähnlich wie der `in`\-Operator, [hasOwnProperty\-Methode \(Objekt\)](../../javascript/reference/hasownproperty-method-object-javascript.md) und andere Methoden.  Gibt einen booleschen Wert zurück, der angibt, ob der Aufruf erfolgreich war.|  
|`Reflect.isExtensible(target)`|Ähnlich wie [Object.isExtensible](../../javascript/reference/object-isextensible-function-javascript.md).|  
|`Reflect.ownKeys(target)`|Ähnlich wie [Object.getOwnPropertyNames](../../javascript/reference/object-getownpropertynames-function-javascript.md).|  
|`Reflect.preventExtensions(target)`|Ähnlich wie [Object.preventExtensions](../../javascript/reference/object-preventextensions-function-javascript.md).  Gibt einen booleschen Wert zurück, der angibt, ob der Aufruf erfolgreich war.|  
|`Reflect.set(target, propertyName, value, receiver)`|Ähnlich wie die Verwendung einer [setter](../../javascript/creating-objects-javascript.md)\-Eigenschaft.  Gibt einen booleschen Wert zurück, der angibt, ob der Aufruf erfolgreich war.|  
|`Reflect.setPrototypeOf(target, prototype)`|Ähnlich wie [Object.setPrototypeOf](../../javascript/reference/object-setprototypeof-function-javascript.md).  Gibt einen booleschen Wert zurück, der angibt, ob der Aufruf erfolgreich war.|  
  
## Beispiel  
 Im folgenden Codebeispiel wird die Verwendung von `Reflect.get` zum Schreiben eines Proxys veranschaulicht, der get\-Vorgänge für Eigenschaften, die mit einem Unterstrich beginnen, blockiert.  
  
```javascript  
var p = new Proxy({}, {  
    get(k, t, r) {  
        // return undefined if key begins with underscore  
        if(k[0] === '_') return undefined;  
  
       // otherwise do default behavior  
       return Reflect.get(k, t, r);  
    }  
});  
  
p._foo = 1;  
console.log(p._foo);  
  
p.foo = 1;  
console.log(p.foo);  
  
// Output:  
// undefined  
// 1  
  
```  
  
## Anforderungen  
 [!INCLUDE[jsv12](../../includes/jsv12-md.md)]