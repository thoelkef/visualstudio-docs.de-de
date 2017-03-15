---
title: "Exemplarische Vorgehensweise: Anpassen des Einf&#252;ge-, Update- und L&#246;schverhaltens von Entit&#228;tsklassen | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 03ff1146-706e-4780-91cb-56a83df63eea
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Exemplarische Vorgehensweise: Anpassen des Einf&#252;ge-, Update- und L&#246;schverhaltens von Entit&#228;tsklassen
Der [Object Relational Designer \(O\/R\-Designer\)](../data-tools/linq-to-sql-tools-in-visual-studio2.md) stellt eine visuelle Entwurfsoberfläche zum Erstellen und Bearbeiten von [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)]\-Klassen \(Entitätsklassen\) bereit, die auf Objekten in einer Datenbank basieren.Mithilfe von [LINQ to SQL](../Topic/LINQ%20to%20SQL.md) kann die LINQ\-Technologie für den Zugriff auf SQL\-Datenbanken verwendet werden.Weitere Informationen finden Sie unter [LINQ \(Language\-Integrated Query\)](../Topic/LINQ%20\(Language-Integrated%20Query\).md).  
  
 Standardmäßig wird die Logik für die Durchführung von Updates von der [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)]\-Laufzeit bereitgestellt.Basierend auf dem Schema der Tabelle \(den Spaltendefinitionen und den Primärschlüsselinformationen\) werden von der Laufzeit Standardanweisungen für Einfüge\-, Update\- und Löschvorgänge erstellt.Wenn Sie das Standardverhalten nicht verwenden möchten, können Sie das Updateverhalten konfigurieren und für erforderliche Einfüge\-, Update\- und Löschvorgänge, die für das Arbeiten mit Daten in der Datenbank notwendig sind, spezielle gespeicherte Prozeduren festlegen.Diese Vorgehensweise ist auch dann sinnvoll, wenn kein Standardverhalten erzeugt wird, z. B. wenn die Entitätsklassen Sichten zugeordnet sind.Das standardmäßige Updateverhalten kann auch dann überschrieben werden, wenn für die Datenbank der Tabellenzugriff über gespeicherte Prozeduren erforderlich ist.Weitere Informationen finden Sie unter [Anpassen von Operationen durch Verwenden gespeicherter Prozeduren](../Topic/Customizing%20Operations%20By%20Using%20Stored%20Procedures.md).  
  
> [!NOTE]
>  Für diese exemplarische Vorgehensweise ist die Verfügbarkeit der gespeicherten Prozeduren **InsertCustomer**, **UpdateCustomer** und **DeleteCustomer** für die Datenbank Northwind erforderlich.Ausführliche Informationen zum Erstellen dieser gespeicherten Prozeduren finden Sie unter [Exemplarische Vorgehensweise: Erstellen von aktualisierten gespeicherten Prozeduren für die Northwind\-Kundentabelle](../data-tools/walkthrough-creating-update-stored-procedures-for-the-northwind-customers-table.md).  
  
 In dieser exemplarischen Vorgehensweise werden die zu befolgenden Schritte dargestellt, um mithilfe von gespeicherten Prozeduren das LINQ to SQL\-Standardlaufzeitverhalten für das Speichern von Daten in einer Datenbank zu überschreiben.  
  
 In dieser exemplarischen Vorgehensweise wird gezeigt, wie Sie die folgenden Aufgaben ausführen:  
  
-   Erstellen einer neuen Windows Forms\-Anwendung und Hinzufügen einer [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)]\-Datei.  
  
-   Erstellen einer Entitätsklasse, die der Tabelle Customers der Datenbank Northwind zugeordnet ist.  
  
-   Erstellen einer Objektdatenquelle, die auf die Customer\-Klasse LINQ to SQL verweist.  
  
-   Erstellen eines Windows Form, das eine <xref:System.Windows.Forms.DataGridView> enthält, die an die Customer\-Klasse gebunden ist.  
  
-   Implementieren der Speicherfunktion für das Formular.  
  
-   Erstellen von <xref:System.Data.Linq.DataContext>\-Methoden durch Hinzufügen von gespeicherten Prozeduren zum [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].  
  
-   Konfigurieren der Customer\-Klasse, sodass sie gespeicherte Prozeduren für Einfüge\-, Update\- und Löschvorgänge verwendet.  
  
## Vorbereitungsmaßnahmen  
 Zum Durchführen dieser exemplarischen Vorgehensweise benötigen Sie Folgendes:  
  
-   Zugriff auf die SQL Server\-Version der Beispieldatenbank Northwind.Weitere Informationen finden Sie unter [Gewusst wie: Installieren von Beispieldatenbanken](../data-tools/how-to-install-sample-databases.md).  
  
-   Die gespeicherten Prozeduren **InsertCustomer**, **UpdateCustomer** und **DeleteCustomer** für die Datenbank Northwind.Weitere Informationen finden Sie unter [Exemplarische Vorgehensweise: Erstellen von aktualisierten gespeicherten Prozeduren für die Northwind\-Kundentabelle](../data-tools/walkthrough-creating-update-stored-procedures-for-the-northwind-customers-table.md).  
  
## Erstellen einer Anwendung und Hinzufügen von LINQ to SQL\-Klassen  
 Da Sie mit [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)]\-Klassen arbeiten und die Daten in einem Windows Form angezeigt werden, erstellen Sie eine neue Windows Forms\-Anwendung, und fügen Sie eine LINQ to SQL\-Klassendatei hinzu.  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
#### So erstellen Sie ein neues Windows\-Anwendungsprojekt, das LINQ to SQL\-Klassen enthält  
  
1.  Erstellen Sie im Menü **Datei** ein neues Projekt.  
  
2.  Nennen Sie das Projekt UpdatingwithSProcsWalkthrough.  
  
    > [!NOTE]
    >  Der [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] wird in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]\- und C\#\-Projekten unterstützt.Erstellen Sie das neue Projekt daher in einer der beiden Sprachen.  
  
3.  Klicken Sie auf die Vorlage **Windows Forms\-Anwendung** und anschließend auf **OK**.Weitere Informationen finden Sie unter [Clientanwendungen](../Topic/Developing%20Client%20Applications%20with%20the%20.NET%20Framework.md).  
  
     Das Projekt UpdatingwithSProcsWalkthrough wird erstellt und zum **Projektmappen\-Explorer** hinzugefügt.  
  
4.  Klicken Sie im Menü **Projekt** auf **Neues Element hinzufügen**.  
  
5.  Klicken Sie auf die Vorlage **LINQ to SQL\-Klassen**, und geben Sie im Feld **Name** den Namen "Northwind.dbml" ein.  
  
6.  Klicken Sie auf **Hinzufügen**.  
  
     Dem Projekt wird eine leere LINQ to SQL\-Klassendatei \(Northwind.dbml\) hinzugefügt, und der [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] wird geöffnet.  
  
## Erstellen der Entitätsklasse Customer und einer Objektdatenquelle  
 Erstellen Sie [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)]\-Klassen, die den Datenbanktabellen zugeordnet sind, indem Sie Tabellen von **Server\-Explorer**\/**Datenbank\-Explorer** auf [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] ziehen.Sie erhalten LINQ to SQL\-Entitätsklassen, die den Tabellen in der Datenbank zugeordnet sind.Nachdem die Entitätsklassen erstellt wurden, können sie wie andere Klassen mit öffentlichen Eigenschaften als Objektdatenquellen dienen.  
  
#### So erstellen Sie eine Customer\-Entitätsklasse und konfigurieren damit eine Datenquelle  
  
1.  Suchen Sie im **Server\-Explorer**\/**Datenbank\-Explorer** in der SQL Server\-Version der Beispieldatenbank Northwind die Tabelle Customer.Weitere Informationen finden Sie unter [Gewusst wie: Verbinden mit der Datenbank Northwind](../data-tools/how-to-connect-to-the-northwind-database.md).  
  
2.  Ziehen Sie den Knoten **Customers** von **Server\-Explorer**\/**Datenbank\-Explorer** auf die [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]\-Oberfläche.  
  
     Eine Entitätsklasse mit dem Namen **Customer** wird erstellt.Sie verfügt über Eigenschaften, die den Spalten in der Tabelle Customers entsprechen.Die Entitätsklasse wird **Customer** \(nicht **Customers**\) genannt, da sie einem einzelnen Kunden aus der Tabelle Customers entspricht.  
  
    > [!NOTE]
    >  Dieses Umbenennungsverhalten wird als *Pluralisierung* bezeichnet.Es kann im [Dialogfeld "Optionen"](../ide/reference/options-dialog-box-visual-studio.md) an\- oder ausgeschaltet werden.Weitere Informationen finden Sie unter [Vorgehensweise: An\- und Ausschalten der Pluralisierung \(O\/R\-Designer\)](../data-tools/how-to-turn-pluralization-on-and-off-o-r-designer.md).  
  
3.  Klicken Sie im Menü **Erstellen** auf **UpdatingwithSProcsWalkthrough erstellen**, um das Projekt zu erstellen.  
  
4.  Klicken Sie im Menü **Daten** auf **Datenquellen anzeigen**.  
  
5.  Klicken Sie im **Datenquellenfenster** auf **Neue Datenquelle hinzufügen**.  
  
6.  Klicken Sie auf der Seite **Datenquellentyp auswählen** auf **Objekt** und anschließend auf **Weiter**.  
  
7.  Erweitern Sie den Knoten **UpdatingwithSProcsWalkthrough**, suchen Sie die Klasse **Customer**, und wählen Sie diese aus.  
  
    > [!NOTE]
    >  Wenn die Klasse **Customer** nicht verfügbar ist, beenden Sie den Assistenten, erstellen Sie das Projekt, und führen Sie den Assistenten erneut aus.  
  
8.  Klicken Sie auf **Fertig stellen**, um die Datenquelle zu erstellen, und fügen Sie die Entitätsklasse **Customer** zum Fenster **Datenquellen** hinzu.  
  
## Erstellen einer DataGridView, um die Kundendaten auf einem Windows Form anzuzeigen  
 Erstellen Sie Steuerelemente, die an Entitätsklassen gebunden sind, indem Sie [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)]\-Datenquellenelemente vom Fenster **Datenquellen** auf ein Windows Form ziehen.  
  
#### So fügen Sie Steuerelemente hinzu, die an Entitätsklassen gebunden sind  
  
1.  Öffnen Sie Form1 in der Entwurfsansicht.  
  
2.  Ziehen Sie aus dem Fenster **Datenquellen** den Knoten **Customer** auf Form1.  
  
    > [!NOTE]
    >  Klicken Sie im Menü **Daten** auf **Datenquellen anzeigen**, um das Fenster **Datenquellen** anzuzeigen.  
  
3.  Öffnen Sie Form1 im Code\-Editor.  
  
4.  Fügen Sie dem Formular den folgenden Code hinzu, sodass er global für das Formular gilt und außerhalb einer bestimmten Methode, jedoch innerhalb der Klasse Form1 steht:  
  
    ```vb#  
    Private NorthwindDataContext1 As New NorthwindDataContext  
    ```  
  
    ```c#  
    private NorthwindDataContext northwindDataContext1  
        = new NorthwindDataContext();  
  
    ```  
  
5.  Erstellen Sie einen Ereignishandler für das `Form_Load`\-Ereignis, und fügen Sie dem Handler den folgenden Code hinzu:  
  
    ```vb#  
    CustomerBindingSource.DataSource = NorthwindDataContext1.Customers  
    ```  
  
    ```c#  
    customerBindingSource.DataSource  
        = northwindDataContext1.Customers;  
  
    ```  
  
## Implementieren der Speicherfunktionalität  
 Die Schaltfläche zum Speichern ist standardmäßig nicht aktiviert, und die Speicherfunktionalität ist nicht implementiert.Auch wird bei Erstellung datengebundener Steuerelemente für Objektdatenquellen nicht automatisch Code hinzugefügt, um geänderte Daten in der Datenbank zu speichern.In diesem Abschnitt wird erklärt, wie die Schaltfläche zum Speichern aktiviert und die Speicherfunktionalität für [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)]\-Objekte implementiert wird.  
  
#### So implementieren Sie die Speicherfunktionalität  
  
1.  Öffnen Sie Form1 in der Entwurfsansicht.  
  
2.  Wählen Sie im **CustomersBindingNavigator** die Schaltfläche zum Speichern \(die Schaltfläche mit dem Diskettensymbol\) aus.  
  
3.  Legen Sie im Fenster **Eigenschaften** die Eigenschaft **Aktiviert** auf **True** fest.  
  
4.  Doppelklicken Sie auf die Schaltfläche zum Speichern, um einen Ereignishandler zu erstellen und zum Code\-Editor zu wechseln.  
  
5.  Fügen Sie dem Ereignishandler für die Speichern\-Schaltfläche den folgenden Code hinzu:  
  
    ```vb#  
    NorthwindDataContext1.SubmitChanges()  
    ```  
  
    ```c#  
    northwindDataContext1.SubmitChanges();  
    ```  
  
## Überschreiben des Standardverhaltens für Aktualisierungen \(Einfüge\-, Aktualisierungs\- und Löschvorgänge\)  
  
#### So überschreiben Sie das standardmäßige Updateverhalten  
  
1.  Öffnen Sie im [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] die LINQ to SQL\-Datei.\(Doppelklicken Sie im **Projektmappen\-Explorer** auf die Datei **Northwind.dbml**\).  
  
2.  Erweitern Sie im **Server\-Explorer**\/**Datenbank\-Explorer** den Knoten **Gespeicherte Prozeduren** der Datenbank Northwind, und suchen Sie die gespeicherten Prozeduren **InsertCustomers**, **UpdateCustomers** und **DeleteCustomers**.  
  
3.  Ziehen Sie alle drei gespeicherten Prozeduren auf den [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].  
  
     Die gespeicherten Prozeduren werden dem Methodenbereich als <xref:System.Data.Linq.DataContext>\-Methoden hinzugefügt.Weitere Informationen finden Sie unter [DataContext\-Methoden \(O\/R\-Designer\)](../data-tools/datacontext-methods-o-r-designer.md).  
  
4.  Wählen Sie im [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] die Entitätsklasse **Customer** aus.  
  
5.  Wählen Sie im Fenster **Eigenschaften** die **Einfügen**\-Eigenschaft aus.  
  
6.  Klicken Sie auf die Auslassungszeichen \(...\) neben **Laufzeit verwenden**, um das Dialogfeld **Verhalten konfigurieren** zu öffnen.  
  
7.  Wählen Sie **Anpassen** aus.  
  
8.  Wählen Sie aus der Liste **Anpassen** die **InsertCustomers**\-Methode aus.  
  
9. Klicken Sie auf **Übernehmen**, um die Konfiguration für die ausgewählte Klasse und das ausgewählte Verhalten zu speichern.  
  
    > [!NOTE]
    >  Sie können mit der Konfiguration des Verhaltens jeder Klasse\/Verhalten\-Kombination fortfahren, solange Sie nach jeder Änderung auf **Übernehmen** klicken.Wenn Sie eine Klasse oder ein Verhalten ändern bevor Sie auf **Übernehmen** klicken, wird ein Warnungsdialogfeld angezeigt, das Ihnen Gelegenheit bietet, alle Änderungen zu übernehmen.  
  
10. Wählen Sie aus der Liste **Verhalten** die Option **Aktualisieren** aus.  
  
11. Wählen Sie **Anpassen** aus.  
  
12. Wählen Sie in der Liste **Anpassen** die **UpdateCustomers**\-Methode aus.  
  
     Überprüfen Sie die Liste der **Methodenargumente** und **Klasseneigenschaften**, und beachten Sie, dass für einige Spalten in der Tabelle zwei **Methodenargumente** sowie zwei **Klasseneigenschaften** vorhanden sind.Dies macht es einfacher, Änderungen zu verfolgen und Anweisungen zur Überprüfung von Parallelitätsverletzungen zu erstellen.  
  
13. Ordnen Sie das **Original\_CustomerID**\-Methodenargument der Klasseneigenschaft **CustomerID \(Original\)** zu.  
  
    > [!NOTE]
    >  Standardmäßig werden Methodenargumente Klasseneigenschaften zugeordnet, wenn die Namen übereinstimmen.Wenn Eigenschaftennamen geändert werden und die Namen von Tabelle und Entitätsklasse nicht mehr übereinstimmen, kann es erforderlich sein, die entsprechende zuzuordnende Klasseneigenschaft auszuwählen, wenn die korrekte Zuordnung vom O\/R\-Designer nicht festgestellt werden kann.Wenn die Methodenargumente nicht über gültige Klasseneigenschaften für die Zuordnung verfügen, können Sie zusätzlich den Wert **Klasseneigenschaften** auf **\(Keine\)** festlegen.  
  
14. Klicken Sie auf **Übernehmen**, um die Konfiguration für die ausgewählte Klasse und das ausgewählte Verhalten zu speichern.  
  
15. Wählen Sie aus der Liste **Verhalten** die Option **Löschen** aus.  
  
16. Wählen Sie **Anpassen** aus.  
  
17. Wählen Sie in der Liste **Anpassen** die **DeleteCustomers**\-Methode aus.  
  
18. Ordnen Sie das **Original\_CustomerID**\-Methodenargument der Klasseneigenschaft **CustomerID \(Original\)** zu.  
  
19. Klicken Sie auf **OK**.  
  
> [!NOTE]
>  Auch wenn es kein Problem in dieser exemplarischen Vorgehensweise darstellt, ist Folgendes zu beachten: [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] behandelt bei Einfüge\- und Updatevorgängen die datenbankgenerierten Werte bei Identitätsspalten \(automatische Inkrementierung\) sowie bei ROWGUID\- \(datenbankgenerierte GUID\) und Timestamp\-Spalten automatisch.Datenbankgenerierte Werte in anderen Spaltentypen führen unerwartet zu einem NULL\-Wert.Um die datenbankgenerierten Werte zurückzugeben, sollte manuell <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A> auf `true` und <xref:System.Data.Linq.Mapping.ColumnAttribute.AutoSync%2A> auf eine der folgenden Einstellungen festgelegt werden: <xref:System.Data.Linq.Mapping.AutoSync>, <xref:System.Data.Linq.Mapping.AutoSync> oder <xref:System.Data.Linq.Mapping.AutoSync>.  
  
## Testen der Anwendung  
 Führen Sie die Anwendung erneut aus, um zu überprüfen, ob der Kundendatensatz in der Datenbank von der gespeicherten Prozedur **UpdateCustomers** ordnungsgemäß aktualisiert wird.  
  
#### So testen Sie die Anwendung  
  
1.  Drücken Sie F5.  
  
2.  Ändern Sie einen Datensatz im Raster, um das Updateverhalten zu testen.  
  
3.  Fügen Sie einen neuen Datensatz hinzu, um das Einfügeverhalten zu testen.  
  
4.  Klicken Sie auf die Speichern\-Schaltfläche, um die Änderungen in der Datenbank zu speichern.  
  
5.  Schließen Sie das Formular.  
  
6.  Drücken Sie F5, und überprüfen Sie, ob der aktualisierte Datensatz und der neu eingefügte Datensatz erhalten bleiben.  
  
7.  Löschen Sie den in Schritt 3 erstellten neuen Datensatz, um das Löschverhalten zu testen.  
  
8.  Klicken Sie auf die Speichern\-Schaltfläche, um die Änderungen zu übermitteln und den gelöschten Datensatz aus der Datenbank zu entfernen.  
  
9. Schließen Sie das Formular.  
  
10. Drücken Sie F5 und überprüfen Sie, ob der gelöschte Datensatz aus der Datenbank entfernt wurde.  
  
    > [!NOTE]
    >  Wenn Ihre Anwendung SQL Server Express Edition verwendet, werden beim Drücken von F5 in Schritt 10 die Änderungen möglicherweise nicht angezeigt. Dies ist abhängig vom Wert der Eigenschaft **Ins Ausgabeverzeichnis kopieren** der Datenbankdatei.Weitere Informationen finden Sie unter [Gewusst wie: Verwalten von lokalen Datendateien im Projekt](../data-tools/how-to-manage-local-data-files-in-your-project.md).  
  
## Nächste Schritte  
 Je nach den Anforderungen Ihrer Anwendung sollten Sie nach dem Erstellen von [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)]\-Entitätsklassen mehrere Schritte ausführen.Zu den möglichen Verbesserungen, die Sie an dieser Anwendung vornehmen können, gehören die folgenden:  
  
-   Implementieren der Parallelitätsprüfung während der Durchführung von Updates.Weitere Informationen finden Sie unter [Vollständige Parallelität: Übersicht](../Topic/Optimistic%20Concurrency:%20Overview.md).  
  
-   Hinzufügen von LINQ\-Abfragen, um Daten zu filtern.Weitere Informationen finden Sie unter [Introduction to LINQ Queries \(C\#\)](/dotnet/csharp/programming-guide/concepts/linq/introduction-to-linq-queries).  
  
## Siehe auch  
 [Object Relational Designer \(O\/R\-Designer\)](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [LINQ to SQL](../Topic/LINQ%20to%20SQL.md)   
 [LINQ to SQL\-Abfragen](../Topic/LINQ%20to%20SQL%20Queries.md)   
 [DataContext\-Methoden \(O\/R\-Designer\)](../data-tools/datacontext-methods-o-r-designer.md)   
 [Vorgehensweise: Zuweisen von gespeicherten Prozeduren zur Durchführung von Update\-, Einfüge\- und Löschvorgängen \(O\/R\-Designer\)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md)   
 [PAVE What's New for Data Application Development in Visual Studio 2012](http://msdn.microsoft.com/de-de/3d50d68f-5f44-4915-842f-6d42fce793f1)