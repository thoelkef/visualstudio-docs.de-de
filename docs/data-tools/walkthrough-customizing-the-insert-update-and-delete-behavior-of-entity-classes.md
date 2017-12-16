---
title: "Exemplarische Vorgehensweise: Anpassen der Insert, update und delete Verhalten von Entitätsklassen | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
ms.assetid: 03ff1146-706e-4780-91cb-56a83df63eea
caps.latest.revision: "3"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.openlocfilehash: 2727f17665d845029fcf32dbcd12dd7603dad519
ms.sourcegitcommit: f0ddee934713ea9126fa107018a57a94a05eafd3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/12/2017
---
# <a name="walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes"></a>Exemplarische Vorgehensweise: Anpassen der Insert, update und delete Verhalten von Entitätsklassen
Die [LINQ to SQL-Tools in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) bietet eine visuelle Entwurfsoberfläche zum Erstellen und Bearbeiten von [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] Klassen (Entität), die auf Objekte in einer Datenbank basieren. Mithilfe von [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index), können Sie LINQ-Technologie für den Zugriff auf SQL-Datenbanken. Weitere Informationen finden Sie unter [LINQ (Language-Integrated Query, sprachintegrierte Abfrage)](/dotnet/csharp/linq/).  
  
Standardmäßig wird die Logik für die Durchführung von Updates von der [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)]-Laufzeit bereitgestellt. Basierend auf dem Schema der Tabelle (den Spaltendefinitionen und den Primärschlüsselinformationen) werden von der Laufzeit Standardanweisungen für Einfüge-, Update- und Löschvorgänge erstellt. Wenn Sie das Standardverhalten nicht verwenden möchten, können Sie das Updateverhalten konfigurieren und für erforderliche Einfüge-, Update- und Löschvorgänge, die für das Arbeiten mit Daten in der Datenbank notwendig sind, spezielle gespeicherte Prozeduren festlegen. Diese Vorgehensweise ist auch dann sinnvoll, wenn kein Standardverhalten erzeugt wird, z. B. wenn die Entitätsklassen Ansichten zugeordnet sind. Das standardmäßige Updateverhalten kann auch dann überschrieben werden, wenn für die Datenbank der Tabellenzugriff über gespeicherte Prozeduren erforderlich ist. Weitere Informationen finden Sie unter [anpassen Operations By Using Stored Procedures](/dotnet/framework/data/adonet/sql/linq/customizing-operations-by-using-stored-procedures).  
  
> [!NOTE]
>  Diese exemplarische Vorgehensweise erfordert die Verfügbarkeit der **InsertCustomer**, **UpdateCustomer**, und **DeleteCustomer** gespeicherte Prozeduren für die Datenbank Northwind.  
  
In dieser exemplarischen Vorgehensweise werden die zu befolgenden Schritte dargestellt, um mithilfe von gespeicherten Prozeduren das LINQ to SQL-Standardlaufzeitverhalten für das Speichern von Daten in einer Datenbank zu überschreiben.  
  
In dieser exemplarischen Vorgehensweise wird gezeigt, wie Sie die folgenden Aufgaben ausführen:  
  
-   Erstellen einer neuen Windows Forms-Anwendung und Hinzufügen einer [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)]-Datei.  
  
-   Erstellen einer Entitätsklasse, die der Tabelle Customers der Datenbank Northwind zugeordnet ist.  
  
-   Erstellen einer Objektdatenquelle, die auf die Customer-Klasse LINQ to SQL verweist.  
  
-   Erstellen eines Windows Form, das eine <xref:System.Windows.Forms.DataGridView> enthält, die an die Customer-Klasse gebunden ist.  
  
-   Implementieren der Speicherfunktion für das Formular.  
  
-   Erstellen von <xref:System.Data.Linq.DataContext>-Methoden durch Hinzufügen von gespeicherten Prozeduren zum [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].  
  
-   Konfigurieren der Customer-Klasse, sodass sie gespeicherte Prozeduren für Einfüge-, Update- und Löschvorgänge verwendet.  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
In dieser exemplarischen Vorgehensweise werden die SQL Server Express LocalDB und der Beispieldatenbank Northwind verwendet.  
  
1.  Wenn Sie nicht über SQL Server Express LocalDB verfügen, installieren Sie es entweder aus der [Downloadseite für SQL Server-Editionen](https://www.microsoft.com/en-us/server-cloud/Products/sql-server-editions/sql-server-express.aspx), oder über die **Installer für Visual Studio**. In der Visual Studio-Installer können SQL Server Express LocalDB installiert werden als Teil der **datenspeicherung und Verarbeitung** arbeitsauslastung oder als eine einzelne Komponente.  
  
2.  Installieren Sie die Beispieldatenbank Northwind, indem folgende Schritte:  

    1. Öffnen Sie in Visual Studio die **Objekt-Explorer von SQL Server** Fenster. (Objekt-Explorer von SQL Server installiert ist, als Teil der **datenspeicherung und Verarbeitung** arbeitsauslastung in der Visual Studio-Installer.) Erweitern Sie die **SQL Server** Knoten. Rechtsklicken Sie auf der LocalDB-Instanz, und wählen Sie **neue Abfrage...** .  

       Ein Abfrage-Editorfenster wird geöffnet.  

    2. Kopieren der [Northwind Transact-SQL-Skript](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) in die Zwischenablage. Dieses T-SQL-Skript die Northwind-Datenbank von Grund auf neu erstellt und mit Daten aufgefüllt.  

    3. Fügen Sie das T-SQL-Skript im Abfrage-Editor, und wählen Sie dann die **Execute** Schaltfläche.  

       Nach kurzer Zeit die Abfrage die Ausführung abgeschlossen ist, und die Northwind-Datenbank wird erstellt.  
  
## <a name="creating-an-application-and-adding-linq-to-sql-classes"></a>Erstellen einer Anwendung und Hinzufügen von LINQ to SQL-Klassen  
Da Sie mit [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)]-Klassen arbeiten und die Daten in einem Windows Form angezeigt werden, erstellen Sie eine neue Windows Forms-Anwendung, und fügen Sie eine LINQ to SQL-Klassendatei hinzu.  
  
[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
#### <a name="to-create-a-new-windows-forms-application-project-that-contains-linq-to-sql-classes"></a>So erstellen Sie ein neues Windows Forms-Anwendungsprojekt enthält, die LINQ to SQL-Klassen  
  
1. In Visual Studio auf die **Datei** klicken Sie im Menü **neu**, **Projekt...** .  
  
2. Erweitern Sie entweder **Visual C#-** oder **Visual Basic** im linken Bereich, und wählen Sie dann **klassische Windows-Desktop**.  

3. Wählen Sie im mittleren Bereich die **Windows Forms-App** Projekttyp.  

4. Nennen Sie das Projekt **UpdatingWithSProcsWalkthrough**, und wählen Sie dann **OK**. 
  
     Die **UpdatingWithSProcsWalkthrough** Projekt wird erstellt und hinzugefügt **Projektmappen-Explorer**.  
  
4.  Klicken Sie im Menü **Projekt** auf **Neues Element hinzufügen**.  
  
5.  Klicken Sie auf die **LINQ to SQL-Klassen** Vorlage und Typ **Northwind.dbml** in der **Namen** Feld.  
  
6.  Klicken Sie auf **Hinzufügen**.  
  
     Dem Projekt wird eine leere LINQ to SQL-Klassendatei (Northwind.dbml) hinzugefügt, und der [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] wird geöffnet.  
  
## <a name="creating-the-customer-entity-class-and-object-data-source"></a>Erstellen der Entitätsklasse Customer und einer Objektdatenquelle  
 Erstellen Sie [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] Klassen, die an den Datenbanktabellen zugeordnet sind, ziehen Sie Tabellen aus **Server-Explorer**/**Datenbank-Explorer** auf die [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]. Sie erhalten LINQ to SQL-Entitätsklassen, die den Tabellen in der Datenbank zugeordnet sind. Nachdem die Entitätsklassen erstellt wurden, können sie wie andere Klassen mit öffentlichen Eigenschaften als Objektdatenquellen dienen.  
  
#### <a name="to-create-a-customer-entity-class-and-configure-a-data-source-with-it"></a>So erstellen Sie eine Customer-Entitätsklasse und konfigurieren damit eine Datenquelle  
  
1.  In **Server-Explorer**/**Datenbank-Explorer**, suchen Sie die Customer-Tabelle in der SQL Server-Version der Northwind-Beispieldatenbank. 
  
2.  Ziehen Sie die **Kunden** Knoten aus **Server-Explorer**/**Datenbank-Explorer** auf die [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] Oberfläche.  
  
     Eine Entitätsklasse **Kunden** wird erstellt. Sie verfügt über Eigenschaften, die den Spalten in der Tabelle Customers entsprechen. Die Entitätsklasse heißt **Kunden** (nicht **Kunden**), da es einen einzelnen Kunden aus der Customers-Tabelle darstellt.  
  
    > [!NOTE]
    >  Dieses Umbenennungsverhalten wird aufgerufen, *Pluralisierung*. Es kann sein aktiviert oder deaktiviert der [Optionen (Dialogfeld)](../ide/reference/options-dialog-box-visual-studio.md). Weitere Informationen finden Sie unter [Vorgehensweise: Aktivieren Sie Pluralisierung ein, und deaktivieren (O/R-Designer)](../data-tools/how-to-turn-pluralization-on-and-off-o-r-designer.md).  
  
3.  Auf der **erstellen** Menü klicken Sie auf **UpdatingwithSProcsWalkthrough erstellen** zum Erstellen des Projekts.  
  
4.  Klicken Sie im Menü **Daten** auf **Datenquellen anzeigen**.  
  
5.  Klicken Sie im **Datenquellenfenster** auf **Neue Datenquelle hinzufügen**.  
  
6.  Klicken Sie auf **Objekt** auf die **wählen Sie einen Datenquellentyp** Seite, und klicken Sie dann auf **Weiter**.  
  
7.  Erweitern Sie die **UpdatingwithSProcsWalkthrough** Knoten suchen, und wählen Sie die **Kunden** Klasse.  
  
    > [!NOTE]
    >  Wenn die **Kunden** Klasse ist nicht verfügbar, beenden Sie den Assistenten, erstellen Sie das Projekt und führen Sie den Assistenten erneut aus.  
8.  Klicken Sie auf **Fertig stellen** zum Erstellen der Datenquelle und Hinzufügen der **Kunden** Entitätsklasse, die **Datenquellen** Fenster.  
  
## <a name="creating-a-datagridview-to-display-the-customer-data-on-a-windows-form"></a>Erstellen einer DataGridView, um die Kundendaten auf einem Windows Form anzuzeigen  
 Erstellen Sie Steuerelemente, die an Entitätsklassen gebunden sind, durch Ziehen von [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] -Datenquellenelemente vom der **Datenquellen** auf einem Windows Form.  
  
#### <a name="to-add-controls-that-are-bound-to-the-entity-classes"></a>So fügen Sie Steuerelemente hinzu, die an Entitätsklassen gebunden sind  
  
1.  Öffnen Sie Form1 in der Entwurfsansicht.  
  
2.  Aus der **Datenquellen** Fenster, ziehen Sie die **Kunden** Knoten auf Form1.  
  
    > [!NOTE]
    >  Zum Anzeigen der **Datenquellen** Fenster, klicken Sie auf **Datenquellen anzeigen** auf die **Daten** Menü.  
  
3.  Öffnen Sie im Code-Editor Form1.  
  
4.  Fügen Sie dem Formular den folgenden Code hinzu, sodass er global für das Formular gilt und außerhalb einer bestimmten Methode, jedoch innerhalb der Klasse Form1 steht:  
  
    ```vb  
    Private NorthwindDataContext1 As New NorthwindDataContext  
    ```  
  
    ```csharp  
    private NorthwindDataContext northwindDataContext1  
        = new NorthwindDataContext();    
    ```  
  
5.  Erstellen Sie einen Ereignishandler für das `Form_Load`-Ereignis, und fügen Sie dem Handler den folgenden Code hinzu:  
  
    ```vb  
    CustomerBindingSource.DataSource = NorthwindDataContext1.Customers  
    ```  
  
    ```csharp  
    customerBindingSource.DataSource  
        = northwindDataContext1.Customers;    
    ```  
  
## <a name="implementing-save-functionality"></a>Implementieren der Speicherfunktionalität  
 Die Schaltfläche zum Speichern ist standardmäßig nicht aktiviert, und die Speicherfunktionalität ist nicht implementiert. Auch wird bei Erstellung datengebundener Steuerelemente für Objektdatenquellen nicht automatisch Code hinzugefügt, um geänderte Daten in der Datenbank zu speichern. In diesem Abschnitt wird erklärt, wie die Schaltfläche zum Speichern aktiviert und die Speicherfunktionalität für [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)]-Objekte implementiert wird.  
  
#### <a name="to-implement-save-functionality"></a>So implementieren Sie die Speicherfunktionalität  
  
1.  Öffnen Sie Form1 in der Entwurfsansicht.  
  
2.  Wählen Sie die Schaltfläche auf der **CustomerBindingNavigator** (die Schaltfläche mit dem Diskettensymbol).  
  
3.  In der **Eigenschaften** legen die **aktiviert** Eigenschaft **"true"**.  
  
4.  Doppelklicken Sie auf die Schaltfläche zum Speichern, um einen Ereignishandler zu erstellen und zum Code-Editor zu wechseln.  
  
5.  Fügen Sie dem Ereignishandler für die Schaltfläche zum Speichern den folgenden Code hinzu:  
  
    ```vb  
    NorthwindDataContext1.SubmitChanges()  
    ```  
  
    ```csharp  
    northwindDataContext1.SubmitChanges();  
    ```  
  
## <a name="overriding-the-default-behavior-for-performing-updates-inserts-updates-and-deletes"></a>Überschreiben des Standardverhaltens für Aktualisierungen (Einfüge-, Aktualisierungs- und Löschvorgänge)  
  
#### <a name="to-override-the-default-update-behavior"></a>So überschreiben Sie das standardmäßige Updateverhalten  
  
1.  Öffnen Sie im [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] die LINQ to SQL-Datei. (Doppelklicken Sie auf die **Northwind.dbml** Datei **Projektmappen-Explorer**.)  
  
2.  In **Server-Explorer**/**Datenbank-Explorer**, erweitern Sie die Datenbank Northwind **gespeicherte Prozeduren** Knoten, und suchen Sie die  **InsertCustomers**, **UpdateCustomers**, und **DeleteCustomers** gespeicherte Prozeduren.  
  
3.  Ziehen Sie alle drei gespeicherten Prozeduren auf den [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].  
  
     Die gespeicherten Prozeduren werden dem Methodenbereich als <xref:System.Data.Linq.DataContext>-Methoden hinzugefügt. Weitere Informationen finden Sie unter [DataContext-Methoden (O/R-Designer)](../data-tools/datacontext-methods-o-r-designer.md).  
  
4.  Wählen Sie die **Kunden** Entitätsklasse in der [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].  
  
5.  In der **Eigenschaften** wählen die **einfügen** Eigenschaft.  
  
6.  Klicken Sie auf die Auslassungspunkte (...) neben **Laufzeit** So öffnen die **Verhalten konfigurieren** (Dialogfeld).  
  
7.  Wählen Sie **anpassen**.  
  
8.  Wählen Sie die **InsertCustomers** Methode in der **anpassen** Liste.  
  
9. Klicken Sie auf **übernehmen** zum Speichern der Konfiguration für die ausgewählte Klasse und das Verhalten.  
  
    > [!NOTE]
    >  Sie können die Konfiguration des Verhaltens jeder Klasse/Verhalten-Kombination, solange Sie klicken Sie auf Weiter **übernehmen** nach jeder Änderung. Wenn Sie die Klasse oder das Verhalten ändern, bevor Sie auf **übernehmen**, ein Warnungsdialogfeld Gelegenheit bietet, alle Änderungen zu übernehmen, wird angezeigt.  
  
10. Wählen Sie **Update** in der **Verhalten** Liste.  
  
11. Wählen Sie **anpassen**.  
  
12. Wählen Sie die **UpdateCustomers** Methode in der **anpassen** Liste.  
  
     Überprüfen Sie die Liste der **Methodenargumente** und **Klasseneigenschaften** und beachten Sie, dass es zwei existieren **Methodenargumente** und zwei **Klasseneigenschaften**für einige Spalten in der Tabelle. Dies macht es einfacher, Änderungen zu verfolgen und Anweisungen zur Überprüfung von Parallelitätsverletzungen zu erstellen.  
  
13. Zuordnung der **Original_CustomerID** -Methodenargument der **CustomerID (Original)** Klasseneigenschaft.  
  
    > [!NOTE]
    >  Standardmäßig werden Methodenargumente Klasseneigenschaften zugeordnet, wenn die Namen übereinstimmen. Wenn Eigenschaftennamen geändert werden und die Namen von Tabelle und Entitätsklasse nicht mehr übereinstimmen, kann es erforderlich sein, die entsprechende zuzuordnende Klasseneigenschaft auszuwählen, wenn die korrekte Zuordnung vom O/R-Designer nicht festgestellt werden kann. Darüber hinaus Wenn Methodenargumente nicht über gültige Klasseneigenschaften für zuordnen verfügen, legen Sie die **Klasseneigenschaften** Wert **(keine)**.  
  
14. Klicken Sie auf **übernehmen** zum Speichern der Konfiguration für die ausgewählte Klasse und das Verhalten.  
  
15. Wählen Sie **löschen** in der **Verhalten** Liste.  
  
16. Wählen Sie **anpassen**.  
  
17. Wählen Sie die **DeleteCustomers** Methode in der **anpassen** Liste.  
  
18. Zuordnung der **Original_CustomerID** -Methodenargument der **CustomerID (Original)** Klasseneigenschaft.  
  
19. Klicken Sie auf **OK**.  
  
> [!NOTE]
>  Auch wenn es kein Problem in dieser exemplarischen Vorgehensweise darstellt, ist Folgendes zu beachten: [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] behandelt bei Einfüge- und Updatevorgängen die datenbankgenerierten Werte bei Identitätsspalten (automatische Inkrementierung) sowie bei ROWGUID- (datenbankgenerierte GUID) und Timestamp-Spalten automatisch. Datenbankgenerierte Werte in anderen Spaltentypen führen unerwartet zu einem NULL-Wert. Um die datenbankgenerierten Werte zurückzugeben, sollte manuell <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A> auf `true` und <xref:System.Data.Linq.Mapping.ColumnAttribute.AutoSync%2A> auf eine der folgenden Einstellungen festgelegt werden: <xref:System.Data.Linq.Mapping.AutoSync>, <xref:System.Data.Linq.Mapping.AutoSync> oder <xref:System.Data.Linq.Mapping.AutoSync>.  
  
## <a name="testing-the-application"></a>Testen der Anwendung  
 Führen Sie die Anwendung erneut aus, um zu überprüfen, ob die **UpdateCustomers** gespeicherte Prozedur richtig den Kundendatensatz in der Datenbank aktualisiert.  
  
#### <a name="to-test-the-application"></a>So testen Sie die Anwendung  
  
1.  Drücken Sie F5.  
  
2.  Ändern Sie einen Datensatz im Raster, um das Updateverhalten zu testen.  
  
3.  Fügen Sie einen neuen Datensatz hinzu, um das Einfügeverhalten zu testen.  
  
4.  Klicken Sie auf die Speichern-Schaltfläche, um die Änderungen in der Datenbank zu speichern.  
  
5.  Schließen Sie das Formular.  
  
6.  Drücken Sie F5, und überprüfen Sie, ob der aktualisierte Datensatz und der neu eingefügte Datensatz erhalten bleiben.  
  
7.  Löschen Sie den in Schritt 3 erstellten neuen Datensatz, um das Löschverhalten zu testen.  
  
8.  Klicken Sie auf die Speichern-Schaltfläche, um die Änderungen zu übermitteln und den gelöschten Datensatz aus der Datenbank zu entfernen.  
  
9. Schließen Sie das Formular.  
  
10. Drücken Sie F5 und überprüfen Sie, ob der gelöschte Datensatz aus der Datenbank entfernt wurde.  
  
    > [!NOTE]
    >  Wenn Ihre Anwendung je nach dem Wert des SQL Server Express Edition verwendet die **in Ausgabeverzeichnis kopieren** Eigenschaft der Datenbankdatei, die Änderungen möglicherweise nicht angezeigt, wenn Sie in Schritt 10 F5 drücken. 
  
## <a name="next-steps"></a>Nächste Schritte  
Je nach den Anforderungen Ihrer Anwendung sollten Sie nach dem Erstellen von [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)]-Entitätsklassen mehrere Schritte ausführen. Hier sind einige Verbesserungen, die Sie an dieser Anwendung vornehmen können:  
  
-   Implementieren der Parallelitätsprüfung während der Durchführung von Updates. Informationen finden Sie unter [vollständige Parallelität: Übersicht über](/dotnet/framework/data/adonet/sql/linq/optimistic-concurrency-overview).  
  
-   Hinzufügen von LINQ-Abfragen, um Daten zu filtern. Informationen finden Sie unter [Einführung in LINQ-Abfragen (c#)](/dotnet/csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).  
  
## <a name="see-also"></a>Siehe auch
[LINQ to SQL-Tools in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)     
[DataContext-Methoden](../data-tools/datacontext-methods-o-r-designer.md)   
[Vorgehensweise: Zuweisen von gespeicherten Prozeduren zum Ausführen von Updates, einfügungen und löschungen](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md)  
[LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)  
[LINQ to SQL-Abfragen](/dotnet/framework/data/adonet/sql/linq/linq-to-sql-queries)  
 