---
title: "fill-Methode (Array) (JavaScript) | Microsoft Docs"
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
ms.assetid: 11526627-c0bb-4157-a8c4-0a039079b4a1
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# fill-Methode (Array) (JavaScript)
Füllt ein Array mit einem angegebenen Wert.  
  
## Syntax  
  
```  
arrayObj.fill(value [ , start [ , end ] ]);  
```  
  
#### Parameter  
 `arrayObj`  
 Erforderlich.  Das Arrayobjekt.  
  
 `value`  
 Erforderlich.  Der zum Füllen des Arrays verwendete Wert.  
  
 `start`  
 Optional.  Der zum Füllen von Arraywerten verwendete Startindex.  Der Standardwert ist 0.  
  
 `end`  
 Optional.  Der zum Füllen von Arraywerten verwendete Endindex.  Der Standardwert ist die Length\-Eigenschaft des `this`\-Objekts.  
  
## Hinweise  
 Wenn `start` negativ ist, wird `start` als `length`\+`start` behandelt, wobei `length` die Länge des Arrays angibt.  Wenn `end` negativ ist, wird `end` als `length`\+`end` behandelt.  
  
## Beispiel  
 Die folgenden Codebeispiele füllen ein Array mit Werten.  
  
```javascript  
[0, 0, 0].fill(7, 1);  
// Array contains [0,7,7]  
  
[0, 0, 0].fill(7);  
// Array contains [7,7,7]  
  
```  
  
## Anforderungen  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]