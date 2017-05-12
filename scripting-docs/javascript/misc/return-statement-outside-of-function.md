---
title: "return-Anweisung ist au&#223;erhalb der Funktion | Microsoft Docs"
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
  - "VS.WebClient.Help.SCRIPT1018"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: 03568f9f-5f4f-4a10-a738-9a73f3832b9e
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# return-Anweisung ist au&#223;erhalb der Funktion
Sie haben eine `return`\-Anweisung im globalen Gültigkeitsbereich des Codes verwendet.  Die `return`\-Anweisung sollte nur innerhalb des Rumpfs einer Funktion auftreten.  
  
 Der Aufruf einer Funktion mit dem `()`\-Operator ist ein Ausdruck.  Jeder Ausdruck hat einen Wert; die `return`\-Anweisung wird verwendet, um den von einer Funktion zurückgegebenen Wert anzugeben.  Das allgemeine Format ist:  
  
```  
  
return [ expression ];  
```  
  
 Bei Ausführung der `return`\-Anweisung wird *expression* ausgewertet und als Wert der Funktion zurückgegeben.  Wenn kein Ausdruck vorhanden ist, wird **undefined** zurückgegeben.  
  
 Die Ausführung der Funktion wird beendet, wenn die `return`\-Anweisung ausgeführt wird, auch dann, wenn im Funktionsrumpf noch weitere Anweisungen vorhanden sind.  Zu dieser Regel besteht folgende Ausnahme: Wenn die **return**\-Anweisung in einem **try**\-Block auftritt und ein entsprechender **finally**\-Block vorhanden ist, wird der Code im **finally**\-Block ausgeführt, bevor die Funktion beendet wird.  
  
 Wenn eine Funktion zurückgegeben wird, da sie das Ende des Funktionsrumpfs erreicht, ohne eine `return`\-Anweisung auszuführen, ist der zurückgegebene Wert der **undefined**\-Wert \(das bedeutet, dass das Funktionsergebnis nicht als Teil eines größeren Ausdruck verwendet werden kann\).  
  
### So beheben Sie diesen Fehler  
  
-   Entfernen Sie die `return`\-Anweisung aus dem Haupttext des Codes \(dem globalen Gültigkeitsbereich\).  
  
## Siehe auch  
 [return\-Anweisung](../../javascript/reference/return-statement-javascript.md)   
 [Function\-Objekt](../../javascript/reference/function-object-javascript.md)   
 [caller\-Eigenschaft \(Funktion\)](../../javascript/reference/caller-property-function-javascript.md)