---
title: "Vorgehensweise: Zuweisen von gespeicherten Prozeduren zur Durchf&#252;hrung von Update-, Einf&#252;ge- und L&#246;schvorg&#228;ngen (O/R-Designer) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e88224ab-ff61-4a3a-b6b8-6f3694546cac
caps.latest.revision: 2
caps.handback.revision: 2
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Vorgehensweise: Zuweisen von gespeicherten Prozeduren zur Durchf&#252;hrung von Update-, Einf&#252;ge- und L&#246;schvorg&#228;ngen (O/R-Designer)
Gespeicherte Prozeduren können dem O\/R\-Designer hinzugefügt und als typische <xref:System.Data.Linq.DataContext>\-Methoden ausgeführt werden.Mit ihnen kann auch das [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)]\-Standardlaufzeitverhalten überschrieben werden, das beim Speichern von Änderungen von Entitätsklassen in einer Datenbank Einfüge\-, Update\- und Löschvorgänge durchführt \(beispielsweise, wenn die <xref:System.Data.Linq.DataContext.SubmitChanges%2A>\-Methode aufgerufen wird\).  
  
> [!NOTE]
>  Wenn Ihre gespeicherte Prozedur Werte zurückgibt, die an den Client zurückgesendet werden müssen \(beispielsweise Werte, die in der gespeicherten Prozedur berechnet werden\), sollten Sie Ausgabeparameter in Ihrer gespeicherten Prozedur erstellen.Wenn Sie keine Ausgabeparameter verwenden können, sollten Sie eine partielle Methodenimplementierung schreiben und sich nicht auf vom O\/R\-Designer erzeugte Überschreibungen verlassen.Member, die datenbankgenerierten Werten zugeordnet werden, müssen nach erfolgreicher Beendigung von INSERT\- oder UPDATE\-Vorgängen auf entsprechende Werte festgelegt werden.Weitere Informationen finden Sie unter [Aufgaben des Entwicklers beim Überschreiben des Standardverhaltens](../Topic/Responsibilities%20of%20the%20Developer%20In%20Overriding%20Default%20Behavior.md).  
  
> [!NOTE]
>  [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] behandelt datenbankgenerierte Werte für die Identitätsspalte \(automatisch inkrementiert\), die ROWGUID\-Spalte \(datenbankgenerierte GUID\) und Timestamp\-Spalte automatisch.Datenbankgenerierte Werte in anderen Spaltentypen führen unerwartet zu einem NULL\-Wert.Um die datenbankgenerierten Werte zurückzugeben, sollte manuell <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A> auf `true` und <xref:System.Data.Linq.Mapping.ColumnAttribute.AutoSync%2A> auf eine der folgenden Einstellungen festgelegt werden: <xref:System.Data.Linq.Mapping.AutoSync>, <xref:System.Data.Linq.Mapping.AutoSync> oder <xref:System.Data.Linq.Mapping.AutoSync>.  
  
## Konfigurieren des Updateverhaltens einer Entitätsklasse  
 Standardmäßig wird die Updatelogik einer Datenbank \(Einfüge\-, Update\- und Löschvorgänge\) mit Änderungen, die von [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)]\-Entitätsklassen an Daten vorgenommen wurden, von der [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)]\-Laufzeit bereitgestellt.Basierend auf dem Schema der Tabelle \(den Spalten\- und Primärschlüsselinformationen\) werden von der Laufzeit Standardbefehle für Einfüge\-, Update\- und Löschvorgänge erstellt.Wenn das Standardverhalten nicht erwünscht ist, kann das Updateverhalten konfiguriert werden, indem spezielle gespeicherte Prozeduren zur Durchführung der erforderlichen Einfüge\-, Update\- und Löschvorgänge zugewiesen werden, die zur Bearbeitung der Daten in der Tabelle erforderlich sind. Diese Vorgehensweise ist auch dann sinnvoll, wenn kein Standardverhalten erzeugt wird, z. B. wenn die Entitätsklassen Sichten zugeordnet sind.Schließlich kann das standardmäßige Updateverhalten auch dann überschrieben werden, wenn die Datenbank den Zugriff auf Tabellen über gespeicherte Prozeduren erfordert.  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
#### So weisen Sie gespeicherte Prozeduren zu, um das Standardverhalten einer Entitätsklasse zu überschreiben  
  
1.  Öffnen Sie die **LINQ to SQL**\-Datei im Designer.\(Doppelklicken Sie im **Projektmappen\-Explorer** auf die DBML\-Datei.\)  
  
2.  Erweitern Sie im **Server\-Explorer**\/**Datenbank\-Explorer** den Knoten **Gespeicherte Prozeduren**, und suchen Sie die gespeicherten Prozeduren, die für die Einfüge\-, Update\- und\/oder Löschbefehle der Entitätsklasse verwendet werden sollen.  
  
3.  Ziehen Sie die gespeicherte Prozedur in den O\/R\-Designer.  
  
     Die gespeicherte Prozedur wird dem Methodenbereich als <xref:System.Data.Linq.DataContext>\-Methode hinzugefügt.Weitere Informationen finden Sie unter [DataContext\-Methoden \(O\/R\-Designer\)](../data-tools/datacontext-methods-o-r-designer.md).  
  
4.  Wählen Sie die Entitätsklasse aus, für die die gespeicherte Prozedur zur Durchführung von Updates verwendet werden soll.  
  
5.  Wählen Sie im Fenster **Eigenschaften** den Befehl aus, der überschrieben werden soll \(**Einfügen**, **Aktualisieren** oder **Löschen**\).  
  
6.  Klicken Sie auf die Auslassungszeichen \(...\) neben den Wörtern **Laufzeit verwenden**, um das Dialogfeld **Verhalten konfigurieren** zu öffnen.  
  
7.  Wählen Sie **Anpassen** aus.  
  
8.  Wählen Sie die gewünschte gespeicherte Prozedur in der Liste **Anpassen** aus.  
  
9. Untersuchen Sie die Listen **Methodenargumente** und **Klasseneigenschaften**, um zu überprüfen, ob die **Methodenargumente** den entsprechenden **Klasseneigenschaften** zugeordnet sind.Ordnen Sie die ursprünglichen Methodenargumente \(Original\_*ArgumentName*\) den ursprünglichen Eigenschaften \(*PropertyName* \(Original\)\) für Update\- und Löschbefehle zu.  
  
    > [!NOTE]
    >  Standardmäßig werden Methodenargumente Klasseneigenschaften zugeordnet, wenn die Namen übereinstimmen.Wenn geänderte Eigenschaftennamen von Tabelle und Entitätsklasse nicht mehr übereinstimmen, kann es notwendig sein, die entsprechende Klasseneigenschaft für die Zuordnung auszuwählen, wenn der Designer die korrekte Zuordnung nicht ermitteln kann.  
  
10. Klicken Sie auf **OK** oder auf **Übernehmen**.  
  
    > [!NOTE]
    >  Sie können mit der Konfiguration des Verhaltens jeder Klasse\/Verhalten\-Kombination fortfahren, solange Sie nach jeder Änderung auf **Übernehmen** klicken.Wenn Sie eine Klasse oder ein Verhalten ändern bevor Sie auf **Übernehmen** klicken, wird ein Warnungsdialogfeld angezeigt, das Ihnen Gelegenheit bietet, alle Änderungen zu übernehmen.  
  
     Um zur Verwendung der Standardlaufzeitlogik für Updates zurückzukehren, klicken Sie im Fenster **Eigenschaften** auf die Auslassungszeichen neben dem Einfüge\-, Update\- oder Löschbefehl, und wählen Sie dann im Dialogfeld **Verhalten konfigurieren** die Option **Laufzeit verwenden** aus.  
  
## Siehe auch  
 [Object Relational Designer \(O\/R\-Designer\)](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [DataContext\-Methoden \(O\/R\-Designer\)](../data-tools/datacontext-methods-o-r-designer.md)   
 [Exemplarische Vorgehensweise: Erstellen von LINQ to SQL\-Klassen \(O\/R\-Designer\)](../Topic/Walkthrough:%20Creating%20LINQ%20to%20SQL%20Classes%20\(O-R%20Designer\).md)   
 [Exemplarische Vorgehensweise: Erstellen von aktualisierten gespeicherten Prozeduren für die Northwind\-Kundentabelle](../data-tools/walkthrough-creating-update-stored-procedures-for-the-northwind-customers-table.md)   
 [LINQ to SQL](../Topic/LINQ%20to%20SQL.md)   
 [Insert\-, Update\- und Delete\-Operationen](../Topic/Insert,%20Update,%20and%20Delete%20Operations.md)