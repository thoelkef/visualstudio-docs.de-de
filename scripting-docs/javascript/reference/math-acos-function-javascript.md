---
title: "Math.acos-Funktion (JavaScript) | Microsoft Docs"
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
  - "acos"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "acos-Methode"
  - "arcosine-Methode"
ms.assetid: 828cb3c3-bdf7-4bb7-97ae-3617ce4b2d62
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# Math.acos-Funktion (JavaScript)
Gibt den Arkuskosinus einer Zahl zurück.  
  
## Syntax  
  
```  
Math.acos(number)  
```  
  
#### Parameter  
 Das erforderliche `number`\-Argument ist ein numerischer Ausdruck.  
  
## Rückgabewert  
 Der Arkuskosinus des `number`\-Arguments, im Bogenmaß.  
  
## Beispiel  
 Der folgende Code veranschaulicht die Verwendung der `acos`\-Funktion.  
  
```javascript  
var v1 = Math.acos(-1.0);  
var v2 = Math.cos(-1.0);  
  
document.write(v1);  
document.write("<br/>");  
document.write(v2);  
  
// Output:  
// 3.141592653589793  
// 0.5403023058681398  
  
```  
  
## Hinweise  
 **Gilt für**: [Math\-Objekt](../../javascript/reference/math-object-javascript.md)  
  
## Anforderungen  
 [!INCLUDE[jsv1](../../includes/jsv1-md.md)]  
  
## Siehe auch  
 [Math.asin\-Funktion](../../javascript/reference/math-asin-function-javascript.md)   
 [Math.atan\-Funktion](../../javascript/reference/math-atan-function-javascript.md)   
 [Math.cos\-Funktion](../../javascript/reference/math-cos-function-javascript.md)   
 [Math.sin\-Funktion](../../javascript/reference/math-sin-function-javascript.md)   
 [Math.tan\-Funktion](../../javascript/reference/math-tan-function-javascript.md)   
 [Math\-Objekt](../../javascript/reference/math-object-javascript.md)