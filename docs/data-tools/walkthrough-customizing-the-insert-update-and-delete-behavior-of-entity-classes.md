---
title: 'Exemplarische Vorgehensweise: Anpassen des Einfüge-, Update- und delete-Verhalten von Entitätsklassen'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
ms.assetid: 03ff1146-706e-4780-91cb-56a83df63eea
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: fb01ef51c0a44047e2caf2f23634ebe741cd2dcb
ms.sourcegitcommit: f37affbc1b885dfe246d4b2c295a6538b383a0ca
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37174973"
---
# <a name="walkthrough-customize-the-insert-update-and-delete-behavior-of-entity-classes"></a>Exemplarische Vorgehensweise: Passen Sie das Einfüge-, Update- und löschverhaltens in Entitätsklassen an

Die [LINQ to SQL-tools in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) bietet eine visuelle Entwurfsoberfläche zum Erstellen und Bearbeiten von LINQ to SQL-Klassen (Entitätsklassen), die auf Objekte in einer Datenbank basieren. Mithilfe von [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index), können Sie LINQ-Technologie für den Zugriff auf SQL-Datenbanken. Weitere Informationen finden Sie unter [LINQ (Language-Integrated Query)](/dotnet/csharp/linq/).

Standardmäßig wird die Logik zum Durchführen von Aktualisierungen von LINQ to SQL-Laufzeit bereitgestellt. Der Laufzeit erstellt `Insert`, `Update`, und `Delete` Anweisungen basierend auf dem Schema der Tabelle (den Spaltendefinitionen und Primärschlüsselinformationen). Wenn Sie nicht das Standardverhalten verwenden möchten, können Sie das Updateverhalten konfigurieren und spezielle gespeicherte Prozeduren zum Durchführen der erforderlichen Einfüge-, Updates und löschungen erforderlich, um die Arbeit mit den Daten in der Datenbank festlegen. Diese Vorgehensweise ist auch dann sinnvoll, wenn kein Standardverhalten erzeugt wird, z. B. wenn die Entitätsklassen Ansichten zugeordnet sind. Das standardmäßige Updateverhalten kann auch dann überschrieben werden, wenn für die Datenbank der Tabellenzugriff über gespeicherte Prozeduren erforderlich ist. Weitere Informationen finden Sie unter [Anpassen von Operationen durch Verwendung von gespeicherten Prozeduren](/dotnet/framework/data/adonet/sql/linq/customizing-operations-by-using-stored-procedures).

> [!NOTE]
> Diese exemplarische Vorgehensweise setzt voraus, dass die **"InsertCustomer"**, **"UpdateCustomer"**, und **DeleteCustomer** gespeicherte Prozeduren für die Datenbank Northwind.

In dieser exemplarischen Vorgehensweise werden die zu befolgenden Schritte dargestellt, um mithilfe von gespeicherten Prozeduren das LINQ to SQL-Standardlaufzeitverhalten für das Speichern von Daten in einer Datenbank zu überschreiben.

Im Verlauf dieser exemplarischen Vorgehensweise erfahren Sie, wie Sie die folgenden Aufgaben ausführen:

-   Erstellen einer neuen Windows Forms-Anwendung und Hinzufügen einer LINQ to SQL-Datei darauf.

-   Erstellen einer Entitätsklasse, die den Northwind zugeordnet ist `Customers` Tabelle.

-   Erstellen eine Objektdatenquelle, die auf LINQ to SQL verweist `Customer` Klasse.

-   Erstellen Sie ein Windows-Formular, enthält eine <xref:System.Windows.Forms.DataGridView> , gebunden ist, um die `Customer` Klasse.

-   Implementieren der Speicherfunktion für das Formular.

-   Erstellen Sie <xref:System.Data.Linq.DataContext> -Methoden durch Hinzufügen von gespeicherten Systemprozeduren, die **O/R Designer**.

-   Konfigurieren der `Customer` Klasse zum Verwenden gespeicherter Prozeduren zum Ausführen von einfügungen, Updates und löscht.

## <a name="prerequisites"></a>Erforderliche Komponenten

In dieser exemplarischen Vorgehensweise verwendet SQL Server Express LocalDB und der Beispieldatenbank Northwind.

1.  Wenn Sie SQL Server Express LocalDB nicht haben, installieren Sie es entweder über die [Downloadseite für SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express), oder über die **Visual Studio-Installer**. In der **Visual Studio-Installer**, können Sie SQL Server Express LocalDB installieren, als Teil der **datenspeicherung und-Verarbeitung** Workload oder als eine einzelne Komponente.

2.  Installieren der Northwind-Beispieldatenbank mit folgenden Schritten:

    1. Öffnen Sie in Visual Studio die **Objekt-Explorer von SQL Server** Fenster. (**Objekt-Explorer von SQL Server** installiert als Teil der **datenspeicherung und-Verarbeitung** arbeitsauslastung in der **Visual Studio-Installer**.) Erweitern Sie die **SQL Server** Knoten. Mit der rechten Maustaste auf der LocalDB-Instanz, und wählen Sie **neue Abfrage**.

       Ein Abfrage-Editor-Fenster wird geöffnet.

    2. Kopieren der [Northwind Transact-SQL-Skript](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) in die Zwischenablage. Dieses T-SQL-Skript wird die Northwind-Datenbank von Grund auf neu erstellt und mit Daten aufgefüllt.

    3. Fügen Sie das T-SQL-Skript im Abfrage-Editor, und wählen Sie dann die **Execute** Schaltfläche.

       Klicken Sie nach kurzer Zeit die Ausführung die Abfrage abgeschlossen ist, und die Northwind-Datenbank wird erstellt.

## <a name="creating-an-application-and-adding-linq-to-sql-classes"></a>Erstellen einer Anwendung und Hinzufügen von LINQ to SQL-Klassen

Da Sie arbeiten mit LINQ to SQL-Klassen und Anzeigen der Daten in einem Windows Form, eine neue Windows Forms-Anwendung erstellen und Hinzufügen einer LINQ to SQL-Klassendatei.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-create-a-new-windows-forms-application-project-that-contains-linq-to-sql-classes"></a>So erstellen Sie ein neues Windows Forms-Anwendungsprojekt enthält, die LINQ to SQL-Klassen

1. In Visual Studio auf die **Datei** , wählen Sie im Menü **neu** > **Projekt**.

2. Erweitern Sie entweder **Visual C#-** oder **Visual Basic** wählen Sie im linken Bereich **Windows Desktop**.

3. Wählen Sie im mittleren Bereich die **Windows Forms-App** Projekttyp.

4. Nennen Sie das Projekt **UpdatingWithSProcsWalkthrough**, und wählen Sie dann **OK**.

     Die **UpdatingWithSProcsWalkthrough** Projekt wird erstellt und hinzugefügt **Projektmappen-Explorer**.

4.  Klicken Sie im Menü **Projekt** auf **Neues Element hinzufügen**.

5.  Klicken Sie auf die **LINQ to SQL-Klassen** Vorlage, und geben **Northwind.dbml** in die **Namen** Feld.

6.  Klicken Sie auf **Hinzufügen**.

     Eine leere LINQ to SQL-Klassendatei (**Northwind.dbml**) wird dem Projekt hinzugefügt und die **O/R Designer** wird geöffnet.

## <a name="create-the-customer-entity-class-and-object-data-source"></a>Erstellen Sie die Customer-Entität-Klasse und Objekt-Datenquelle

Erstellen von LINQ to SQL-Klassen, Datenbanktabellen zugeordnet sind, ziehen Sie Tabellen aus **Server-Explorer** oder **Datenbank-Explorer** auf die **O/R Designer**. Sie erhalten LINQ to SQL-Entitätsklassen, die den Tabellen in der Datenbank zugeordnet sind. Nachdem die Entitätsklassen erstellt wurden, können sie wie andere Klassen mit öffentlichen Eigenschaften als Objektdatenquellen dienen.

### <a name="to-create-a-customer-entity-class-and-configure-a-data-source-with-it"></a>So erstellen Sie eine Customer-Entitätsklasse und konfigurieren damit eine Datenquelle

1.  In **Server-Explorer** oder **Datenbank-Explorer**, suchen Sie die **Kunden** -Tabelle in SQL Server-Version der Northwind-Beispieldatenbank.

2.  Ziehen Sie die **Kunden** aus **Server-Explorer** oder **Datenbank-Explorer** auf der **O/R Designer* Oberfläche.

     Die Entitätsklasse **Kunden** erstellt wird. Sie verfügt über Eigenschaften, die den Spalten in der Tabelle Customers entsprechen. Die Entitätsklasse wird mit dem Namen **Kunden** (nicht **Kunden**) da es einen einzelnen Kunden aus der Customers-Tabelle darstellt.

    > [!NOTE]
    > Dieses Umbenennungsverhalten wird aufgerufen, *Pluralisierung*. Sie können aktiviert oder deaktiviert die [Abonnementoptionen](../ide/reference/options-dialog-box-visual-studio.md). Weitere Informationen finden Sie unter [Vorgehensweise: Aktivieren/Deaktivieren der Pluralisierung (O/R Designer)](../data-tools/how-to-turn-pluralization-on-and-off-o-r-designer.md).

3.  Auf der **erstellen** Menü klicken Sie auf **UpdatingwithSProcsWalkthrough erstellen** zum Erstellen des Projekts.

4.  Klicken Sie im Menü **Daten** auf **Datenquellen anzeigen**.

5.  Klicken Sie im **Datenquellenfenster** auf **Neue Datenquelle hinzufügen**.

6.  Klicken Sie auf **Objekt** auf die **wählen Sie einen Datenquellentyp** Seite, und klicken Sie dann auf **Weiter**.

7.  Erweitern Sie die **UpdatingwithSProcsWalkthrough** Knoten, und wählen Sie die **Kunden** Klasse.

    > [!NOTE]
    > Wenn die **Kunden** Klasse ist nicht verfügbar, den Assistenten abbrechen, erstellen Sie das Projekt und führen Sie den Assistenten erneut aus.
8.  Klicken Sie auf **Fertig stellen** zum Erstellen der Datenquelle und Hinzufügen der **Kunden** Entitätsklasse, um die **Datenquellen** Fenster.

## <a name="create-a-datagridview-to-display-the-customer-data-on-a-windows-form"></a>Erstellen einer DataGridView, um die Kundendaten in einem Windows Form anzuzeigen

Erstellen Sie Steuerelemente, die an Entitätsklassen gebunden sind, durch Ziehen von LINQ zu SQL-Datenquellenelemente aus der **Datenquellen** in ein Windows-Formular.

### <a name="to-add-controls-that-are-bound-to-the-entity-classes"></a>So fügen Sie Steuerelemente hinzu, die an Entitätsklassen gebunden sind

1.  Open **Form1** in der Entwurfsansicht.

2.  Von der **Datenquellen** ziehen Sie die **Kunden** Knoten **Form1**.

    > [!NOTE]
    > Zum Anzeigen der **Datenquellen** Fenster, klicken Sie auf **Datenquellen anzeigen** auf die **Daten** Menü.

3.  Open **Form1** im Code-Editor.

4.  Fügen Sie den folgenden Code in das Formular, die global für das Formular, außerhalb einer bestimmten Methode, jedoch innerhalb der `Form1` Klasse:

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

## <a name="implement-save-functionality"></a>Implementieren der Speicherfunktion

Die Schaltfläche zum Speichern ist standardmäßig nicht aktiviert, und die Speicherfunktionalität ist nicht implementiert. Auch wird bei Erstellung datengebundener Steuerelemente für Objektdatenquellen nicht automatisch Code hinzugefügt, um geänderte Daten in der Datenbank zu speichern. In diesem Abschnitt wird erläutert, wie das Speichern aktiviert Schaltfläche und die Speicherfunktionalität für LINQ auf SQL-Objekte implementieren.

### <a name="to-implement-save-functionality"></a>So implementieren Sie die Speicherfunktionalität

1.  Open **Form1** in der Entwurfsansicht.

2.  Aktivieren Sie das Speichern in auf die Schaltfläche der **CustomersBindingNavigator** (die Schaltfläche mit dem Diskettensymbol).

3.  In der **Eigenschaften** legen die **aktiviert** Eigenschaft **"true"**.

4.  Doppelklicken Sie auf die Schaltfläche zum Speichern, um einen Ereignishandler zu erstellen und zum Code-Editor zu wechseln.

5.  Fügen Sie dem Ereignishandler für die Schaltfläche zum Speichern den folgenden Code hinzu:

    ```vb
    NorthwindDataContext1.SubmitChanges()
    ```

    ```csharp
    northwindDataContext1.SubmitChanges();
    ```

## <a name="override-the-default-behavior-for-performing-updates-inserts-updates-and-deletes"></a>Überschreiben Sie das Standardverhalten für Aktualisierungen (einfügungen, Updates und löschungen)

### <a name="to-override-the-default-update-behavior"></a>So überschreiben Sie das standardmäßige Updateverhalten

1.  Öffnen Sie die LINQ to SQL-Datei in die **O/R Designer**. (Doppelklicken Sie auf die **Northwind.dbml** Datei **Projektmappen-Explorer**.)

2.  In **Server-Explorer** oder **Datenbank-Explorer**, erweitern Sie die Datenbank Northwind **gespeicherte Prozeduren** Knoten, und suchen Sie die **InsertCustomers**, **UpdateCustomers**, und **DeleteCustomers** gespeicherte Prozeduren.

3.  Ziehen Sie alle drei gespeicherte Prozeduren auf die **O/R Designer**.

     Die gespeicherten Prozeduren werden dem Methodenbereich als <xref:System.Data.Linq.DataContext>-Methoden hinzugefügt. Weitere Informationen finden Sie unter [DataContext-Methoden (O/R Designer)](../data-tools/datacontext-methods-o-r-designer.md).

4.  Wählen Sie die **Kunden** Entitätsklasse in der **O/R Designer**.

5.  In der **Eigenschaften** wählen Sie im Fenster der **einfügen** Eigenschaft.

6.  Klicken Sie auf die Auslassungspunkte (**...** ) neben **Laufzeit** zum Öffnen der **Verhalten konfigurieren** Dialogfeld.

7.  Wählen Sie **anpassen**.

8.  Wählen Sie die **InsertCustomers** -Methode in der die **anpassen** Liste.

9. Klicken Sie auf **übernehmen** zum Speichern der Konfiguration für die ausgewählte Klasse und Verhalten.

    > [!NOTE]
    > Sie können das Verhalten für jede Klasse/Verhalten-Kombination zu konfigurieren, solange Sie klicken Sie auf Weiter **übernehmen** nach jeder Änderung. Wenn Sie die Klasse oder das Verhalten ändern, bevor Sie auf **übernehmen**, ein Warnungsdialogfeld angezeigt, wird eine Möglichkeit zum Anwenden von Änderungen.

10. Wählen Sie **Update** in die **Verhalten** Liste.

11. Wählen Sie **anpassen**.

12. Wählen Sie die **UpdateCustomers** -Methode in der die **anpassen** Liste.

     Überprüfen Sie die Liste der **Methodenargumente** und **Klasseneigenschaften** , und beachten Sie, dass zwei **Methodenargumente** und zwei **Klasseneigenschaften**für einige Spalten in der Tabelle. Dies macht es einfacher, Änderungen zu verfolgen und Anweisungen zur Überprüfung von Parallelitätsverletzungen zu erstellen.

13. Zuordnung der **Original_CustomerID** Methodenargument für die **CustomerID (Original)** Klasseneigenschaft.

    > [!NOTE]
    > Standardmäßig werden Methodenargumente Klasseneigenschaften zugeordnet, wenn die Namen übereinstimmen. Wenn Eigenschaftennamen geändert werden und von der Tabelle und Entitätsklasse nicht mehr übereinstimmen, müssen Sie möglicherweise auf die entsprechende Klasseneigenschaft abzubildenden auf, wenn die **O/R Designer** kann nicht die richtige Zuordnung bestimmt. Darüber hinaus Wenn Methodenargumente nicht über gültige Klasseneigenschaften für das Zuordnen zu verfügen, legen Sie die **Klasseneigenschaften** Wert **(keine)**.

14. Klicken Sie auf **übernehmen** zum Speichern der Konfiguration für die ausgewählte Klasse und Verhalten.

15. Wählen Sie **löschen** in die **Verhalten** Liste.

16. Wählen Sie **anpassen**.

17. Wählen Sie die **DeleteCustomers** -Methode in der die **anpassen** Liste.

18. Zuordnung der **Original_CustomerID** Methodenargument für die **CustomerID (Original)** Klasseneigenschaft.

19. Klicken Sie auf **OK**.

> [!NOTE]
> Obwohl es sich nicht um ein Problem in dieser exemplarischen Vorgehensweise ist, ist anzumerken, dass LINQ to SQL-Datenbank generierte Werte für die Identität (automatisch inkrementierten), ROWGUID-(datenbankgenerierte GUID) und Timestamp-Spalten automatisch während des Einfügens verarbeitet und aktualisiert. Datenbankgenerierte Werte in anderen Spaltentypen führen unerwartet zu einem NULL-Wert. Sie sollten manuell festlegen, um die datenbankgenerierten Werte zurückzugeben, <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A> zu `true` und <xref:System.Data.Linq.Mapping.ColumnAttribute.AutoSync%2A> auf einen der folgenden: [AutoSync.Always](<xref:System.Data.Linq.Mapping.AutoSync.Always>), [AutoSync.OnInsert](<xref:System.Data.Linq.Mapping.AutoSync.OnInsert>), oder [AutoSync.OnUpdate](<xref:System.Data.Linq.Mapping.AutoSync.OnUpdate>).

## <a name="test-the-application"></a>Testen der Anwendung

Führen Sie die Anwendung erneut aus, um zu überprüfen, ob die **UpdateCustomers** gespeicherten Prozedur wird ordnungsgemäß aktualisiert den Kundendatensatz in der Datenbank.

1.  Drücken Sie **F5**.

2.  Ändern Sie einen Datensatz im Raster, um das Updateverhalten zu testen.

3.  Fügen Sie einen neuen Eintrag aus, um das Einfügeverhalten zu testen.

4.  Klicken Sie auf die Speichern-Schaltfläche, um die Änderungen in der Datenbank zu speichern.

5.  Schließen Sie das Formular.

6.  Drücken Sie **F5** und stellen Sie sicher, dass der aktualisierte Datensatz und den neu eingefügten Datensatz beibehalten.

7.  Löschen Sie das neue zeichnen Sie erstellt haben, Schritt 3 aus, um das Löschverhalten zu testen.

8.  Klicken Sie in der Schaltfläche, um die Änderungen zu übermitteln, und entfernen den gelöschten Datensatz aus der Datenbank.

9. Schließen Sie das Formular.

10. Drücken Sie **F5** und stellen Sie sicher, dass der gelöschte Datensatz aus der Datenbank entfernt wurde.

    > [!NOTE]
    > Wenn Ihre Anwendung SQL Server Express Edition, abhängig vom Wert verwendet die **in Ausgabeverzeichnis kopieren** Eigenschaft der Datenbankdatei, die Änderungen möglicherweise nicht angezeigt werden, wenn Sie drücken **F5** in Schritt 10.

## <a name="next-steps"></a>Nächste Schritte

Je nach den Anforderungen Ihrer Anwendung sind mehrere Schritte, die Sie nach dem Erstellen von LINQ to SQL-Entitätsklassen ausführen möchten. Hier sind einige Verbesserungen, die Sie an dieser Anwendung vornehmen können:

- Implementieren der Parallelitätsprüfung während der Durchführung von Updates. Weitere Informationen finden Sie unter [optimistische Parallelität: Übersicht über die](/dotnet/framework/data/adonet/sql/linq/optimistic-concurrency-overview).

- Hinzufügen von LINQ-Abfragen, um Daten zu filtern. Weitere Informationen finden Sie unter [Einführung in LINQ-Abfragen (c#)](/dotnet/csharp/programming-guide/concepts/linq/introduction-to-linq-queries).

## <a name="see-also"></a>Siehe auch

- [LINQ to SQL-Tools in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [DataContext-Methoden](../data-tools/datacontext-methods-o-r-designer.md)
- [Gewusst wie: Zuweisen von gespeicherten Prozeduren zum Ausführen von Updates, einfügungen und löschungen](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)
- [LINQ to SQL-Abfragen](/dotnet/framework/data/adonet/sql/linq/linq-to-sql-queries)