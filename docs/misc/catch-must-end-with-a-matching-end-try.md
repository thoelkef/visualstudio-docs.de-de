---
title: "&quot;Catch&quot; muss mit einem entsprechenden &quot;End Try&quot; abgeschlossen werden. | Microsoft Docs"
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
  - "bc30441"
  - "vbc30441"
helpviewer_keywords: 
  - "BC30441"
ms.assetid: 0e4756b4-1f29-4073-88c5-8f8c93ba6c9e
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &quot;Catch&quot; muss mit einem entsprechenden &quot;End Try&quot; abgeschlossen werden.
Im Code wird eine `Catch`\-Anweisung ohne zugehörige `End Try`\-Anweisung verwendet.`Catch`\-Anweisungen müssen mit einer `End Try`\-Anweisung abgeschlossen werden.  
  
 **Fehler\-ID:** BC30441  
  
### So beheben Sie diesen Fehler  
  
1.  Entfernen Sie die `Catch`\-Anweisung.  
  
2.  Fügen Sie eine `End Try`\-Anweisung hinzu, um den Block zu beenden.  
  
## Siehe auch  
 [Try...Catch...Finally Statement](/dotnet/visual-basic/language-reference/statements/try-catch-finally-statement)   
 [Übersicht über die strukturierte Ausnahmebehandlung für Visual Basic](http://msdn.microsoft.com/de-de/bb81af80-a735-4873-9711-6151a48e418a)