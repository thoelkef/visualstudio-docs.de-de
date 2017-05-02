---
title: "join-Methode (Array) (JavaScript) | Microsoft Docs"
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
  - "join"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Join-Methode"
  - "Verketten von Zeichenfolgen, join-Methode"
  - "Arrays [Visual Studio], verknüpfen"
ms.assetid: 20f8fde1-014b-488e-9008-464a86e6b21f
caps.latest.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 16
---
# join-Methode (Array) (JavaScript)
Fügt alle Elemente eines Arrays hinzu, die von dem angegebenen Trennzeichen getrennt werden.  
  
## Syntax  
  
```  
  
arrayObj.join([separator])   
```  
  
## Parameter  
 `arrayObj`  
 Erforderlich.  Ein `Array`\-Objekt.  
  
 `separator`  
 Optional.  Ein Zeichenfolge, durch das die Elemente eines Arrays im resultierenden `String`\-Objekt getrennt werden.  Ohne diese Angabe werden die Arrayelemente mit einem Komma getrennt.  
  
## Hinweise  
 Hat ein Element des Arrays den Wert **undefined** oder `null`, wird es wie eine leere Zeichenfolge behandelt.  
  
## Beispiel  
 Das folgende Beispiel veranschaulicht die Verwendung der **join**\-Methode.  
  
```javascript  
var a, b;  
a = new Array(0,1,2,3,4);  
b = a.join("-");  
document.write(b);  
  
// Output:  
// 0-1-2-3-4  
  
```  
  
## Anforderungen  
 [!INCLUDE[jsv2](../../includes/jsv2-md.md)]  
  
## Siehe auch  
 [String\-Objekt](../../javascript/reference/string-object-javascript.md)