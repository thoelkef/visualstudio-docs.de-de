---
title: "Math.log-Funktion (JavaScript) | Microsoft Docs"
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
  - "log"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "log-Methode"
  - "Math-Objekt"
ms.assetid: 5d617fb5-4b27-404e-842f-eea5549a7c1a
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# Math.log-Funktion (JavaScript)
Gibt den natürlichen Logarithmus \(zur Basis `e`\) der angegebenen Zahl zurück.  
  
## Syntax  
  
```  
Math.log(number)   
```  
  
#### Parameter  
 number  
 Eine Zahl.  
  
## Rückgabewert  
 Wenn `number` positiv ist, gibt diese Funktion den natürliche Logarithmus der Zahl zurück.  Wenn `number` negativ ist, gibt diese Funktion `NaN` zurück.  Wenn `number` 0 ist, gibt diese Funktion `-Infinity` zurück.  
  
## Beispiel  
 Der folgende Code veranschaulicht die Verwendung dieser Funktion.  
  
```javascript  
var numArr = [ 45.3, 69.0, 557.04, 0.222 ];  
  
for (i in numArr) {  
    document.write(Math.log(numArr[i]));  
    document.write("<br/>");  
}  
  
// Output:   
// 3.8133070324889884  
// 4.23410650459726  
// 6.322637050634291  
// -1.5050778971098575  
  
```  
  
## Anforderungen  
 [!INCLUDE[jsv1](../../includes/jsv1-md.md)]  
  
 **Gilt für**: [Math\-Objekt](../../javascript/reference/math-object-javascript.md)  
  
## Siehe auch  
 [Math.sqrt\-Funktion](../../javascript/reference/math-sqrt-function-javascript.md)