---
title: "Set-Objekt (JavaScript) | Microsoft Docs"
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
  - "Set"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: 4a4dd749-2a76-44fb-9cb0-a3ef317f75fb
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# Set-Objekt (JavaScript)
Eine Auflistung eindeutiger Werte eines beliebigen Typs.  
  
## Syntax  
  
```  
setObj = new Set()  
  
```  
  
## Hinweise  
 Wenn Sie versuchen, einen nicht eindeutigen Wert zu `Set` hinzuzufügen, wird der neue Wert der Auflistung nicht hinzugefügt.  
  
## Eigenschaften  
 In der folgenden Tabelle werden die Eigenschaften des `Set`\-Objekts aufgelistet.  
  
|Eigenschaft|Beschreibung|  
|-----------------|------------------|  
|[\-Konstruktor](../../javascript/reference/constructor-property-set.md)|Gibt die Funktion an, durch die ein Satz erstellt wird.|  
|[prototype](../../javascript/reference/prototype-property-set.md)|Gibt einen Verweis auf den Prototyp für einen Satz zurück.|  
|[size](../../javascript/reference/size-property-set-javascript.md)|Gibt die Anzahl der Elemente in einem Satz zurück.|  
  
## Methoden  
 In der folgenden Tabelle werden die Methoden des `Set`\-Objekts aufgelistet.  
  
|Methode|Beschreibung|  
|-------------|------------------|  
|[add](../../javascript/reference/add-method-set-javascript.md)|Fügt einem Satz ein Element hinzu.|  
|[clear](../../javascript/reference/clear-method-set-javascript.md)|Entfernt alle Elemente aus einem Satz.|  
|[delete](../../javascript/reference/delete-method-set-javascript.md)|Entfernt ein angegebenes Element aus einem Satz.|  
|[forEach](../../javascript/reference/foreach-method-set-javascript.md)|Führt die angegebene Aktion für jedes Element in einem Satz aus.|  
|[has](../../javascript/reference/has-method-set-javascript.md)|Gibt `true` zurück, wenn der Satz ein angegebenes Element enthält.|  
|[toString](../../javascript/reference/tostring-method-set-javascript.md)|Gibt eine Zeichenfolgendarstellung eines Satzes zurück.|  
|[valueOf](../../javascript/reference/valueof-method-set-javascript.md)|Gibt den einfachen Wert des angegebenen Objekts zurück.|  
  
## Beispiel  
 Im folgenden Beispiel wird gezeigt, wie Sie einem Satz Member hinzufügen und sie dann abrufen.  
  
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