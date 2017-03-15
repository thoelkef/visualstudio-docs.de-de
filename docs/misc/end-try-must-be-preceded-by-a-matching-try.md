---
title: "&#39;End Try&#39; muss ein entsprechendes &#39;Try&#39; voranstehen. | Microsoft Docs"
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
  - "bc30383"
  - "vbc30383"
helpviewer_keywords: 
  - "BC30383"
ms.assetid: 1d13357a-ab44-4082-b204-6e2e94f4774e
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;End Try&#39; muss ein entsprechendes &#39;Try&#39; voranstehen.
`End`  `Try` wird zum Beenden eines `Try`\-Blocks verwendet und kann daher nur am Ende des Blocks angegeben werden. Entweder ist die `End Try`\-Anweisung redundant, oder die `End``Try`\-Anweisung befindet sich außerhalb des entsprechenden `Try`\-Blocks.  
  
 **Fehler\-ID:** BC30383  
  
### So beheben Sie diesen Fehler  
  
1.  Suchen und entfernen Sie die unnötige `End Try`\-Anweisung.  
  
2.  Fügen Sie `End Try` an der gewünschten Stelle im Code hinzu.  
  
## Siehe auch  
 [Try...Catch...Finally Statement](/dotnet/visual-basic/language-reference/statements/try-catch-finally-statement)   
 [Übersicht über die strukturierte Ausnahmebehandlung für Visual Basic](http://msdn.microsoft.com/de-de/bb81af80-a735-4873-9711-6151a48e418a)