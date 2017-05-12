---
title: "charCodeAt-Methode (String) (JavaScript) | Microsoft Docs"
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
  - "charCodeAt"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "charCodeAt-Methode"
ms.assetid: 5b0290a7-ee4d-4738-a909-c02ef64a2f1a
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# charCodeAt-Methode (String) (JavaScript)
Gibt den Unicode\-Wert des Zeichens an der angegebenen Position zurück.  
  
## Syntax  
  
```  
  
strObj. charCodeAt(index)  
```  
  
## Parameter  
 `strObj`  
 Erforderlich.  Ein `String`\-Objekt oder Zeichenfolgenliteral.  
  
 `index`  
 Erforderlich.  Der nullbasierte Index des gewünschten Zeichens.  Wenn sich am angegebenen Index kein Zeichen befindet, wird `NaN` zurückgegeben.  
  
## Hinweise  
  
## Beispiel  
 Im folgenden Beispiel wird die Verwendung der `charCodeAt`\-Methode veranschaulicht.  
  
```javascript  
var str = "ABCDEFGHIJKLMNOPQRSTUVWXYZ";   
document.write(str.charCodeAt(str.length - 1));  
  
// Output: 90   
```  
  
## Anforderungen  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## Siehe auch  
 [String.fromCharCode\-Funktion](../../javascript/reference/string-fromcharcode-function-javascript.md)