---
title: "forEach-Methode (Set) (JavaScript) | Microsoft Docs"
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
ms.assetid: 813bff6e-6098-4260-ab6e-b0d2da6be94d
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# forEach-Methode (Set) (JavaScript)
Führt die angegebene Aktion für jedes Element in einem Satz aus.  
  
## Syntax  
  
```javascript  
setObj.forEach(callbackfn[, thisArg])  
```  
  
#### Parameter  
 `setObj`  
 Erforderlich.  Ein `Set`\-Objekt.  
  
 `callbackfn`  
 Erforderlich.  `callbackfn` akzeptiert bis zu drei Argumente.  Die Funktion, die `forEach` einmal für jedes Element im Satz aufruft.  
  
 `thisArg`  
 Optional.  Ein Objekt, auf das das `this`\-Schlüsselwort in der `callbackfn`\-Funktion verweisen kann.  Wird `thisArg` nicht angegeben, wird `undefined` als `this`\-Wert verwendet.  
  
## Ausnahmen  
 Wenn es sich beim `callbackfn`\-Argument nicht um ein Funktionsobjekt handelt, wird eine `TypeError`\-Ausnahme ausgelöst.  
  
## Hinweise  
 Die Syntax der Rückruffunktion lautet wie folgt:  
  
 `function callbackfn(value, key, setObj)`  
  
 Sie können die Rückruffunktion deklarieren, indem Sie bis zu drei Parameter verwenden, wie in der folgenden Tabelle dargestellt.  
  
|Rückrufargument|Definition|  
|---------------------|----------------|  
|`value`|Ein im Satz enthaltener Wert.|  
|`key`|Ein im Satz enthaltener Wert.  Ein Satz hat keine Schlüssel, dieser Wert ist also der gleiche wie `value`.|  
|`setObj`|Das zu durchlaufende `Set`\-Objekt.|  
  
## Beispiel  
 Das folgende Beispiel veranschaulicht die Verwendung von `forEach`.  Das `callbackfn`\-Argument enthält den Code für die Rückruffunktion.  
  
```javascript  
var s = new Set();  
  
s.add("scale");  
s.add(10);  
s.add("5");  
  
s.forEach(function(item, sameItem, s) {  
    document.write("Size of the set object is: " + s.size + "<br />");  
    document.write("Deleting item: " + item + "<br />");  
    s.delete(sameItem);  
});  
  
// Output:  
// Size of the set object is: 3  
// Deleting item: scale  
// Size of the set object is: 2  
// Deleting item: 10  
// Size of the set object is: 1  
// Deleting item: 5  
```  
  
## Beispiel  
 Das folgende Beispiel zeigt, dass Sie Member aus einem Satz auch abrufen können, indem Sie der Rückruffunktion nur einen Parameter übergeben.  
  
```javascript  
var s = new Set();  
s.add("Thomas Jefferson");  
s.add(1776);  
s.add("founding father");  
  
s.forEach(function (item) {  
    document.write(item.toString() + ", ");  
});  
  
// Output:  
// Thomas Jefferson, 1776, founding father,  
  
```  
  
## Anforderungen  
 [!INCLUDE[jsv11](../../includes/jsv11-md.md)]