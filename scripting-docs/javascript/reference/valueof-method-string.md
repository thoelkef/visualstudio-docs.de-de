---
title: "valueOf-Methode (String) | Microsoft Docs"
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
ms.assetid: dfb55e6b-e38f-4b49-8196-9693f87126a4
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# valueOf-Methode (String)
Gibt die Zeichenfolge zurück.  
  
## Syntax  
  
```  
  
string.valueOf()  
```  
  
#### Parameter  
 Diese Methode hat keine Parameter.  
  
## Rückgabewert  
 Gibt den Zeichenfolgenwert zurück.  
  
## Hinweise  
 Im folgenden Beispiel ist das Zeichenfolgenobjekt das selbe wie der Rückgabewert.  
  
```javascript  
var str = "every good boy does fine";  
var strStr = str.valueOf();  
  
if (str === strStr)  
document.write("same");  
else  
document.write("different");  
  
// Output:  
// same  
  
```  
  
## Anforderungen  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]