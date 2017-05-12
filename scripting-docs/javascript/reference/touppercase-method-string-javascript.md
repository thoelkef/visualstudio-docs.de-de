---
title: "toUpperCase-Methode (String) (JavaScript) | Microsoft Docs"
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
  - "toUpperCase"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "toUpperCase-Methode"
ms.assetid: 4fd4ccc3-e794-498a-9db1-baf48fc1dda1
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# toUpperCase-Methode (String) (JavaScript)
Konvertiert alle alphabetischen Zeichen in einer Zeichenfolge in Großbuchstaben.  
  
## Syntax  
  
```  
  
        strVariable.toUpperCase()  
"String Literal".toUpperCase()   
```  
  
## Hinweise  
 Die `toUpperCase`\-Methode hat keine Auswirkungen auf nicht alphabetische Zeichen.  
  
## Beispiel  
 Das folgende Beispiel veranschaulicht die Auswirkungen der `toUpperCase`\-Methode:  
  
```javascript  
var str1 = "This is a STRING.";  
var str2 = str1.toUpperCase();  
document.write(str2);  
  
// Output: THIS IS A STRING.  
  
```  
  
## Anforderungen  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Gilt für**: [String\-Objekt](../../javascript/reference/string-object-javascript.md)  
  
## Siehe auch  
 [toLocaleUpperCase\-Methode \(String\)](../../javascript/reference/tolocaleuppercase-method-string-javascript.md)   
 [toLowerCase\-Methode](../../javascript/reference/tolowercase-method-javascript.md)