---
title: "Object.isSealed-Funktion (JavaScript) | Microsoft Docs"
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
  - "isSealed-Funktion [JavaScript]"
  - "Object.isSealed [JavaScript]"
  - "Eigenschaften [JavaScript], Attribute sperren"
ms.assetid: af4f192e-cebe-44b9-8eef-90c096f5ae8f
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# Object.isSealed-Funktion (JavaScript)
Gibt `true` zurück, wenn vorhandene Eigenschaftenattribute und deren Werte in einem Objekt nicht geändert werden können und neue Eigenschaften nicht dem Objekt hinzugefügt werden können.  
  
## Syntax  
  
```javascript  
Object.isSealed(object)  
```  
  
#### Parameter  
 `object`  
 Erforderlich.  Das zu überprüfende Objekt.  
  
## Rückgabewert  
 `true`, wenn die folgenden Bedingungen alle erfüllt sind:  
  
-   Das Objekt ist nicht erweiterbar, das bedeutet, dass dem Objekt keine neue Eigenschaften hinzugefügt werden können.  
  
-   Das `configurable`\-Attribut ist für alle vorhandenen Eigenschaften `false`.  
  
 Wenn das Objekt über keine Eigenschaften verfügt, gibt die Funktion `true` zurück, wenn das Objekt nicht erweiterbar ist.  
  
## Ausnahmen  
 Wenn es sich beim `object`\-Argument nicht um ein Objekt handelt, wird eine `TypeError`\-Ausnahme ausgelöst.  
  
## Hinweise  
 Wenn das `configurable`\-Attribut einer Eigenschaft `false` ist, können die Eigenschaftenattribute nicht geändert und die Eigenschaft kann nicht gelöscht werden.  Wenn das `writable`\-Attribut `false` ist, kann der Dateneigenschaftenwert nicht geändert werden.  Wenn `configurable` `false` ist und `writable` `true` ist, können das `value`\-Attribut und das `writable`\-Attribut geändert werden.  
  
 Die `Object.isSealed`\-Funktion verwendet das `writable`\-Attribut von Eigenschaften nicht, um den Rückgabewert zu bestimmen.  
  
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
|`Object.isSealed`|Nein|Ja|Nein|  
|[Object.isFrozen](../../javascript/reference/object-isfrozen-function-javascript.md)|Nein|Ja|Ja|  
  
## Beispiel  
 Das folgende Beispiel veranschaulicht die Verwendung der `Object.isSealed`\-Funktion.  
  
```javascript  
// Create an object that has two properties.  
var obj = { pasta: "spaghetti", length: 10 };  
  
// Seal the object, and verify that it is sealed.  
Object.seal(obj);  
document.write(Object.isSealed(obj));  
document.write("<br/>");  
  
// Try to add a new property, and then verify that it is not added.   
obj.newProp = 50;  
document.write(obj.newProp);  
document.write("<br/>");  
  
// Try to delete a property, and then verify that it is still present.   
delete obj.length;  
document.write(obj.length);  
  
// Output:  
// true  
// undefined  
// 10  
  
```  
  
## Anforderungen  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## Siehe auch  
 [Object.preventExtensions\-Funktion](../../javascript/reference/object-preventextensions-function-javascript.md)   
 [Object.seal\-Funktion](../../javascript/reference/object-seal-function-javascript.md)   
 [Object.freeze\-Funktion](../../javascript/reference/object-freeze-function-javascript.md)   
 [Object.isExtensible\-Funktion](../../javascript/reference/object-isextensible-function-javascript.md)   
 [Object.isFrozen\-Funktion](../../javascript/reference/object-isfrozen-function-javascript.md)   
 [Object.defineProperty\-Funktion](../../javascript/reference/object-defineproperty-function-javascript.md)   
 [Object.getOwnPropertyDescriptor\-Funktion](../../javascript/reference/object-getownpropertydescriptor-function-javascript.md)