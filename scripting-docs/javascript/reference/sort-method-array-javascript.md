---
title: "sort-Methode (Array) (JavaScript) | Microsoft Docs"
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
  - "sort"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Sort-Methode"
ms.assetid: 9bd8b54a-c838-4806-85c8-62eebe6bc48c
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# sort-Methode (Array) (JavaScript)
Sortiert ein `Array`.  
  
## Syntax  
  
```  
  
arrayobj.sort(sortFunction)   
```  
  
## Parameter  
 `arrayObj`  
 Erforderlich.  Ein `Array`\-Objekt.  
  
 `sortFunction`  
 Dies ist optional.  Der Name der Funktion zur Bestimmung der Reihenfolge der Elemente.  Wenn die Angabe ausgelassen wird, werden die Elemente aufsteigend in ASCII\-Zeichenreihenfolge sortiert.  
  
## Rückgabewert  
 Das sortierte Array.  
  
## Hinweise  
 Die `sort`\-Methode sortiert innerhalb des `Array`\-Objekts. Während der Ausführung wird kein neues `Array`\-Objekt erstellt.  
  
 Wenn Sie eine Funktion im `sortFunction`\-Argument angeben, muss diese einen der folgenden Werte zurückgeben:  
  
-   Einen negativen Wert, wenn das erste übergebene Argument kleiner als das zweite ist.  
  
-   Null, wenn beide Argumente gleichwertig sind.  
  
-   Einen positiven Wert, wenn das erste Argument größer als das zweite ist.  
  
## Beispiel  
 Im folgenden Beispiel wird die Verwendung der `sort`\-Methode gezeigt.  
  
```javascript  
var a = new Array(4, 11, 2, 10, 3, 1);  
  
var b = a.sort();  
document.write(b);  
document.write("<br/>");  
  
// This is ASCII character order.  
// Output: 1,10,11,2,3,4)  
  
// Sort the array elements with a function that compares array elements.  
b = a.sort(CompareForSort);  
document.write(b);  
document.write("<br/>");  
// Output: 1,2,3,4,10,11.  
  
// Sorts array elements in ascending order numerically.  
function CompareForSort(first, second)  
{  
    if (first == second)  
        return 0;  
    if (first < second)  
        return -1;  
    else  
        return 1;   
}  
```  
  
## Anforderungen  
 [!INCLUDE[jsv2](../../includes/jsv2-md.md)]