---
title: "Object.isExtensible-Funktion (JavaScript) | Microsoft Docs"
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
  - "isExtensible-Funktion [JavaScript]"
  - "Object.isExtensible-Funktion [JavaScript]"
ms.assetid: a7d10beb-0d01-4e2d-8263-59ff07ac4352
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# Object.isExtensible-Funktion (JavaScript)
Gibt einen Wert zurück, der angibt, ob neue Eigenschaften einem Objekt hinzugefügt werden können.  
  
## Syntax  
  
```javascript  
Object.isExtensible(object)  
```  
  
#### Parameter  
 `object`  
 Erforderlich.  Das zu überprüfende Objekt.  
  
## Rückgabewert  
 `true`, wenn das Objekt erweiterbar ist, was bedeutet, dass dem Objekt neue Eigenschaften hinzugefügt werden können; andernfalls `false`.  
  
## Ausnahmen  
 Wenn es sich beim `object`\-Argument nicht um ein Objekt handelt, wird eine `TypeError`\-Ausnahme ausgelöst.  
  
## Hinweise  
 Weitere Informationen über das Festlegen von Eigenschaftsattributen finden Sie unter [Object.defineProperty\-Funktion](../../javascript/reference/object-defineproperty-function-javascript.md).  Um die Attribute einer Eigenschaft abzurufen, können Sie [Object.getOwnPropertyDescriptor\-Funktion](../../javascript/reference/object-getownpropertydescriptor-function-javascript.md) verwenden.  
  
## Verwandte Funktionen  
 Die folgenden verwandten Funktionen verhindern die Änderung von Objektattributen.  
  
|Funktion|Das Objekt wird damit zu einem nicht erweiterbaren Objekt.|`configurable` wird für jede Eigenschaft auf `false` festgelegt.|`writable` wird für jede Eigenschaft auf `false` festgelegt.|  
|--------------|----------------------------------------------------------------|----------------------------------------------------------------------|------------------------------------------------------------------|  
|[Object.preventExtensions](../../javascript/reference/object-preventextensions-function-javascript.md)|Ja|Nein|Nein|  
|[Object.seal](../../javascript/reference/object-seal-function-javascript.md)|Ja|Ja|Nein|  
|[Object.freeze](../../javascript/reference/object-freeze-function-javascript.md)|Ja|Ja|Ja|  
  
 Die folgenden Funktionen geben `true` zurück, wenn alle Bedingungen, die in der folgenden Tabelle markiert sind, erfüllt werden.  
  
|Funktion|Ist das Objekt erweiterbar?|Ist `configurable` für alle Eigenschaften `false`?|Ist `writable` für alle Dateneigenschaften `false`?|  
|--------------|---------------------------------|--------------------------------------------------------|---------------------------------------------------------|  
|`Object.isExtensible`|Ja|Nein|Nein|  
|[Object.isSealed](../../javascript/reference/object-issealed-function-javascript.md)|Nein|Ja|Nein|  
|[Object.isFrozen](../../javascript/reference/object-isfrozen-function-javascript.md)|Nein|Ja|Ja|  
  
## Beispiel  
 Das folgende Beispiel veranschaulicht die Verwendung der `Object.isExtensible`\-Funktion.  
  
```javascript  
// Create an object that has two properties.  
var obj = { pasta: "spaghetti", length: 10 };  
  
// Make the object non-extensible.  
Object.preventExtensions(obj);  
  
// Try to add a new property, and then verify that it is not added.  
obj.newProp = 50;  
document.write(obj.newProp);  
  
// Output:  
undefined  
  
```  
  
## Anforderungen  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## Siehe auch  
 [Object.preventExtensions\-Funktion](../../javascript/reference/object-preventextensions-function-javascript.md)   
 [Object.seal\-Funktion](../../javascript/reference/object-seal-function-javascript.md)   
 [Object.freeze\-Funktion](../../javascript/reference/object-freeze-function-javascript.md)   
 [Object.isSealed\-Funktion](../../javascript/reference/object-issealed-function-javascript.md)   
 [Object.isFrozen\-Funktion](../../javascript/reference/object-isfrozen-function-javascript.md)