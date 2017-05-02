---
title: "Object.preventExtensions-Funktion (JavaScript) | Microsoft Docs"
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
  - "Object.preventExtensions-Funktion [JavaScript]"
  - "preventExtensions-Funktion [JavaScript]"
  - "neue Eigenschaften verhindern [JavaScript]"
  - "Eigenschaften [JavaScript], neue verhindern"
ms.assetid: e6b48197-2374-4437-a9fe-519dd45a2077
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# Object.preventExtensions-Funktion (JavaScript)
Verhindert das Hinzufügen neuer Eigenschaften zu einem Objekt.  
  
## Syntax  
  
```javascript  
Object.preventExtensions(object)  
```  
  
#### Parameter  
 `object`  
 Erforderlich.  Das Objekt, das nicht erweiterbar gemacht werden soll.  
  
## Rückgabewert  
 Das an die Funktion zu übergebende Objekt.  
  
## Ausnahmen  
 Wenn es sich beim `object`\-Argument nicht um ein Objekt handelt, wird eine `TypeError`\-Ausnahme ausgelöst.  
  
## Hinweise  
 Die `Object.preventExtensions`\-Funktion macht ein Objekt nicht erweiterbar, sodass ihm keine neuen benannten Eigenschaften hinzugefügt werden können.  Nachdem ein Objekt nicht erweiterbar gemacht wurde, ist es nicht möglich, es erweiterbar zu machen.  
  
 Weitere Informationen über das Festlegen von Eigenschaftsattributen finden Sie unter [Object.defineProperty\-Funktion](../../javascript/reference/object-defineproperty-function-javascript.md).  
  
## Verwandte Funktionen  
 Die folgenden verwandten Funktionen verhindern die Änderung von Objektattributen.  
  
|Funktion|Das Objekt wird damit zu einem nicht erweiterbaren Objekt.|`configurable` wird für jede Eigenschaft auf `false` festgelegt.|`writable` wird für jede Eigenschaft auf `false` festgelegt.|  
|--------------|----------------------------------------------------------------|----------------------------------------------------------------------|------------------------------------------------------------------|  
|`Object.preventExtensions`|Ja|Nein|Nein|  
|[Object.seal](../../javascript/reference/object-seal-function-javascript.md)|Ja|Ja|Nein|  
|[Object.freeze](../../javascript/reference/object-freeze-function-javascript.md)|Ja|Ja|Ja|  
  
 Die folgenden Funktionen geben `true` zurück, wenn alle Bedingungen, die in der folgenden Tabelle markiert sind, erfüllt werden.  
  
|Funktion|Ist das Objekt erweiterbar?|Ist `configurable` für alle Eigenschaften `false`?|Ist `writable` für alle Dateneigenschaften `false`?|  
|--------------|---------------------------------|--------------------------------------------------------|---------------------------------------------------------|  
|[Object.isExtensible](../../javascript/reference/object-isextensible-function-javascript.md)|Ja|Nein|Nein|  
|[Object.isSealed](../../javascript/reference/object-issealed-function-javascript.md)|Nein|Ja|Nein|  
|[Object.isFrozen](../../javascript/reference/object-isfrozen-function-javascript.md)|Nein|Ja|Ja|  
  
## Beispiel  
 Das folgende Beispiel veranschaulicht die Verwendung der `Object.preventExtensions`\-Funktion.  
  
```javascript  
// Create an object that has two properties.  
var obj = { pasta: "spaghetti", length: 10 };  
  
// Make the object non-extensible.  
Object.preventExtensions(obj);  
document.write(Object.isExtensible(obj));  
document.write("<br/>");  
  
// Try to add a new property, and then verify that it is not added.  
obj.newProp = 50;  
document.write(obj.newProp);  
  
// Output:  
// false  
// undefined  
  
```  
  
## Anforderungen  
 [!INCLUDE[jsv9](../../includes/jsv9-md.md)]  
  
## Siehe auch  
 [Object.seal\-Funktion](../../javascript/reference/object-seal-function-javascript.md)   
 [Object.freeze\-Funktion](../../javascript/reference/object-freeze-function-javascript.md)   
 [Object.isExtensible\-Funktion](../../javascript/reference/object-isextensible-function-javascript.md)   
 [Object.isSealed\-Funktion](../../javascript/reference/object-issealed-function-javascript.md)   
 [Object.isFrozen\-Funktion](../../javascript/reference/object-isfrozen-function-javascript.md)