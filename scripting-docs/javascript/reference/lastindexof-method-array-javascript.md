---
title: "lastIndexOf-Methode (Array) (JavaScript) | Microsoft Docs"
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
  - "Arrays [JavaScript], lastIndexOf-Methode"
  - "lastIndexOf-Methode [JavaScript]"
ms.assetid: 04f5145d-007e-498f-b06f-11ab384c2968
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# lastIndexOf-Methode (Array) (JavaScript)
Gibt den Index des letzten Vorkommens eines angegebenen Werts in einem Array zurück.  
  
## Syntax  
  
```  
  
array1.lastIndexOf(searchElement[, fromIndex])  
```  
  
#### Parameter  
  
|Parameter|Definition|  
|---------------|----------------|  
|`array1`|Erforderlich.  Das Array\-Objekt, das durchsucht werden soll.|  
|`searchElement`|Erforderlich.  Der im `array1` zu suchende Wert.|  
|`fromIndex`|Optional.  Der Arrayindex, an der mit der Suche begonnen werden soll.  Wenn `fromIndex` ausgelassen wird, wird die Suche beim letzten Index im Array gestartet.|  
  
## Rückgabewert  
 Der Index des letzten Vorkommens von `searchElement` im Array oder \-1, wenn `searchElement` nicht gefunden wird.  
  
## Hinweise  
 Die `lastIndexOf`\-Methode durchsucht ein Array nach dem angegebenen Wert.  Die Methode gibt den Index des ersten Vorkommens oder \-1 zurück, wenn der angegebene Wert nicht gefunden wird.  
  
 Die Suche wird in absteigenden Indexreihenfolge durchgeführt \(letztes Member zuerst\).  Verwenden Sie [indexOf\-Methode \(Array\)](../../javascript/reference/indexof-method-array-javascript.md) für die Suche in aufsteigender Reihenfolge.  
  
 Die Arrayelemente werden mit dem `searchElement`\-Wert durch strikte Gleichheit verglichen, ähnlich wie der Vergleich durch den `===`\-Operator.  Weitere Informationen finden Sie unter [Vergleichsoperatoren](../../javascript/reference/comparison-operators-javascript.md).  
  
 Das optionale `fromIndex`\-Argument gibt den Arrayindex an, in dem die Suche starten soll.  Wenn `fromIndex` größer oder gleich der Arraylänge ist, wird das gesamte Array durchsucht.  Wenn `fromIndex` negativ ist, startet die Suche bei Arraylänge plus `fromIndex`.  Wenn der berechnete Index kleiner als 0 ist, wird \-1 zurückgegeben.  
  
## Beispiel  
 In den folgenden Beispielen wird die Verwendung der `lastIndexOf`\-Methode veranschaulicht.  
  
```javascript  
// Create an array.  
var ar = ["ab", "cd", "ef", "ab", "cd"];  
  
// Determine the first location, in descending order, of "cd".  
document.write(ar.lastIndexOf("cd") + "<br/>");  
  
// Output: 4  
  
// Find "cd" in descending order, starting at index 2.  
document.write(ar.lastIndexOf("cd", 2) + "<br/>");  
  
// Output: 1  
  
// Search for "gh" (which is not found).  
document.write(ar.lastIndexOf("gh")+ "<br/>");  
  
// Output: -1  
  
// Find "ab" with a fromIndex argument of -3.  
// The search in descending order starts at index 3,  
// which is the array length minus 2.  
document.write(ar.lastIndexOf("ab", -3) + "<br/>");  
// Output: 0  
  
```  
  
## Anforderungen  
 [!INCLUDE[jsv9](../../includes/jsv9-md.md)]  
  
## Siehe auch  
 [indexOf\-Methode \(Array\)](../../javascript/reference/indexof-method-array-javascript.md)   
 [Array\-Objekt](../../javascript/reference/array-object-javascript.md)   
 [Verwenden von Arrays](../../javascript/advanced/using-arrays-javascript.md)