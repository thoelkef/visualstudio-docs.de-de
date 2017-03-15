---
title: "Der &quot;Catch&quot;-Block wurde nie erreicht; &quot;&lt;Ausnahme&gt;&quot; wurde oben in derselben Try-Anweisung behandelt. | Microsoft Docs"
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
  - "bc42031"
  - "vbc42031"
helpviewer_keywords: 
  - "BC42031"
ms.assetid: 7d15597c-5988-42ea-a853-63cbf78faaf3
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Der &quot;Catch&quot;-Block wurde nie erreicht; &quot;&lt;Ausnahme&gt;&quot; wurde oben in derselben Try-Anweisung behandelt.
Ein `Catch`\-Block im Code kann nicht erreicht werden, weil er in einem vorhergehenden `Try`\-Block behandelt wird.  
  
 Standardmäßig ist diese Meldung eine Warnung. Weitere Informationen zum Ausblenden von Warnungen oder zum Behandeln von Warnungen als Fehler finden Sie unter [Konfigurieren von Warnungen in Visual Basic](../ide/configuring-warnings-in-visual-basic.md).  
  
 **Fehler\-ID:** BC42031  
  
### So beheben Sie diesen Fehler  
  
-   Entfernen Sie die redundante Anweisung.  
  
## Siehe auch  
 [Gewusst wie: Auffangen einer Ausnahme in Visual Basic](http://msdn.microsoft.com/de-de/f3063c89-d2bf-49b1-91b5-b87edfb18b95)   
 [Gewusst wie: Testen von Code mit einem Try...Catch\-Block in Visual Basic](http://msdn.microsoft.com/de-de/8368e205-ed73-4185-a247-af84fb4fafa9)   
 [Gewusst wie: Filtern von Fehlern in einem Catch\-Block in Visual Basic](http://msdn.microsoft.com/de-de/85964d0a-56e7-4301-a96e-5eaea23b7b9b)   
 [Exemplarische Vorgehensweise: Strukturierte Ausnahmebehandlung \(Visual Basic\)](http://msdn.microsoft.com/de-de/440da655-4b32-490b-8b16-bfe46f41fa76)   
 [Try...Catch...Finally Statement](/dotnet/visual-basic/language-reference/statements/try-catch-finally-statement)