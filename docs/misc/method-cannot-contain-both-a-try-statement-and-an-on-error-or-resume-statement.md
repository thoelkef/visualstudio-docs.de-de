---
title: "Eine Methode kann nicht gleichzeitig eine Try-Anweisung und eine On Error- oder Resume-Anweisung enthalten. | Microsoft Docs"
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
  - "vbc30544"
  - "bc30544"
helpviewer_keywords: 
  - "BC30544"
ms.assetid: 1e75d5fe-9a6b-43c2-9749-1f2d7ce5b10d
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Eine Methode kann nicht gleichzeitig eine Try-Anweisung und eine On Error- oder Resume-Anweisung enthalten.
Sie haben eine `Try`\-Anweisung zusammen mit `On Error` oder `Resume` verwendet.  
  
 **Fehler\-ID:** BC30544  
  
### So beheben Sie diesen Fehler  
  
1.  Entfernen Sie die Anweisung `On Error` oder `Resume`.  
  
## Siehe auch  
 [Übersicht über die strukturierte Ausnahmebehandlung für Visual Basic](http://msdn.microsoft.com/de-de/bb81af80-a735-4873-9711-6151a48e418a)   
 [Try...Catch...Finally Statement](/dotnet/visual-basic/language-reference/statements/try-catch-finally-statement)