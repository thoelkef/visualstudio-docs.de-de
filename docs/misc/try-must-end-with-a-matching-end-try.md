---
title: "&quot;Try&quot; muss mit einem entsprechenden &quot;End Try&quot; abgeschlossen werden. | Microsoft Docs"
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
  - "bc30384"
  - "vbc30384"
helpviewer_keywords: 
  - "BC30384"
ms.assetid: 898300b4-c091-4105-aeb0-9bd559ff6b6f
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &quot;Try&quot; muss mit einem entsprechenden &quot;End Try&quot; abgeschlossen werden.
`Try` wird zum Einleiten eines `Try`\-Blocks verwendet und kann daher nur am Anfang des Blocks stehen. Der Block muss mit einer passenden `End Try`\-Anweisung beendet werden. Entweder ist eine redundante `Try` vorhanden, oder Sie haben den `Try`\-Block nicht mit `Finally` abgeschlossen.  
  
 **Fehler\-ID:** BC30384  
  
### So beheben Sie diesen Fehler  
  
1.  Suchen und entfernen Sie die unnötige `Try`, oder beenden Sie den Block mit einer passenden `End Try`.  
  
## Siehe auch  
 [Try...Catch...Finally Statement](/dotnet/visual-basic/language-reference/statements/try-catch-finally-statement)   
 [Übersicht über die strukturierte Ausnahmebehandlung für Visual Basic](http://msdn.microsoft.com/de-de/bb81af80-a735-4873-9711-6151a48e418a)