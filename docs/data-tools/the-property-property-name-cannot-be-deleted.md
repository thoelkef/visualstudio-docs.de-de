---
title: "Die &lt;Eigenschaftenname&gt;-Eigenschaft kann nicht gel&#246;scht werden | Microsoft Docs"
ms.custom: ""
ms.date: "09/21/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 55873f74-7834-4ec1-8815-eeeb65618d87
caps.latest.revision: 2
caps.handback.revision: 2
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Die &lt;Eigenschaftenname&gt;-Eigenschaft kann nicht gel&#246;scht werden
Die \<Eigenschaftenname\>\-Eigenschaft kann nicht gelöscht werden, da sie als Unterscheidungseigenschaft für die Vererbung zwischen \<Klassenname\> und \<Klassenname\> festgelegt ist.  
  
 Die ausgewählte Eigenschaft wird als **Discriminator Property** für die Vererbung zwischen den in der Fehlermeldung angegebenen Klassen festgelegt.Eigenschaften können nicht gelöscht werden, wenn sie zwischen Datenklassen an der Vererbungskonfiguration teilnehmen.  
  
 Legen Sie die **Discriminator Property** auf eine andere Eigenschaft der Datenklasse fest, damit die gewünschte Eigenschaft gelöscht werden kann.  
  
### So beheben Sie diesen Fehler  
  
1.  Wählen Sie im O\/R\-Designer die Vererbungslinie aus, die die in der Fehlermeldung angegebenen Datenklassen verbindet.  
  
2.  Legen Sie die **Discriminator Property** auf eine andere Eigenschaft fest.  
  
3.  Versuchen Sie erneut, die Eigenschaft zu löschen.  
  
## Siehe auch  
 [Vorgehensweise: Konfigurieren von Vererbung mit dem O\/R\-Designer](../data-tools/how-to-configure-inheritance-by-using-the-o-r-designer.md)   
 [Vererbung von Datenklassen \(O\/R\-Designer\)](../data-tools/data-class-inheritance-o-r-designer.md)   
 [Exemplarische Vorgehensweise: Erstellen von LINQ to SQL\-Klassen mithilfe von Vererbung einer einzelnen Tabelle \(O\/R\-Designer\)](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md)