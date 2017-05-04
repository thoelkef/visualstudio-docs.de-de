---
title: "Object.isFrozen-Funktion (JavaScript) | Microsoft Docs"
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
  - "isFrozen-Funktion [JavaScript]"
  - "Object.isFrozen-Funktion [JavaScript]"
ms.assetid: 6cf1bbc6-56e8-429b-8e2c-0024fa614acc
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# Object.isFrozen-Funktion (JavaScript)
Gibt `true` zurück, wenn vorhandene Eigenschaftenattribute und deren Werte in einem Objekt nicht geändert werden können und neue Eigenschaften nicht dem Objekt hinzugefügt werden können.  
  
## Syntax  
  
```javascript  
Object.isFrozen(object)  
```  
  
#### Parameter  
 `object`  
 Erforderlich.  Das zu überprüfende Objekt.  
  
## Rückgabewert  
 `true`, wenn die folgenden Bedingungen alle erfüllt sind:  
  
-   Das Objekt ist nicht erweiterbar, das bedeutet, dass dem Objekt keine neue Eigenschaften hinzugefügt werden können.  
  
-   Das `configurable`\-Attribut ist für alle vorhandenen Eigenschaften `false`.  
  
-   Das `writable`\-Attribut ist für alle Eigenschaften der vorhandenen Daten `false`.  
  
 Wenn das Objekt über keine Eigenschaften verfügt, gibt die Funktion `true` zurück, wenn das Objekt nicht erweiterbar ist.  
  
## Ausnahmen  
 Wenn es sich beim `object`\-Argument nicht um ein Objekt handelt, wird eine `TypeError`\-Ausnahme ausgelöst.  
  
## Hinweise  
 Wenn das `configurable`\-Attribut einer Eigenschaft `false` ist, können die Eigenschaftenattribute nicht geändert und die Eigenschaft kann nicht gelöscht werden.  Wenn das `writable`\-Attribut `false` ist, kann der Dateneigenschaftenwert nicht geändert werden.  Wenn `configurable` `false` ist und `writable` `true` ist, können das `value`\-Attribut und das `writable`\-Attribut geändert werden.  
  
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
|[Object.isExtensible](../../javascript/reference/object-isextensible-function-javascript.md)|Ja|Nein|Nein|  
|[Object.isSealed](../../javascript/reference/object-issealed-function-javascript.md)|Nein|Ja|Nein|  
|`Object.isFrozen`|Nein|Ja|Ja|  
  
## Beispiel  
 Das folgende Beispiel veranschaulicht die Verwendung der `Object.isFrozen`\-Funktion.  
  
```javascript  
// Create an object that has two properties.  
var obj = { pasta: "spaghetti", length: 10 };  
  
// Freeze the object, and verify that it is frozen.  
Object.freeze(obj);  
document.write(obj.isFrozen());  
  
// Try to add a new property, and then verify that it is not added.   
obj.newProp = 50;  
document.write (obj.newProp);  
document.write ("<br/>");  
  
// Try to delete a property, and then verify that it is still present.  
delete obj.length;  
document.write (obj.length);  
document.write ("<br/> ");  
  
// Try to change a property value, and then verify that it is not changed.  
obj.pasta = "linguini";  
document.write (obj.pasta);  
  
// Output:  
// true  
// undefined  
// 10  
// spaghetti  
  
```  
  
## Anforderungen  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## Siehe auch  
 [Object.preventExtensions\-Funktion](../../javascript/reference/object-preventextensions-function-javascript.md)   
 [Object.seal\-Funktion](../../javascript/reference/object-seal-function-javascript.md)   
 [Object.freeze\-Funktion](../../javascript/reference/object-freeze-function-javascript.md)   
 [Object.isExtensible\-Funktion](../../javascript/reference/object-isextensible-function-javascript.md)   
 [Object.isSealed\-Funktion](../../javascript/reference/object-issealed-function-javascript.md)   
 [Object.defineProperty\-Funktion](../../javascript/reference/object-defineproperty-function-javascript.md)   
 [Object.getOwnPropertyDescriptor\-Funktion](../../javascript/reference/object-getownpropertydescriptor-function-javascript.md)   
 [Object.getOwnPropertyNames\-Funktion](../../javascript/reference/object-getownpropertynames-function-javascript.md)