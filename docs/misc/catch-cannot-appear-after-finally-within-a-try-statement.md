---
title: "&quot;Catch&quot; kann nicht hinter &quot;Finally&quot; in einer Try-Anweisung stehen | Microsoft Docs"
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
  - "vbc30379"
  - "bc30379"
helpviewer_keywords: 
  - "BC30379"
ms.assetid: 33d1278b-cf10-4c66-aaf8-08a4372f370b
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &quot;Catch&quot; kann nicht hinter &quot;Finally&quot; in einer Try-Anweisung stehen
Eine `Catch`\-Anweisung wird im Code hinter dem `Finally`\-Schlüsselwort angezeigt, das einen `Try`\-Anweisungsblock beendet.`Catch` muss innerhalb eines `Try...Catch...Finally`\-Anweisungsblocks angezeigt werden.  
  
 **Fehler\-ID:** BC30379  
  
### So beheben Sie diesen Fehler  
  
1.  Verschieben Sie die `Catch`\-Anweisung im Code an eine geeignete Position.  
  
## Siehe auch  
 [Try...Catch...Finally Statement](/dotnet/visual-basic/language-reference/statements/try-catch-finally-statement)   
 [Übersicht über die strukturierte Ausnahmebehandlung für Visual Basic](http://msdn.microsoft.com/de-de/bb81af80-a735-4873-9711-6151a48e418a)