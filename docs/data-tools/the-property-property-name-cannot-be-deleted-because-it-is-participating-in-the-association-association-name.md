---
title: "Die &lt;Eigenschaftenname&gt;-Eigenschaft kann nicht gel&#246;scht werden, weil sie an der Zuordnung &lt;Zuordnungsname&gt; teilnimmt | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 389873cc-92dd-48da-bfca-0f6c8e0ae3c2
caps.latest.revision: 3
caps.handback.revision: 1
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Die &lt;Eigenschaftenname&gt;-Eigenschaft kann nicht gel&#246;scht werden, weil sie an der Zuordnung &lt;Zuordnungsname&gt; teilnimmt
Die ausgewählte Eigenschaft wurde als **Zuordnungseigenschaft** für die Zuordnung zwischen den in der Fehlermeldung angegebenen Klassen festgelegt.Eigenschaften können nicht gelöscht werden, wenn sie an einer Zuordnung zwischen Datenklassen beteiligt sind.  
  
 Legen Sie die **Zuordnungseigenschaft** auf eine andere Eigenschaft der Datenklasse fest, damit die gewünschte Eigenschaft gelöscht werden kann.  
  
### So beheben Sie diesen Fehler  
  
1.  Wählen Sie im O\/R\-Designer die Zuordnungslinie aus, die die in der Fehlermeldung angegebenen Datenklassen verbindet.  
  
2.  Doppelklicken Sie auf die Linie, um das Dialogfeld **Zuordnungs\-Editor** zu öffnen.  
  
3.  Entfernen Sie die Eigenschaft aus den **Zuordnungseigenschaften**.  
  
4.  Versuchen Sie erneut, die Eigenschaft zu löschen.  
  
## Siehe auch  
 [Übersicht über den O\/R\-Designer](../Topic/LINQ%20to%20SQL%20Tools%20in%20Visual%20Studio1.md)   
 [Vorgehensweise: Erstellen einer Zuordnung \(Beziehung\) zwischen LINQ to SQL\-Klassen \(O\/R\-Designer\)](../data-tools/how-to-create-an-association-relationship-between-linq-to-sql-classes-o-r-designer.md)   
 [Exemplarische Vorgehensweise: Erstellen von LINQ to SQL\-Klassen \(O\/R\-Designer\)](../Topic/Walkthrough:%20Creating%20LINQ%20to%20SQL%20Classes%20\(O-R%20Designer\).md)   
 [LINQ to SQL](../Topic/LINQ%20to%20SQL.md)