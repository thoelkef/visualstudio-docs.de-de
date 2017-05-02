---
title: "Array.isArray-Funktion (JavaScript) | Microsoft Docs"
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
  - "Array.isArray-Funktion [JavaScript]"
  - "isArray-Funktion [JavaScript]"
ms.assetid: 58f7d2e0-d310-4292-b9bc-37a73c585780
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# Array.isArray-Funktion (JavaScript)
Bestimmt, ob ein Objekt ein Array ist.  
  
## Syntax  
  
```  
Array.isArray(object)   
```  
  
#### Parameter  
 `object`  
 Erforderlich.  Das zu überprüfende Objekt.  
  
## Rückgabewert  
 `true`, wenn `object` ein Array ist, andernfalls `false`.  Wenn das `object`\-Argument kein Objekt ist, wird `false` zurückgegeben.  
  
## Beispiel  
 Das folgende Beispiel veranschaulicht die Verwendung der `Array.isArray`\-Funktion.  
  
```javascript  
var ar = [];  
var result = Array.isArray(ar);  
// Output: true  
  
var ar = new Array();  
var result = Array.isArray(ar);  
// Output: true  
  
var ar = [1, 2, 3];  
var result = Array.isArray(ar);  
// Output: true  
  
var result = Array.isArray("an array");  
document.write(result);  
// Output: false  
```  
  
## Anforderungen  
 [!INCLUDE[jsv9](../../includes/jsv9-md.md)]  
  
## Siehe auch  
 [Array\-Objekt](../../javascript/reference/array-object-javascript.md)   
 [Verwenden von Arrays](../../javascript/advanced/using-arrays-javascript.md)   
 [typeof\-Operator](../../javascript/reference/typeof-operator-decrementjavascript.md)