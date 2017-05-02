---
title: "Ung&#252;ltiger Bereich im Zeichensatz (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "javascript"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.WebClient.Help.SCRIPT5021"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: 971e9d5a-f88a-47a8-af94-f3c7c4aed5ab
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# Ung&#252;ltiger Bereich im Zeichensatz (JavaScript)
Sie haben versucht, einen regulären Ausdruck mit einem ungültigen Zeichensatzbereich zu erstellen.  Zeichensätze dürfen nur Bereiche aus einzelnen Zeichen enthalten, z. B. a bis z oder 0 bis 9; Zeichenklassen \(wie \\w\) dürfen nicht in einen Zeichensatz einbezogen werden.  Das erste Zeichen im Bereich muss vor dem zweiten Zeichen im Bereich stehen.  Beispiel:  
  
```javascript  
var good = /[a-z]/;     // A valid character range - a comes before z.  
var notGood = /[z-a]/;  // An invalid character range - z does not come before a.  
```  
  
### So beheben Sie diesen Fehler  
  
-   Verwenden Sie nur einzelne Zeichen, um den Zeichensatz für reguläre Ausdrücke zu erstellen, und stellen Sie sicher, dass sich die Zeichen in der richtigen Reihenfolge befinden.  
  
## Siehe auch  
 [Regular Expression\-Objekt](../../javascript/reference/regular-expression-object-javascript.md)   
 [Regular Expression Syntax \(JavaScript\)](http://msdn.microsoft.com/de-de/ab0766e1-7037-45ed-aa23-706f58358c0e)