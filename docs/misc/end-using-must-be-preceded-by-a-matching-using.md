---
title: "&quot;End Using&quot; muss eine entsprechende Using-Anweisung voranstehen. | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc36007"
  - "vbc36007"
helpviewer_keywords: 
  - "BC36007"
ms.assetid: 10fb31ba-9b6c-403f-bacc-c7b5df14f1dd
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &quot;End Using&quot; muss eine entsprechende Using-Anweisung voranstehen.
Eine `End Using`\-Anweisung wird ohne die entsprechende vorangehende `Using`\-Deklaration angezeigt.  
  
 **Fehler\-ID:** BC36007  
  
### So beheben Sie diesen Fehler  
  
-   Entfernen Sie die `End Using`\-Anweisung, falls sie redundant ist.  
  
-   Geben Sie die fehlende [Using Statement](/dotnet/visual-basic/language-reference/statements/using-statement) ein, falls diese fehlt.  
  
-   Verschieben Sie die `End Using`\-Anweisung im Code an die entsprechende Position.  
  
## Siehe auch  
 [End \<keyword\> Statement](../Topic/End%20%3Ckeyword%3E%20Statement%20\(Visual%20Basic\).md)