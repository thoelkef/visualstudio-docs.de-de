---
title: "indexOf-Methode (Array) (JavaScript) | Microsoft Docs"
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
helpviewer_keywords: 
  - "Arrays [JavaScript], indexOf-Methode"
  - "indexOf-Methode [JavaScript]"
ms.assetid: 5bee31ae-aaf1-4466-8cfd-ed287e3cdf17
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# indexOf-Methode (Array) (JavaScript)
Gibt den Index des ersten Vorkommens eines Werts in einem Array zurück.  
  
## Syntax  
  
```  
  
array1.indexOf(searchElement[, fromIndex])  
```  
  
#### Parameter  
  
|Parameter|Definition|  
|---------------|----------------|  
|`array1`|Erforderlich.  Ein Arrayobjekt.|  
|`searchElement`|Erforderlich.  Der im `array1` zu suchende Wert.|  
|`fromIndex`|Optional.  Der Arrayindex, an der mit der Suche begonnen werden soll.  Wenn `fromIndex` nicht angegeben wird, beginnt die Suche bei Index 0.|  
  
## Rückgabewert  
 Der Index des ersten Vorkommens von `searchElement` im Array oder \-1, wenn `searchElement` nicht gefunden wird.  
  
## Hinweise  
 Die `indexOf`\-Methode durchsucht ein Array nach dem angegebenen Wert.  Die Methode gibt den Index des ersten Vorkommens oder \-1 zurück, wenn der angegebene Wert nicht gefunden wird.  
  
 Die Suche wird in aufsteigender Indexreihenfolge durchgeführt.  
  
 Die Arrayelemente werden mit dem `searchElement`\-Wert auf die strikte Gleichheit verglichen, ähnlich wie beim Einsatz des `===`\-Operators.  Weitere Informationen finden Sie unter [Vergleichsoperatoren](../../javascript/reference/comparison-operators-javascript.md).  
  
 Das optionale `fromIndex`\-Argument gibt den Arrayindex an, in dem die Suche starten soll.  Wenn `fromIndex` größer oder gleich der Arraylänge ist, wird \-1 zurückgegeben.  Wenn `fromIndex` negativ ist, startet die Suche bei Arraylänge plus `fromIndex`.  
  
## Beispiel  
 In den folgenden Beispielen wird die Verwendung der `indexOf`\-Methode veranschaulicht.  
  
```javascript  
// Create an array. (The elements start at index 0.)  
var ar = ["ab", "cd", "ef", "ab", "cd"];  
  
// Determine the first location of "cd".  
document.write(ar.indexOf("cd") + "<br/>");  
  
// Output: 1  
  
// Find "cd" starting at index 2.  
document.write(ar.indexOf("cd", 2) + "<br/>");  
  
// Output: 4  
  
// Find "gh" (which is not found).  
document.write (ar.indexOf("gh")+ "<br/>");  
  
// Output: -1  
  
// Find "ab" with a fromIndex argument of -2.  
// The search starts at index 3, which is the array length plus -2.  
document.write (ar.indexOf("ab", -2) + "<br/>");  
// Output: 3  
  
```  
  
## Anforderungen  
 [!INCLUDE[jsv9](../../includes/jsv9-md.md)]  
  
## Siehe auch  
 [JavaScript\-Methoden](../../javascript/reference/javascript-methods.md)   
 [Array\-Objekt](../../javascript/reference/array-object-javascript.md)   
 [Verwenden von Arrays](../../javascript/advanced/using-arrays-javascript.md)