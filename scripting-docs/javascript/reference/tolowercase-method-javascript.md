---
title: "toLowerCase-Methode (JavaScript) | Microsoft Docs"
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
  - "toLowerCase"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "toLowerCase-Methode"
ms.assetid: dfd543b9-3e7a-4f83-a391-9cde109ad6bc
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# toLowerCase-Methode (JavaScript)
Konvertiert alle alphabetischen Zeichen in einer Zeichenfolge in Kleinbuchstaben.  
  
## Syntax  
  
```  
  
        strVariable.toLowerCase()  
"String Literal".toLowerCase()   
```  
  
## Hinweise  
 Die `toLowerCase`\-Methode hat keine Auswirkungen auf nicht alphabetische Zeichen.  
  
 Das folgende Beispiel veranschaulicht die Auswirkungen der `toLowerCase`\-Methode:  
  
```javascript  
var str1 = "This is a STRING.";  
var str2 = str1. toLowerCase();  
document.write(str2);  
  
// Output: this is a string.  
  
```  
  
## Anforderungen  
 [!INCLUDE[jsv1](../../includes/jsv1-md.md)]  
  
 **Gilt für**: [String\-Objekt](../../javascript/reference/string-object-javascript.md)  
  
## Siehe auch  
 [toLocaleLowerCase\-Methode \(String\)](../../javascript/reference/tolocalelowercase-method-string-javascript.md)   
 [toUpperCase\-Methode \(String\)](../../javascript/reference/touppercase-method-string-javascript.md)