---
title: "shift-Methode (Array) (JavaScript) | Microsoft Docs"
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
  - "shift"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "shift-Methode"
ms.assetid: f33baec5-f67e-4760-b7c1-553727bd0423
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# shift-Methode (Array) (JavaScript)
Entfernt das erste Element aus einem Array und gibt es zurück.  
  
## Syntax  
  
```  
  
arrayObj.shift( )  
```  
  
#### Parameter  
 Der erforderliche `arrayObj`\-Verweis ist ein `Array`\-Objekt.  
  
## Rückgabewert  
 Gibt das Element zurück, das aus dem Array entfernt wurde.  
  
## Hinweise  
 Im folgenden Beispiel wird die Verwendung der `shift`\-Methode veranschaulicht.  
  
```javascript  
var arr = new Array(10, 11, 12);  
while (arr.length > 0)  
    {  
    var i = arr.shift();  
    document.write (i.toString() + " ");  
    }  
  
// Output:   
// 10 11 12  
```  
  
## Anforderungen  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## Siehe auch  
 [unshift\-Methode \(Array\)](../../javascript/reference/unshift-method-array-javascript.md)