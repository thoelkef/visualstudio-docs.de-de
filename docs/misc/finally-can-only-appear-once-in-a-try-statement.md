---
title: "„Finally“ darf in einer Try-Anweisung nur einmal angegeben werden. | Microsoft Docs"
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
  - "vbc30381"
  - "bc30381"
helpviewer_keywords: 
  - "BC30381"
ms.assetid: 4fa1d5fa-c54a-4f8c-9d66-9dbcc38c53bf
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# „Finally“ darf in einer Try-Anweisung nur einmal angegeben werden.
`Finally` wird zum Beenden eines `Try...Catch...Finally`\-Blocks verwendet, kann daher nur einmal am Ende des Blocks angegeben werden.  
  
 **Fehler\-ID:** BC30381  
  
### So beheben Sie diesen Fehler  
  
1.  Suchen und entfernen Sie das redundante `Finally`.  
  
## Siehe auch  
 [Try...Catch...Finally Statement](/dotnet/visual-basic/language-reference/statements/try-catch-finally-statement)   
 [Übersicht über die strukturierte Ausnahmebehandlung für Visual Basic](http://msdn.microsoft.com/de-de/bb81af80-a735-4873-9711-6151a48e418a)