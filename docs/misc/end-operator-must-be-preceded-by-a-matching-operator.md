---
title: "&#39;End Operator&#39; muss eine entsprechende Operator-Deklaration voranstehen. | Microsoft Docs"
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
  - "vbc33007"
  - "bc33007"
helpviewer_keywords: 
  - "BC33007"
ms.assetid: 57df3e01-0858-4cf7-9295-075a2c0c4bde
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;End Operator&#39; muss eine entsprechende Operator-Deklaration voranstehen.
Eine `End Operator`\-Anweisung tritt ohne die entsprechende vorangehende `Operator`\-Deklaration auf.  
  
 **Fehler\-ID:** BC33007  
  
### So beheben Sie diesen Fehler  
  
-   Entfernen Sie die `End Operator`\-Anweisung, falls sie redundant ist.  
  
-   Geben Sie die fehlende `Operator`\-Prozedur an, falls diese fehlt.  
  
-   Verschieben Sie die `End Operator`\-Anweisung im Code an die entsprechende Position.  
  
## Siehe auch  
 [End \<keyword\> Statement](../Topic/End%20%3Ckeyword%3E%20Statement%20\(Visual%20Basic\).md)   
 [Operator Procedures](/dotnet/visual-basic/programming-guide/language-features/procedures/operator-procedures)   
 [Operator Statement](/dotnet/visual-basic/language-reference/statements/operator-statement)   
 [How to: Define an Operator](../Topic/How%20to:%20Define%20an%20Operator%20\(Visual%20Basic\).md)   
 [How to: Define a Conversion Operator](../Topic/How%20to:%20Define%20a%20Conversion%20Operator%20\(Visual%20Basic\).md)