---
title: "Object.is-Funktion (JavaScript) | Microsoft Docs"
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
ms.assetid: 6e2f6c6d-7cd2-47c4-a513-3ba53988d27d
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# Object.is-Funktion (JavaScript)
Gibt einen Wert zurück, der angibt, ob zwei Werte den gleichen Wert besitzen.  
  
## Syntax  
  
```javascript  
Object.is(value1, value2)  
```  
  
#### Parameter  
 `value1`  
 Erforderlich.  Der erste zu testende Wert.  
  
 `value2`  
 Erforderlich.  Der zweite zu testende Wert.  
  
## Rückgabewert  
 `true`, wenn der Wert dem gleichen Wert entspricht; andernfalls `false`.  
  
## Hinweise  
 Im Gegensatz zu dem  \=\= Operator, erzwingt `Object.is` beim Testen von Werten keine Typen.  
  
 Der von `Object.is` angewendete Vergleich ähnelt dem vom \=\=\= Operator angewendeten Vergleich, außer dass `Object.is` `Number.isNaN` als den gleichen Wert wie `NaN`.  Es behandelt \+ 0 und \-0 ebenfalls als unterschiedliche Werte.  
  
## Anforderungen  
 [!INCLUDE[jsv12](../../includes/jsv12-md.md)]