---
title: "charAt-Methode (String) (JavaScript) | Microsoft Docs"
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
  - "charAt"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "String-Objekt, Zurückgeben von Zeichen"
  - "charAt-Methode"
  - "Zeichen, Zurückgeben eines Teils"
ms.assetid: 63173e15-17f6-47c5-8f94-98ef1eb04c1a
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# charAt-Methode (String) (JavaScript)
Gibt das Zeichen im angegebenen Index zurück.  
  
## Syntax  
  
```  
  
strObj. charAt(index)  
```  
  
## Parameter  
 `strObj`  
 Erforderlich.  Ein `String`\-Objekt oder Zeichenfolgenliteral.  
  
 `index`  
 Erforderlich.  Der nullbasierte Index des gewünschten Zeichens.  
  
## Hinweise  
 Die `charAt`\-Methode gibt einen Zeichenwert zurück, der dem Zeichen am angegebenen `index` entspricht.  Das erste Zeichen in einer Zeichenfolge hat den Index 0, das zweite den Index 1 usw.  Bei Werten von `index`, die sich außerhalb des gültigen Bereichs befinden, wird eine leere Zeichenfolge zurückgegeben.  
  
## Beispiel  
 Im folgenden Beispiel wird die Verwendung der `charAt`\-Methode veranschaulicht:  
  
```javascript  
var str = "ABCDEFGHIJKLMNOPQRSTUVWXYZ";  
document.write(str.charAt(str.length - 1));  
  
// Output: Z  
  
```  
  
## Anforderungen  
 [!INCLUDE[jsv1](../../includes/jsv1-md.md)]  
  
 **Gilt für**: [String\-Objekt](../../javascript/reference/string-object-javascript.md)  
  
## Siehe auch  
 [String\-Objekt](../../javascript/reference/string-object-javascript.md)