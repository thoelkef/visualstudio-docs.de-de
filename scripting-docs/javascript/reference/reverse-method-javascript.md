---
title: "reverse-Methode (JavaScript) | Microsoft Docs"
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
  - "reverse"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Arrays [Visual Studio], Umkehren von Elementen"
  - "reverse-Methode"
  - "Vertauschen von Elementen"
ms.assetid: 02ab051b-79b8-4646-b502-381671e78c12
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# reverse-Methode (JavaScript)
Kehrt die Elemente in ein `Array` um.  
  
## Syntax  
  
```  
  
arrayObj.reverse()   
```  
  
## Parameter  
 `arrayObj`  
 Erforderlich.  Ein `Array`\-Objekt.  
  
## Rückgabewert  
 Das umgekehrte Array.  
  
## Hinweise  
 Der erforderliche `arrayObj`\-Verweis ist ein `Array`\-Objekt.  
  
 Mit der `reverse`\-Methode kann die Reihenfolge der Elemente eines `Array`\-Objekts umgekehrt werden.  Bei der Ausführung der Methode wird kein neues `Array`\-Objekt erstellt.  
  
 Ist das Array nicht zusammenhängend, werden durch die `reverse`\-Methode Elemente erstellt, die die Lücken im Array füllen.  Jedes dieser so erstellten Elemente hat den Wert `undefined`.  
  
## Beispiel  
 Im folgenden Beispiel wird die Verwendung der `reverse`\-Methode veranschaulicht.  
  
```javascript  
var arr = new Array(0,1,2,3,4);   
var reverseArr = arr.reverse();  
document.write(reverseArr);  
  
// Output:  
// 4,3,2,1,0  
  
```  
  
## Anforderungen  
 [!INCLUDE[jsv2](../../includes/jsv2-md.md)]  
  
## Siehe auch  
 [concat\-Methode \(Array\)](../../javascript/reference/concat-method-array-javascript.md)