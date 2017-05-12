---
title: "Object.seal-Funktion (JavaScript) | Microsoft Docs"
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
  - "Object.seal-Funktion"
  - "seal-Funktion"
ms.assetid: e72c804a-4dab-4ec9-b9df-9c9c908aa12d
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# Object.seal-Funktion (JavaScript)
Verhindert die Änderung von Attributen vorhandener Eigenschaften und verhindert die Hinzufügung neuer Eigenschaften.  
  
## Syntax  
  
```javascript  
Object.seal(object)  
```  
  
#### Parameter  
 `object`  
 Erforderlich.  Das Objekt, dessen Attribute gesperrt werden sollen.  
  
## Rückgabewert  
 Das an die Funktion zu übergebende Objekt.  
  
## Ausnahmen  
 Wenn es sich beim `object`\-Argument nicht um ein Objekt handelt, wird eine `TypeError`\-Ausnahme ausgelöst.  
  
## Hinweise  
 Die `Object.seal`\-Funktion führt beide der folgenden Aktionen aus:  
  
-   Macht das Objekt nicht erweiterbar, sodass keine neuen Eigenschaften hinzugefügt werden können.  
  
-   Legt das `configurable`\-Attribut für alle Eigenschaften des Objekts auf `false` fest.  
  
 Wenn das `configurable`\-Attribut den Wert `false` hat, können Eigenschaftenattribute nicht geändert werden, und die Eigenschaft kann nicht gelöscht werden.  Wenn `configurable` `false` ist und `writable` `true` ist, können das `value`\-Attribut und das `writable`\-Attribut geändert werden.  
  
 Die `Object.seal`\-Funktion ändert das `writable`\-Attribut nicht.  
  
 Weitere Informationen über das Festlegen von Eigenschaftsattributen finden Sie unter [Object.defineProperty\-Funktion](../../javascript/reference/object-defineproperty-function-javascript.md).  Um die Attribute einer Eigenschaft abzurufen, können Sie [Object.getOwnPropertyDescriptor\-Funktion](../../javascript/reference/object-getownpropertydescriptor-function-javascript.md) verwenden.  
  
## Verwandte Funktionen  
 Die folgenden verwandten Funktionen verhindern die Änderung von Objektattributen.  
  
|Funktion|Das Objekt wird damit zu einem nicht erweiterbaren Objekt.|`configurable` wird für jede Eigenschaft auf `false` festgelegt.|`writable` wird für jede Eigenschaft auf `false` festgelegt.|  
|--------------|----------------------------------------------------------------|----------------------------------------------------------------------|------------------------------------------------------------------|  
|[Object.preventExtensions](../../javascript/reference/object-preventextensions-function-javascript.md)|Ja|Nein|Nein|  
|`Object.seal`|Ja|Ja|Nein|  
|[Object.freeze](../../javascript/reference/object-freeze-function-javascript.md)|Ja|Ja|Ja|  
  
 Die folgenden Funktionen geben `true` zurück, wenn alle Bedingungen, die in der folgenden Tabelle markiert sind, erfüllt werden.  
  
|Funktion|Ist das Objekt erweiterbar?|Ist `configurable` für alle Eigenschaften `false`?|Ist `writable` für alle Dateneigenschaften `false`?|  
|--------------|---------------------------------|--------------------------------------------------------|---------------------------------------------------------|  
|[Object.isExtensible](../../javascript/reference/object-isextensible-function-javascript.md)|Ja|Nein|Nein|  
|[Object.isSealed](../../javascript/reference/object-issealed-function-javascript.md)|Nein|Ja|Nein|  
|[Object.isFrozen](../../javascript/reference/object-isfrozen-function-javascript.md)|Nein|Ja|Ja|  
  
## Beispiel  
 Das folgende Beispiel veranschaulicht die Verwendung der `Object.seal`\-Funktion.  
  
```javascript  
// Create an object that has two properties.  
var obj = { pasta: "spaghetti", length: 10 };  
// Seal the object.  
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
 [Object.freeze\-Funktion](../../javascript/reference/object-freeze-function-javascript.md)   
 [Object.isExtensible\-Funktion](../../javascript/reference/object-isextensible-function-javascript.md)   
 [Object.isSealed\-Funktion](../../javascript/reference/object-issealed-function-javascript.md)   
 [Object.isFrozen\-Funktion](../../javascript/reference/object-isfrozen-function-javascript.md)