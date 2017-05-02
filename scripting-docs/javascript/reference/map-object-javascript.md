---
title: "Map-Objekt (JavaScript) | Microsoft Docs"
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
  - "Map"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: a91dbcbe-f58d-41a0-be15-8c9d30020327
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# Map-Objekt (JavaScript)
Eine Auflistung von Schlüssel\-Wert\-Paaren.  
  
## Syntax  
  
```javascript  
mapObj = new Map()  
```  
  
## Hinweise  
 Die Schlüssel und Werte in der Auflistung können eines beliebigen Typs sein.  Wenn Sie einen Wert mithilfe eines vorhandenen Schlüssels zur Auflistung hinzufügen, ersetzt der neue Wert den alten Wert.  
  
## Eigenschaften  
 In der folgenden Tabelle werden die Eigenschaften des `Map`\-Objekts aufgelistet.  
  
|Eigenschaft|Beschreibung|  
|-----------------|------------------|  
|[\-Konstruktor](../../javascript/reference/constructor-property-map.md)|Gibt die Funktion an, durch die eine Zuordnung erstellt wird.|  
|[prototype](../../javascript/reference/prototype-property-map.md)|Gibt einen Verweis auf den Prototyp für eine Zuordnung zurück.|  
|[size](../../javascript/reference/size-property-map-javascript.md)|Gibt die Anzahl der Elemente in einer Zuordnung zurück.|  
  
## Methoden  
 In der folgenden Tabelle werden die Methoden des `Map`\-Objekts aufgelistet.  
  
|Methode|Beschreibung|  
|-------------|------------------|  
|[clear](../../javascript/reference/clear-method-map-javascript.md)|Entfernt alle Elemente aus einer Zuordnung.|  
|[delete](../../javascript/reference/delete-method-map-javascript.md)|Entfernt ein angegebenes Element aus einer Zuordnung.|  
|[forEach](../../javascript/reference/foreach-method-map-javascript.md)|Führt die angegebene Aktion für jedes Element in einer Zuordnung aus.|  
|[get](../../javascript/reference/get-method-map-javascript.md)|Gibt ein angegebenes Element aus einer Zuordnung zurück.|  
|[has](../../javascript/reference/has-method-map-javascript.md)|Gibt `true` zurück, wenn die Zuordnung ein angegebenes Element enthält.|  
|[set](../../javascript/reference/set-method-map-javascript.md)|Fügt einer Zuordnung ein neues Element hinzu.|  
|[toString](../../javascript/reference/tostring-method-map-javascript.md)|Gibt eine Zeichenfolgendarstellung einer Zuordnung zurück.|  
|[valueOf](../../javascript/reference/valueof-method-map-javascript.md)|Gibt den einfachen Wert des angegebenen Objekts zurück.|  
  
## Beispiel  
 Im folgenden Beispiel wird gezeigt, wie Sie einer `Map` Member hinzufügen und sie dann abrufen.  
  
```javascript  
var m = new Map();  
m.set(1, "black");  
m.set(2, "red");  
m.set("colors", 2);  
m.set({x:1}, 3);  
  
m.forEach(function (item, key, mapObj) {  
    document.write(item.toString() + "<br />");  
});  
  
document.write("<br />");  
document.write(m.get(2));  
  
// Output:  
// black  
// red  
// 2  
// 3  
//  
// red  
  
```  
  
## Anforderungen  
 [!INCLUDE[jsv11](../../includes/jsv11-md.md)]