---
title: "propertyIsEnumerable-Methode (Objekt) (JavaScript) | Microsoft Docs"
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
  - "propertyIsEnumerable"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "propertyIsEnumerable-Eigenschaft"
ms.assetid: d90c7c2e-ea23-4710-a957-9aefbbd1f68b
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# propertyIsEnumerable-Methode (Objekt) (JavaScript)
Bestimmt, ob eine angegebene Eigenschaft aufzählbar ist.  
  
## Syntax  
  
```  
  
object. propertyIsEnumerable(proName)  
```  
  
## Parameter  
 `object`  
 Erforderlich.  Instanz eines Objekts.  
  
 `proName`  
 Erforderlich.  Zeichenfolgenwert eines Eigenschaftsnamens.  
  
## Hinweise  
 Die `propertyIsEnumerable`\-Methode gibt `true` zurück, wenn `proName` in `object` vorhanden ist und mit einer `For`\-Schleife aufgelistet werden kann.  Die `propertyIsEnumerable`\-Methode gibt `false` zurück, wenn `object` keine Eigenschaft mit dem angegebenen Namen besitzt oder wenn die angegebene Eigenschaft nicht aufzählbar ist.  Normalerweise sind vordefinierte Eigenschaften nicht aufzählbar, wohingegen benutzerdefinierte Eigenschaften stets aufzählbar sind.  
  
 Die `propertyIsEnumerable`\-Methode berücksichtigt keine Objekte in der Prototypenkette.  
  
## Beispiel  
  
```javascript  
var a = new Array("apple", "banana", "cactus");  
document.write(a.propertyIsEnumerable(1));  
  
// Output: true  
  
```  
  
## Anforderungen  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## Siehe auch  
 [prototype\-Eigenschaft \(Objekt\)](../../javascript/reference/prototype-property-object-javascript.md)