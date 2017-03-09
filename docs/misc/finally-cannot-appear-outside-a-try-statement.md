---
title: "&quot;Finally&quot; kann nicht au&#223;erhalb einer Try-Anweisung verwendet werden. | Microsoft Docs"
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
  - "vbc30382"
  - "bc30382"
helpviewer_keywords: 
  - "BC30382"
ms.assetid: 0314d8d2-18bc-4bbd-858c-0a18408b52fd
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &quot;Finally&quot; kann nicht au&#223;erhalb einer Try-Anweisung verwendet werden.
`Finally` wird zum Beenden eines `Try...Catch...Finally`\-Blocks verwendet und kann daher nur einmal am Ende des Blocks angegeben werden. Entweder ist `Finally` unnötig, oder die `Finally`\-Anweisung befindet sich außerhalb des entsprechenden `Try`\-Blocks.  
  
 **Fehler\-ID:** BC30382  
  
### So beheben Sie diesen Fehler  
  
1.  Suchen und entfernen Sie die unnötige `Finally`\-Anweisung.  
  
2.  Verschieben Sie die `Finally`\-Anweisung an die gewünschte Position im Code.  
  
## Siehe auch  
 [Try...Catch...Finally Statement](/dotnet/visual-basic/language-reference/statements/try-catch-finally-statement)   
 [Übersicht über die strukturierte Ausnahmebehandlung für Visual Basic](http://msdn.microsoft.com/de-de/bb81af80-a735-4873-9711-6151a48e418a)