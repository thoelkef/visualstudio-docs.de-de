---
title: "Eine Ausnahme wurde ausgel&#246;st, sie ist aber nicht aufgetreten | Microsoft Docs"
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
  - "VS.WebClient.Help.SCRIPT5022"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: b5235490-a8e7-42e3-804e-d85235bc6f05
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# Eine Ausnahme wurde ausgel&#246;st, sie ist aber nicht aufgetreten
Sie haben dem Code eine `throw`\-Anweisung hinzugefügt, die aber nicht in einen **try**\-Block eingeschlossen wurde, oder es ist kein zugehöriger **catch**\-Block vorhanden, um den Fehler abzufangen.  Ausnahmen werden im **try** \-Block mit der **throw** \-Anweisung ausgelöst und außerhalb des **try** \-Blocks mit einer **catch** \-Anweisung abgefangen.  
  
### So beheben Sie diesen Fehler  
  
-   Schließen Sie Code, der eine Ausnahme auslösen kann, in einen **try** \-Block ein, und stellen Sie sicher, dass ein zugehöriger **catch**\-Block vorhanden ist.  
  
-   Stellen Sie sicher, dass die catch\-Anweisung die korrekte Form von Ausnahme erwartet.  
  
-   Wenn die Ausnahme erneut ausgelöst wird, stellen Sie sicher, dass eine andere entsprechende catch\-Anweisung vorhanden ist.  
  
## Siehe auch  
 [Error\-Objekt](../../javascript/reference/error-object-javascript.md)   
 [throw\-Anweisung](../../javascript/reference/throw-statement-javascript.md)   
 [try...catch...finally\-Anweisung](../../javascript/reference/try-dot-dot-dot-catch-dot-dot-dot-finally-statement-javascript.md)