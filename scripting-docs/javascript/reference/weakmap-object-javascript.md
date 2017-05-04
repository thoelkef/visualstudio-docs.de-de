---
title: "WeakMap-Objekt (JavaScript) | Microsoft Docs"
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
  - "WeakMap"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: 4682d2dc-caf9-4fa8-8313-a0a0b804fd1d
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# WeakMap-Objekt (JavaScript)
Eine Auflistung von Schlüssel\-Wert\-Paaren, wobei jeder Schlüssel ein Objektverweis ist.  
  
## Syntax  
  
```  
weakmapObj = new WeakMap()  
```  
  
## Hinweise  
 Ein `WeakMap`\-Objekt kann nicht aufgelistet werden.  
  
 Wenn Sie einen Wert mithilfe eines vorhandenen Schlüssels zur Auflistung hinzufügen, ersetzt der neue Wert den alten Wert.  
  
 In einem `WeakMap`\-Objekt werden Schlüsselobjekte schwach referenziert.  Dies bedeutet, dass `WeakMap` die Ausführung einer Garbage Collection für die Schlüsselobjekte nicht verhindert.  Wenn \(außer `WeakMap`\) keine Verweise auf die Schlüsselobjekten vorhanden sind, kann der Garbage Collector die Schlüsselobjekte erfassen.  
  
## Eigenschaften  
 In der folgenden Tabelle werden die Eigenschaften des `WeakMap`\-Objekts aufgelistet.  
  
|Eigenschaft|Beschreibung|  
|-----------------|------------------|  
|[\-Konstruktor](../../javascript/reference/constructor-property-weakmap.md)|Gibt die Funktion an, durch die `WeakMap` erstellt wird.|  
|[prototype](../../javascript/reference/prototype-property-weakmap.md)|Gibt einen Verweis auf den Prototyp für `WeakMap` zurück.|  
  
## Methoden  
 In der folgenden Tabelle werden die Methoden des `WeakMap`\-Objekts aufgelistet.  
  
|Methode|Beschreibung|  
|-------------|------------------|  
|[clear](../../javascript/reference/clear-method-weakmap-javascript.md)|Entfernt alle Elemente aus einer `WeakMap`.|  
|[delete](../../javascript/reference/delete-method-weakmap-javascript.md)|Entfernt das angegebene Element aus `WeakMap`.|  
|[get](../../javascript/reference/get-method-weakmap-javascript.md)|Gibt ein angegebenes Element aus `WeakMap` zurück.|  
|[has](../../javascript/reference/has-method-weakmap-javascript.md)|Gibt `true` zurück, wenn `WeakMap` ein angegebenes Element enthält.|  
|[set](../../javascript/reference/set-method-weakmap-javascript.md)|Fügt `WeakMap` ein neues Element hinzu.|  
|[toString](../../javascript/reference/tostring-method-weakmap-javascript.md)|Gibt eine Zeichenfolgendarstellung von `WeakMap` zurück.|  
|[valueOf](../../javascript/reference/valueof-method-weakmap-javascript.md)|Gibt den einfachen Wert des angegebenen Objekts zurück.|  
  
## Beispiel  
 Im folgenden Beispiel wird gezeigt, wie Sie einem `WeakMap`\-Objekt Member hinzufügen und sie dann abrufen.  
  
```javascript  
var dog = {  
    breed: "yorkie"  
}  
  
var cat = {  
    breed: "burmese"  
}  
  
var wm = new WeakMap();  
wm.set(dog, "fido");  
wm.set(cat, "pepper");  
  
document.write(wm.get(dog) + ": ");  
document.write(dog.breed);  
document.write("<br />");  
document.write(wm.get(cat) + ": ");  
document.write(cat.breed);  
  
// Output:  
// fido: yorkie  
// pepper: burmese  
  
```  
  
## Anforderungen  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]