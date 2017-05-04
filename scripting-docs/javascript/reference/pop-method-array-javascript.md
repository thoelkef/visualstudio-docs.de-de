---
title: "pop-Methode (Array) (JavaScript) | Microsoft Docs"
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
  - "pop"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Pop-Methode"
ms.assetid: 4fae7f98-29f1-4041-ba43-601f2e5145ec
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# pop-Methode (Array) (JavaScript)
Entfernt das letzte Element aus einem Array und gibt dieses zurück.  
  
## Syntax  
  
```  
  
arrayObj.pop( )  
```  
  
## Hinweise  
 Die [push](../../javascript/reference/push-method-array-javascript.md)\-Methode und die `pop`\-Methode ermöglichen es Ihnen, einen Stapel zu simulieren, für den beim Speichern von Daten das LIFO\-Prinzip \(Last In, First Out\) verwendet wird.  
  
 Der erforderliche `arrayObj`\-Verweis ist ein `Array`\-Objekt.  
  
 Wenn das Array leer ist, wird `undefined` zurückgegeben.  
  
## Beispiel  
 Im folgenden Beispiel wird die Verwendung der `pop`\-Methode veranschaulicht.  
  
```javascript  
var number;  
var my_array = new Array();  
  
my_array.push (5, 6, 7);  
my_array.push (8, 9);  
  
number = my_array.pop();  
while (number != undefined)  
   {  
   document.write (number + " ");  
   number = my_array.pop();  
   }  
  
// Output: 9 8 7 6 5  
```  
  
## Anforderungen  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## Siehe auch  
 [push\-Methode \(Array\)](../../javascript/reference/push-method-array-javascript.md)