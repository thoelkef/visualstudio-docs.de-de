---
title: "Vorgehensweise: Erstellen von LINQ to SQL-Klassen, die Tabellen und Ansichten (O/R-Designer) zugeordnet sind | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0fb78bbc-7a78-4ab4-b32f-85ece912e660
caps.latest.revision: 3
caps.handback.revision: 1
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Vorgehensweise: Erstellen von LINQ to SQL-Klassen, die Tabellen und Ansichten (O/R-Designer) zugeordnet sind
[!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)]\-Klassen, die Datenbanktabellen und \-sichten zugeordnet sind, werden als *Entitätsklassen* bezeichnet. Die Entitätsklasse wird einem Datensatz zugeordnet, während die einzelnen Eigenschaften einer Entitätsklasse den jeweiligen Spalten eines Datensatzes zugeordnet werden.Sie können Entitätsklassen auf Grundlage von Datenbanktabellen oder \-sichten erstellen, indem Sie Tabellen oder Sichten von **Server\-Explorer**\/**Datenbank\-Explorer** auf den [Object Relational Designer \(O\/R\-Designer\)](../data-tools/linq-to-sql-tools-in-visual-studio2.md) ziehen.[!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] generiert die Klassen und wendet die spezifischen [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)]\-Attribute an, um die [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)]\-Funktionalität zu aktivieren \(die Datenkommunikations\- und Bearbeitungsfunktionen von <xref:System.Data.Linq.DataContext>\).Ausführliche Informationen zu [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)]\-Klassen finden Sie unter [Das LINQ to SQL\-Objektmodell](../Topic/The%20LINQ%20to%20SQL%20Object%20Model.md).  
  
> [!NOTE]
>  Bei [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] handelt es sich um eine einfache objektrelationale Zuordnung, da nur 1:1\-Zuordnungsbeziehungen unterstützt werden.Das heißt, dass eine Entitätsklasse nur über eine 1:1\-Zuordnungsbeziehung zu einer Datenbanktabelle oder \-sicht verfügen kann.Eine komplexe Zuordnung, z. B. das Zuordnen einer Entitätsklasse zu mehreren Tabellen, wird nicht unterstützt.Sie können jedoch einer Sicht, die mehrere zusammengehörige Tabellen verknüpft, eine Entitätsklasse zuordnen.  
  
## Erstellen von LINQ to SQL\-Klassen, die Datenbanktabellen oder \-sichten zugeordnet sind  
 Entitätsklassen können erstellt werden, indem die Tabellen oder Sichten von **Server\-Explorer**\/**Datenbank\-Explorer** auf den [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] gezogen werden, zusätzlich zu den <xref:System.Data.Linq.DataContext>\-Methoden zum Durchführen von Updates.  
  
 Standardmäßig erstellt die [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)]\-Laufzeit die Logik zum Speichern von in einer aktualisierbaren Entitätsklasse vorgenommenen Änderungen in der Datenbank.Diese Logik basiert auf dem Schema der Tabelle \(den Spaltendefinitionen und Primärschlüsselinformationen\).Wenn Sie dieses Verhalten nicht wünschen, können Sie eine Entitätsklasse konfigurieren, um anstelle des [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)]\-Laufzeitverhaltens gespeicherte Prozeduren zum Durchführen von Einfüge\-, Update\- und Löschvorgängen zu verwenden.Weitere Informationen finden Sie unter [Vorgehensweise: Zuweisen von gespeicherten Prozeduren zur Durchführung von Update\-, Einfüge\- und Löschvorgängen \(O\/R\-Designer\)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md).  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
#### So erstellen Sie LINQ to SQL\-Klassen, die Datenbanktabellen oder \-sichten zugeordnet sind  
  
1.  Erweitern Sie in **Server**\/**Datenbank\-Explorer** den Knoten **Tabellen** oder **Sichten**, und suchen Sie die Datenbanktabelle oder \-sicht, die Sie in Ihrer Anwendung verwenden möchten.  
  
2.  Ziehen Sie die Tabelle oder die Sicht auf den [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].  
  
     Eine Entitätsklasse wird erstellt und auf der Entwurfsoberfläche angezeigt.Die Entitätsklasse verfügt über Eigenschaften, die sich auf die Spalten in der ausgewählten Tabelle oder Sicht beziehen.  
  
## Erstellen einer Objektdatenquelle und Anzeigen der Daten auf einem Formular  
 Nach dem Erstellen von Entitätsklassen mithilfe von [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] können Sie eine Objektdatenquelle erstellen und das [Datenquellenfenster](../Topic/Data%20Sources%20Window.md) mit den Entitätsklassen füllen.  
  
#### So erstellen Sie eine Objektdatenquelle auf Grundlage von LINQ to SQL\-Entitätsklassen  
  
1.  Klicken Sie im Menü **Erstellen** auf **Projektmappe erstellen**, um ein Projekt zu erstellen.  
  
2.  Klicken Sie im Menü **Daten** auf **Datenquellen anzeigen**.  
  
3.  Klicken Sie im **Datenquellenfenster** auf **Neue Datenquelle hinzufügen**.  
  
4.  Klicken Sie auf der Seite **Datenquellentyp auswählen** auf **Objekt** und dann auf **Weiter**.  
  
5.  Erweitern Sie die Knoten, suchen und wählen Sie die Klasse aus.  
  
    > [!NOTE]
    >  Wenn die Klasse **Customer** nicht verfügbar ist, beenden Sie den Assistenten, erstellen Sie das Projekt, und führen Sie den Assistenten erneut aus.  
  
6.  Klicken Sie auf **Fertig stellen**, um die Datenquelle zu erstellen, und fügen Sie die Entitätsklasse **Customer** zum Fenster **Datenquellen** hinzu.  
  
7.  Ziehen Sie Elemente aus dem Fenster **Datenquellen** auf ein Formular.  
  
## Siehe auch  
 [Object Relational Designer \(O\/R\-Designer\)](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [Exemplarische Vorgehensweise: Erstellen von LINQ to SQL\-Klassen \(O\/R\-Designer\)](../Topic/Walkthrough:%20Creating%20LINQ%20to%20SQL%20Classes%20\(O-R%20Designer\).md)   
 [DataContext\-Methoden \(O\/R\-Designer\)](../data-tools/datacontext-methods-o-r-designer.md)   
 [Vorgehensweise: Erstellen von DataContext\-Methoden, die gespeicherten Prozeduren und Funktionen \(O\/R\-Designer\) zugeordnet sind](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md)   
 [Das LINQ to SQL\-Objektmodell](../Topic/The%20LINQ%20to%20SQL%20Object%20Model.md)   
 [Vorgehensweise: Hinzufügen von Validierungen zu Entitätsklassen](../data-tools/how-to-add-validation-to-entity-classes.md)   
 [Exemplarische Vorgehensweise: Anpassen des Einfüge\-, Update\- und Löschverhaltens von Entitätsklassen](../data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes.md)   
 [Exemplarische Vorgehensweise: Hinzufügen von Validierung zu Entitätsklassen](../Topic/Walkthrough:%20Adding%20Validation%20to%20Entity%20Classes.md)   
 [Vorgehensweise: Erstellen einer Zuordnung \(Beziehung\) zwischen LINQ to SQL\-Klassen \(O\/R\-Designer\)](../data-tools/how-to-create-an-association-relationship-between-linq-to-sql-classes-o-r-designer.md)