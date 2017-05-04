---
title: "parseFloat-Funktion (JavaScript) | Microsoft Docs"
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
  - "parseFloat"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "parseFloat-Methode"
ms.assetid: a7d87a69-1919-4623-be85-972e6376dd2d
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# parseFloat-Funktion (JavaScript)
Konvertiert eine Zeichenfolge in eine Gleitkommazahl.  
  
## Syntax  
  
```  
parseFloat(numString)   
```  
  
## Hinweise  
 Das erforderliche `numString`\-Argument ist eine Zeichenfolge, die eine Gleitkommazahl enthält.  
  
 Die `parseFloat`\-Funktion gibt einen numerischen Wert gleich der Zahl zurück, die in `numString` enthalten ist.  Falls kein Präfix von `numString` erfolgreich in eine Gleitkommazahl umgewandelt werden kann, wird `NaN` \(Not a Number\) zurückgegeben.  
  
```javascript  
parseFloat("abc")      // Returns NaN.  
parseFloat("1.2abc")   // Returns 1.2.  
```  
  
 Eine Überprüfung auf `NaN` können Sie mit der `isNaN`\-Funktion durchführen.  
  
## Anforderungen  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Gilt für**: [Global\-Objekt](../../javascript/reference/global-object-javascript.md)  
  
## Siehe auch  
 [isNaN\-Funktion](../../javascript/reference/isnan-function-javascript.md)   
 [parseInt\-Funktion](../../javascript/reference/parseint-function-javascript.md)   
 [String\-Objekt](../../javascript/reference/string-object-javascript.md)