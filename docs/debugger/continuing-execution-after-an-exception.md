---
title: "Fortfahren mit der Ausf&#252;hrung nach einer Ausnahme | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "Debugger, Ausnahmen"
  - "Ausnahmebehandlung, Fortsetzen der Ausführung nach"
  - "Ausnahmen (Dialogfeld)"
  - "Ausnahmen, Fortsetzen der Ausführung nach"
  - "Ausführung, Fortsetzen nach einer Ausnahme"
  - "Verwalteter Code, Ausnahmebehandlung"
  - "Verwaltete Ausnahmen, Fortsetzen der Ausführung nach"
  - "Programmausführung"
  - "Programme, Ausführen"
  - "Threading [Visual Studio], Fortsetzen der Ausführung nach Ausnahmen"
ms.assetid: 6fe97aac-2131-4615-bd92-d3afee741558
caps.latest.revision: 25
caps.handback.revision: 25
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Fortfahren mit der Ausf&#252;hrung nach einer Ausnahme
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Wenn die Ausführung wegen einer Ausnahme vom Debugger unterbrochen wird, wird ein Dialogfeld angezeigt.  Bei Visual Basic oder C\# wird standardmäßig das Dialogfeld [Exception Assistant](../Topic/Exception%20Assistant.md) angezeigt.  Bei C\+\+ wird das ältere Dialogfeld **Ausnahme** angezeigt.  Wenn Sie Visual Basic oder C\# verwenden, aber im Dialogfeld **Optionen** die Option **Ausnahmen\-Assistent** deaktiviert haben, wird das Dialogfeld **Ausnahme** angezeigt.  
  
 Wird das Dialogfeld **Ausnahmen\-Assistent** oder das Dialogfeld **Ausnahme** angezeigt, können Sie versuchen, das Problem, das die Ausnahme verursacht hat, zu beheben.  
  
## Verwalteter Code  
 In verwaltetem Code kann die Ausführung nach einem Ausnahmefehler im gleichen Thread fortgesetzt werden.  Der **Ausnahmen\-Assistent** entlädt die Aufrufliste bis an den Punkt, an dem die Ausnahme ausgelöst wurde.  
  
## Systemeigener Code  
 Bei systemeigenem C\/C\+\+ haben Sie zwei Möglichkeiten:  
  
-   Sie können auf **Unterbrechen** klicken und versuchen, das Problem zu beheben.  Im Unterbrechungsmodus können Sie die Aufrufliste entladen, indem Sie im Fenster **Aufrufliste** mit der rechten Maustaste auf einen Rahmen klicken und im Kontextmenü die Option **Bis zu diesem Rahmen entladen** auswählen.  Wenn Sie das Debuggen fortsetzen, ohne das Problem behoben zu haben, wird das Dialogfeld **Ausnahme** erneut angezeigt.  Andernfalls wird das Dialogfeld **Ausnahme** nicht erneut angezeigt.  
  
-   Sie können auf **Weiter** klicken, um die Ausführung fortzusetzen, ohne das Problem zu beheben.  Das Dialogfeld **Ausnahme** wird erneut angezeigt.  
  
## Gemischter Code  
 Wenn beim Debuggen gemischten Codes \(systemeigener und verwalteter Code\) ein Ausnahmefehler auftritt, verhindern Einschränkungen des Betriebssystems das Entladen der Aufrufliste.  Sollten Sie versuchen, die Aufrufliste über das Kontextmenü neu zu laden, erhalten Sie die Fehlermeldung, dass der Debugger beim Debuggen von gemischtem Code keine Entladung aus einer unbehandelten Ausnahme vornehmen kann.  
  
## Siehe auch  
 [Verwalten von Ausnahmen mit dem Debugger](../debugger/managing-exceptions-with-the-debugger.md)