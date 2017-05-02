---
title: "push-Methode (Array) (JavaScript) | Microsoft Docs"
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
  - "push"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Push-Methode"
ms.assetid: fa6e5799-dabe-4b3d-bd1f-0afc68c77134
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# push-Methode (Array) (JavaScript)
Fügt neue Elemente an ein Array an und gibt die neue Länge des Arrays zurück.  
  
## Syntax  
  
```  
  
arrayObj.push([item1 [item2 [. . . [itemN ]]]])  
```  
  
## Parameter  
 `arrayObj`  
 Erforderlich.  Ein `Array`\-Objekt.  
  
 `item, item2,. . ., itemN`  
 Optional.  Neue Elemente von dem `Array`.  
  
## Hinweise  
 Die `push`\-Methode und die `pop`\-Methode ermöglichen Ihnen, einen LIFO\-Stack \(last in, first out\) zu simulieren.  
  
 Die `push`\-Methode fügt Elemente in der Reihenfolge hinzu, in der sie auftreten.  Wenn eines der Argumente ein Array ist, wird es als einzelnes Element hinzugefügt.  Mit der `concat`\-Methode können Sie Elemente von zwei oder mehr Arrays verknüpfen.  
  
## Beispiel  
 Im folgenden Beispiel wird die Verwendung der `push`\-Methode veranschaulicht.  
  
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
  
// Output:  
// 9 8 7 6 5  
```  
  
## Anforderungen  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## Siehe auch  
 [concat\-Methode \(Array\)](../../javascript/reference/concat-method-array-javascript.md)   
 [pop\-Methode \(Array\)](../../javascript/reference/pop-method-array-javascript.md)