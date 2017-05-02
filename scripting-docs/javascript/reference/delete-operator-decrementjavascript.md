---
title: "delete-Operator (JavaScript) | Microsoft Docs"
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
  - "delete_JavaScriptKeyword"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Arrayelemente, löschen"
  - "Eigenschaften, löschen"
  - "delete-Operator"
ms.assetid: 55c6487e-96ea-455b-a7ed-dc35c41ac2f3
caps.latest.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 16
---
# delete-Operator (JavaScript)
Löscht eine Eigenschaft aus einem Objekt oder entfernt ein Element aus einem Array.  
  
## Syntax  
  
```  
delete expression  
```  
  
## Hinweise  
 Das `expression`\-Argument ist ein gültiger [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] Ausdruck, der normalerweise einen Eigenschaftennamen oder ein Arrayelement ergibt.  
  
 Wenn das Ergebnis von `expression` ein Objekt ist, die in `expression` angegebene Eigenschaft existiert und das Objekt nicht zulässt, diese zu löschen, wird `false` zurückgegeben.  
  
 In allen anderen Fällen wird `true` zurückgegeben.  
  
## Beispiel  
 Im folgenden Beispiel wird veranschaulicht, wie ein Element aus einem Array entfernt wird.  
  
```javascript  
// Create an array.  
var ar = new Array (10, 11, 12, 13, 14);  
  
// Remove an element from the array.  
delete ar[1];  
  
// Print the results.  
document.write ("element 1: " + ar[1]);  
document.write ("<br />");  
document.write ("array: " + ar);  
// Output:  
//  element 1: undefined  
//  array: 10,,12,13,14  
```  
  
## Beispiel  
 Im folgenden Beispiel wird das Löschen einer Eigenschaft aus einem Objekt veranschaulicht.  
  
```javascript  
// Create an object and add expando properties.  
var myObj = new Object();  
myObj.name = "Fred";  
myObj.count = 42;  
  
// Delete the properties from the object.  
delete myObj.name;  
delete myObj["count"];  
  
// Print the results.  
document.write ("name: " + myObj.name);  
document.write ("<br />");  
document.write ("count: " + myObj.count);  
// Output:  
//  name: undefined  
//  count: undefined  
```  
  
## Anforderungen  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
## Siehe auch  
 [Operatorrangfolge](../../javascript/operator-subtractprecedence-javascript.md)   
 [Zusammenfassung der Operatoren \(JavaScript\)](../../javascript/misc/operator-subtractsummary-javascript.md)