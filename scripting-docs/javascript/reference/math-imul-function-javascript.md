---
title: "Math.imul-Funktion (JavaScript) | Microsoft Docs"
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
ms.assetid: dce5e11c-36b9-4c39-84d3-6cd494dd1cbf
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# Math.imul-Funktion (JavaScript)
Gibt das Produkt zweier Zahlen zurück, die als 32\-Bit\-Ganzzahlen mit Vorzeichen behandelt werden.  
  
## Syntax  
  
```  
Math.imul(x, y);  
```  
  
#### Parameter  
 `x`  
 Erforderlich.  Die erste Zahl.  
  
 `y`  
 Erforderlich.  Die zweite Zahl.  
  
## Hinweise  
 Diese Funktion wird für Compiler wie Emscripten und Mandreel verwendet, die die Multiplikation von ganzen Zahlen auf andere Weise implementieren als JavaScript.  
  
## Beispiel  
 Im folgenden Codebeispiel wird die Multiplikation von Zahlen mit `Math.imul` veranschaulicht.  
  
```javascript  
var result1 = Math.imul(2, 5);  
// result1 == 10  
  
var result2 = Math.imul(Math.pow(2, 32) - 1, Math.pow(2, 32) - 2);  
// result2 == 2  
  
```  
  
## Anforderungen  
 [!INCLUDE[jsv12](../../includes/jsv12-md.md)]