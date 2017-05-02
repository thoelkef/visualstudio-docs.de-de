---
title: "Array.of-Funktion (Array) (JavaScript) | Microsoft Docs"
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
ms.assetid: 2884dda3-65d1-4990-9afe-87865c2d4f7f
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# Array.of-Funktion (Array) (JavaScript)
Gibt ein Array aus den übergebenen Argumenten zurück.  
  
## Syntax  
  
```  
Array.of(element0[, element1][, ...][,elementN]);  
```  
  
#### Parameter  
 `element0,...,elementN`  
 Optional.  Die im Array zu platzierenden Elemente.  Es wird ein Array mit n \+ 1 Elementen und einer Länge von n \+ 1 erstellt.  
  
## Hinweise  
 Diese Funktion ist vergleichbar mit einem Aufruf von `new Array(args)`, jedoch weist `Array.of` kein besonderes Verhalten auf, wenn ein Argument übergeben wird.  
  
## Beispiel  
 Im folgenden Beispiel wird ein Array aus übergebenen Zahlen erstellt.  
  
```javascript  
var arr = Array.of(1, 2, 3);  
// arr[0] == 1  
  
```  
  
## Beispiel  
 Das folgende Beispiel zeigt den Unterschied zwischen der Verwendung von `Array.of` und `new Array`.  
  
```javascript  
var arr1 = Array.of(3);  
// arr1[0] == 3  
  
// With new Array, a single argument specifies  
// the length of the new array.  
var arr2 = new Array(3);  
// arr2[0] is undefined  
// arr2.length == 3  
  
```  
  
## Anforderungen  
 [!INCLUDE[jsv12](../../includes/jsv12-md.md)]