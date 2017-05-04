---
title: "&quot;catch&quot; erwartet | Microsoft Docs"
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
  - "VS.WebClient.Help.SCRIPT1033"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: f1cd947f-eba2-411e-8e84-8ca86f608643
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# &quot;catch&quot; erwartet
Sie haben den **try**\-Ausnahmebehandlungsblock verwendet, jedoch nicht die zugeordnete **catch**\-Anweisung geschrieben.  Der Ausnahmebehandlungsmechanismus erfordert, dass der Code, der fehlgeschlagenen kann, zusammen mit dem Code, der bei Auftreten einer Ausnahme nicht ausgeführt werden soll, von einem **try** \-Block umschlossen wird.  Ausnahmen werden im **try**\-Block mit der **throw**\-Anweisung ausgelöst und außerhalb des **try**\-Blocks mit einer oder mehreren **catch**\-Anweisungen abgefangen.  
  
### So beheben Sie diesen Fehler  
  
-   Fügen Sie den zugeordneten **catch**\-Block hinzu.  
  
-   Versuchen Sie, einen **finally**\-Block anstelle eines **catch**\-Blocks zu verwenden.  
  
## Siehe auch  
 [try...catch...finally\-Anweisung](../../javascript/reference/try-dot-dot-dot-catch-dot-dot-dot-finally-statement-javascript.md)   
 [Error\-Objekt](../../javascript/reference/error-object-javascript.md)