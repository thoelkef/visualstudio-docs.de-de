---
title: "in-Operator (JavaScript) | Microsoft Docs"
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
  - "in_JavaScriptKeyword"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "in-Operator"
ms.assetid: dcd8f901-96b8-4c91-848b-b1ec0ab1c11c
caps.latest.revision: 17
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 17
---
# in-Operator (JavaScript)
Überprüft, ob eine Eigenschaft in einem Objekt vorhanden ist.  
  
## Syntax  
  
```  
  
result = property in object  
```  
  
## Parameter  
 `result`  
 Erforderlich.  Beliebige Variable.  
  
 `property`  
 Erforderlich.  Ein Ausdruck, der als Zeichenfolgenausdruck ausgewertet wird.  
  
 `object`  
 Erforderlich.  Ein beliebiges Objekt.  
  
## Hinweise  
 Der Operator `in` prüft, ob ein Objekt über eine Eigenschaft mit dem Namen `property` verfügt.  Sie bestimmt auch, ob die Eigenschaft Teil der Prototypenkette des Objekts ist.  Weitere Informationen zu Objektprototypen finden Sie unter [Prototypen und Prototypvererbung](../../javascript/advanced/prototypes-and-prototype-inheritance.md).  
  
## Beispiel  
 Im folgenden Beispiel wird die Verwendung des `in`\-Operators gezeigt:  
  
```javascript  
// Create an object that has some properties.  
var myObject = new Object();  
myObject.name = "James";  
myObject.age = "22";  
myObject.phone = "555 0234";  
  
if ("phone" in myObject)  
   document.write ("property is present");  
else  
   document.write ("property is not present");  
  
// Output: property is present  
```  
  
## Anforderungen  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## Siehe auch  
 [Operatorrangfolge](../../javascript/operator-subtractprecedence-javascript.md)   
 [Zusammenfassung der Operatoren \(JavaScript\)](../../javascript/misc/operator-subtractsummary-javascript.md)