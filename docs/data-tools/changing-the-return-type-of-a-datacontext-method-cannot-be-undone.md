---
title: "Eine &#196;nderung des R&#252;ckgabetyps einer DataContext-Methode kann nicht r&#252;ckg&#228;ngig gemacht werden | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 76b161fc-5075-4192-8d94-f15b02e199e9
caps.latest.revision: 3
caps.handback.revision: 1
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Eine &#196;nderung des R&#252;ckgabetyps einer DataContext-Methode kann nicht r&#252;ckg&#228;ngig gemacht werden
Eine Änderung des Rückgabetyps einer DataContext\-Methode kann nicht rückgängig gemacht werden.Wenn Sie den Typ auf den automatisch generierten Typ zurücksetzen möchten, müssen Sie das Element wieder aus dem Server\-Explorer\/Datenbank\-Explorer in den O\/R\-Designer ziehen.Möchten Sie den Rückgabetyp wirklich ändern?  
  
 Der Rückgabetyp einer <xref:System.Data.Linq.DataContext>\-Methode ist je nachdem, wo Sie das Element im [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] ablegen, unterschiedlich.Wenn Sie ein Element direkt auf einer existierenden Entitätsklasse ablegen, wird eine <xref:System.Data.Linq.DataContext>\-Methode erzeugt, die den Rückgabetyp dieser Entitätsklasse hat.Wenn Sie ein Element in einem leeren Bereich von [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] ablegen, wird eine <xref:System.Data.Linq.DataContext>\-Methode erzeugt, die einen automatisch erzeugten Typ zurückgibt.Sie können den Rückgabetyp einer <xref:System.Data.Linq.DataContext>\-Methode ändern, wenn Sie sie dem Methodenbereich hinzugefügt haben.Um den Rückgabetyp einer <xref:System.Data.Linq.DataContext>\-Methode zu überprüfen oder zu ändern, markieren Sie sie, und klicken Sie auf die Eigenschaft **Rückgabetyp** im Fenster **Eigenschaften**.  
  
### So ändern Sie den Rückgabetyp eines DataContext  
  
-   Klicken Sie auf **Ja**.  
  
### So schließen Sie das Meldungsfeld, ohne den Rückgabetyp zu ändern  
  
-   Klicken Sie auf **Nein**.  
  
### So setzen Sie den Typ auf den ursprünglichen Rückgabetyp zurück, nachdem der Rückgabetyp geändert wurde  
  
1.  Wählen Sie die <xref:System.Data.Linq.DataContext>\-Methode im [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] aus, und löschen Sie sie.  
  
2.  Suchen Sie das Element in **Server\-Explorer\/Datenbank\-Explorer**, und ziehen Sie es auf den [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].  
  
     Eine <xref:System.Data.Linq.DataContext>\-Methode mit dem ursprünglichen Standardrückgabetyp wird erstellt.  
  
## Siehe auch  
 [Object Relational Designer \(O\/R\-Designer\)](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [DataContext\-Methoden \(O\/R\-Designer\)](../data-tools/datacontext-methods-o-r-designer.md)   
 [Vorgehensweise: Erstellen von DataContext\-Methoden, die gespeicherten Prozeduren und Funktionen \(O\/R\-Designer\) zugeordnet sind](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md)   
 [LINQ to SQL](../Topic/LINQ%20to%20SQL.md)