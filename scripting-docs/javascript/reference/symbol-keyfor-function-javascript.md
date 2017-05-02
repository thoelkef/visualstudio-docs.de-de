---
title: "Symbol.keyFor-Funktion (JavaScript) | Microsoft Docs"
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
ms.assetid: f0b6f034-6d0a-421c-b1c6-52489411e9a3
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# Symbol.keyFor-Funktion (JavaScript)
Gibt den Schlüssel eines angegebenen Symbols zurück.  
  
## Syntax  
  
```vb  
Symbol.keyFor(sym);  
```  
  
#### Parameter  
 `sym`  
 Erforderlich.  Das Symbolobjekt.  
  
## Hinweise  
 Diese Methode sucht das Symbol in der globalen Symbolregistrierung.  
  
## Beispiel  
  
```javascript  
// Local symbol  
var sym1 = Symbol("desc");  
// Global symbol  
var sym2 = Symbol.for("desc");  
  
console.log(Symbol.keyFor(sym1)):  
console.log(Symbol.keyFor(sym2));  
  
// Output:  
// undefined  
// desc  
```  
  
## Anforderungen  
 [!INCLUDE[jsv12](../../includes/jsv12-md.md)]