---
title: "&quot;Interface&quot; muss mit einem entsprechenden &quot;End Interface&quot; abgeschlossen werden | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc30253"
  - "bc30253"
helpviewer_keywords: 
  - "BC30253"
ms.assetid: 0a2d5b70-997f-4926-ab79-4fdfa23042f7
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &quot;Interface&quot; muss mit einem entsprechenden &quot;End Interface&quot; abgeschlossen werden
Eine `Interface`\-Anweisung tritt ohne entsprechende `End Interface`\-Anweisung auf. Sie müssen eine `End Interface`\-Anweisung verwenden, um die Schnittstellendefinition abzuschließen.  
  
 **Fehler\-ID:** BC30253  
  
### So beheben Sie diesen Fehler  
  
1.  Überprüfen Sie, ob die `Interface`\-Member korrekt formatiert sind.  
  
2.  Fügen Sie am Ende der Schnittstellendefinition eine `End Interface`\-Anweisung hinzu.  
  
## Siehe auch  
 [Interface Statement](/dotnet/visual-basic/language-reference/statements/interface-statement)