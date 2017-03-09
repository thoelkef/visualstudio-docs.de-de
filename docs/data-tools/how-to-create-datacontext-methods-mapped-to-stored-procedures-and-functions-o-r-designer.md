---
title: "Vorgehensweise: Erstellen von DataContext-Methoden, die gespeicherten Prozeduren und Funktionen (O/R-Designer) zugeordnet sind | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e7ca32f1-50b3-48af-ad92-ceafd749296a
caps.latest.revision: 2
caps.handback.revision: 2
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Vorgehensweise: Erstellen von DataContext-Methoden, die gespeicherten Prozeduren und Funktionen (O/R-Designer) zugeordnet sind
Dem [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] können gespeicherte Prozeduren und Funktionen als <xref:System.Data.Linq.DataContext>\-Methoden hinzugefügt werden.Durch Aufrufen der Methode und Übergeben der erforderlichen Parameter wird die gespeicherte Prozedur oder Funktion in der Datenbank ausgeführt und gibt die Daten im Rückgabetyp der <xref:System.Data.Linq.DataContext>\-Methode zurück.Ausführliche Informationen zu <xref:System.Data.Linq.DataContext>\-Klassen finden Sie unter [DataContext\-Methoden \(O\/R\-Designer\)](../data-tools/datacontext-methods-o-r-designer.md).  
  
> [!NOTE]
>  Mit gespeicherten Prozeduren kann auch das [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)]\-Standardlaufzeitverhalten überschrieben werden, das beim Speichern von Änderungen von Entitätsklassen in einer Datenbank Einfüge\-, Update\- und Löschvorgänge durchführt.Weitere Informationen finden Sie unter [Vorgehensweise: Zuweisen von gespeicherten Prozeduren zur Durchführung von Update\-, Einfüge\- und Löschvorgängen \(O\/R\-Designer\)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md).  
  
## Erstellen von DataContext\-Methoden  
 Sie können <xref:System.Data.Linq.DataContext>\-Methoden erstellen, indem Sie gespeicherte Prozeduren oder Funktionen vom **Server\-Explorer\/Datenbank\-Explorer** auf den [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] ziehen.  
  
> [!NOTE]
>  Der Rückgabetyp einer generierten <xref:System.Data.Linq.DataContext>\-Methode ist davon abhängig, wo Sie die gespeicherte Prozedur oder Funktion im [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] ablegen.Wenn Sie Elemente direkt auf einer existierenden Entitätsklasse ablegen, wird eine <xref:System.Data.Linq.DataContext>\-Methode mit dem Rückgabewert dieser Entitätsklasse erstellt.Wenn Sie Elemente in einem leeren Bereich von [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] ablegen, wird eine <xref:System.Data.Linq.DataContext>\-Methode erstellt, die einen automatisch generierten Typ zurückgibt.Sie können den Rückgabetyp einer <xref:System.Data.Linq.DataContext>\-Methode ändern, nachdem Sie diese dem Methodenbereich hinzugefügt haben.Um den Rückgabetyp einer <xref:System.Data.Linq.DataContext>\-Methode zu überprüfen oder zu ändern, markieren Sie sie, und überprüfen Sie die Eigenschaft **Rückgabetyp** im Fenster **Eigenschaften**.Weitere Informationen finden Sie unter [Vorgehensweise: Ändern des Rückgabetyps einer DataContext\-Methode \(O\/R\-Designer\)](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md).  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
#### So erstellen Sie DataContext\-Methoden, die automatisch generierte Typen zurückgeben  
  
1.  Erweitern Sie in **Server\-Explorer**\/**Datenbank\-Explorer** den Knoten **Gespeicherte Prozeduren** für die Datenbank, mit der Sie arbeiten.  
  
2.  Suchen Sie die gewünschte gespeicherte Prozedur, und ziehen Sie diese auf einen leeren Bereich des [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].  
  
     Die <xref:System.Data.Linq.DataContext>\-Methode wird mit einem automatisch generierten Rückgabetyp erstellt und im Bereich **Methoden** angezeigt.  
  
#### So erstellen Sie DataContext\-Methoden, die über den Rückgabetyp einer Entitätsklasse verfügen  
  
1.  Erweitern Sie in **Server\-Explorer**\/**Datenbank\-Explorer** den Knoten **Gespeicherte Prozeduren** für die Datenbank, mit der Sie arbeiten.  
  
2.  Suchen Sie die gewünschte gespeicherte Prozedur, und ziehen Sie diese im [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] auf eine vorhandene Entitätsklasse.  
  
     Die <xref:System.Data.Linq.DataContext>\-Methode wird mit dem Rückgabetyp der ausgewählten Entitätsklasse erstellt und im Bereich **Methoden** angezeigt.  
  
> [!NOTE]
>  Informationen über das Ändern des Rückgabetyps vorhandener <xref:System.Data.Linq.DataContext>\-Methoden finden Sie unter [Vorgehensweise: Ändern des Rückgabetyps einer DataContext\-Methode \(O\/R\-Designer\)](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md).  
  
## Siehe auch  
 [Object Relational Designer \(O\/R\-Designer\)](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [DataContext\-Methoden \(O\/R\-Designer\)](../data-tools/datacontext-methods-o-r-designer.md)   
 [Exemplarische Vorgehensweise: Erstellen von LINQ to SQL\-Klassen \(O\/R\-Designer\)](../Topic/Walkthrough:%20Creating%20LINQ%20to%20SQL%20Classes%20\(O-R%20Designer\).md)   
 [LINQ to SQL](../Topic/LINQ%20to%20SQL.md)   
 [Introduction to LINQ in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/linq/introduction-to-linq)   
 [Gewusst wie: Schreiben von LINQ\-Abfragen in C\#](../Topic/How%20to:%20Write%20LINQ%20Queries%20in%20C%23.md)