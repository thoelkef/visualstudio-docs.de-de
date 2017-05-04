---
title: "splice-Methode (Array) (JavaScript) | Microsoft Docs"
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
  - "splice"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "splice-Methode"
ms.assetid: 85fdfb13-e3d9-4c89-b524-3ccee7001c93
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# splice-Methode (Array) (JavaScript)
Entfernt Elemente aus einem Array und fügt ggf. an ihrer Stelle neue Elemente ein, wobei die gelöschten Elemente zurückgegeben werden.  
  
## Syntax  
  
```  
  
arrayObj.splice(start, deleteCount, [item1[, item2[, . . . [,itemN]]]])  
```  
  
## Parameter  
 `arrayObj`  
 Erforderlich.  Ein `Array`\-Objekt.  
  
 `start`  
 Erforderlich.  Die nullbasierte Position im Array, an der mit dem Entfernen von Elementen begonnen werden soll.  
  
 `deleteCount`  
 Erforderlich.  Die Anzahl der zu entfernenden Elemente.  
  
 `item1, item2,. . ., itemN`  
 Optional.  Elemente, die statt der gelöschten Elemente in das Array eingefügt werden sollen.  
  
## Hinweise  
 Die `splice`\-Methode ändert das `arrayObj`, indem die angegebene Anzahl von Elementen ab der Position `start` entfernt und neue Elemente eingefügt werden.  Die gelöschten Elemente werden als neues `Array`\-Objekt zurückgegeben.  
  
## Beispiel  
 Im folgenden Code wird die Verwendung der `splice`\-Methode veranschaulicht.  
  
```javascript  
var arr = new Array("4", "11", "2", "10", "3", "1");  
arr.splice(2, 2, "21", "31");  
document.write(arr);  
  
// Output: 4,11,21,31,3,1  
  
```  
  
## Anforderungen  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## Siehe auch  
 [slice\-Methode \(Array\)](../../javascript/reference/slice-method-array-javascript.md)