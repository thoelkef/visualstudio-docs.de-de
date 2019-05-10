---
title: 'Exemplarische Vorgehensweise: Anpassen des Einfüge-, Update- und Löschverhaltens in Entitätsklassen'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
ms.assetid: 03ff1146-706e-4780-91cb-56a83df63eea
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: e869ae13c9d7ec82cb4d70fb5f3c5fce355691d5
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62565406"
---
# <a name="walkthrough-customize-the-insert-update-and-delete-behavior-of-entity-classes"></a>Exemplarische Vorgehensweise: Anpassen des Einfüge-, Update- und Löschverhaltens in Entitätsklassen

Die [LINQ to SQL-tools in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) bietet eine visuelle Entwurfsoberfläche zum Erstellen und Bearbeiten von LINQ to SQL-Klassen (Entitätsklassen), die auf Objekte in einer Datenbank basieren. Mithilfe von [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index), können Sie LINQ-Technologie für den Zugriff auf SQL-Datenbanken. Weitere Informationen finden Sie unter [LINQ (Language-Integrated Query, sprachintegrierte Abfrage)](/dotnet/csharp/linq/).

Standardmäßig wird die Logik zum Durchführen von Aktualisierungen von LINQ to SQL-Laufzeit bereitgestellt. Der Laufzeit erstellt `Insert`, `Update`, und `Delete` Anweisungen basierend auf dem Schema der Tabelle (den Spaltendefinitionen und Primärschlüsselinformationen). Wenn Sie das Standardverhalten nicht verwenden möchten, können Sie das Updateverhalten konfigurieren und für erforderliche Einfüge-, Update- und Löschvorgänge, die für das Arbeiten mit Daten in der Datenbank notwendig sind, spezielle gespeicherte Prozeduren festlegen. Diese Vorgehensweise ist auch dann sinnvoll, wenn kein Standardverhalten erzeugt wird, z. B. wenn die Entitätsklassen Ansichten zugeordnet sind. Das standardmäßige Updateverhalten kann auch dann überschrieben werden, wenn für die Datenbank der Tabellenzugriff über gespeicherte Prozeduren erforderlich ist. Weitere Informationen finden Sie unter [Anpassen von Operationen durch Verwendung von gespeicherten Prozeduren](/dotnet/framework/data/adonet/sql/linq/customizing-operations-by-using-stored-procedures).

> [!NOTE]
> Für diese exemplarische Vorgehensweise ist die Verfügbarkeit der gespeicherten Prozeduren **InsertCustomer**, **UpdateCustomer** und **DeleteCustomer** für die Datenbank „Northwind“ erforderlich.

In dieser exemplarischen Vorgehensweise werden die zu befolgenden Schritte dargestellt, um mithilfe von gespeicherten Prozeduren das LINQ to SQL-Standardlaufzeitverhalten für das Speichern von Daten in einer Datenbank zu überschreiben.

Im Verlauf dieser exemplarischen Vorgehensweise erfahren Sie, wie Sie die folgenden Aufgaben ausführen:

- Erstellen einer neuen Windows Forms-Anwendung und Hinzufügen einer LINQ to SQL-Datei darauf.

- Erstellen einer Entitätsklasse, die den Northwind zugeordnet ist `Customers` Tabelle.

- Erstellen eine Objektdatenquelle, die auf LINQ to SQL verweist `Customer` Klasse.

- Erstellen Sie ein Windows-Formular, enthält eine <xref:System.Windows.Forms.DataGridView> , gebunden ist, um die `Customer` Klasse.

- Implementieren der Speicherfunktion für das Formular.

- Erstellen Sie <xref:System.Data.Linq.DataContext> -Methoden durch Hinzufügen von gespeicherten Systemprozeduren, die **O/R Designer**.

- Konfigurieren der `Customer` Klasse zum Verwenden gespeicherter Prozeduren zum Ausführen von einfügungen, Updates und löscht.

## <a name="prerequisites"></a>Vorraussetzungen

In dieser exemplarischen Vorgehensweise verwendet SQL Server Express LocalDB und der Beispieldatenbank Northwind.

1. Wenn Sie SQL Server Express LocalDB nicht haben, installieren Sie es entweder über die [Downloadseite für SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express), oder über die **Visual Studio-Installer**. In der **Visual Studio-Installer**, können Sie SQL Server Express LocalDB installieren, als Teil der **datenspeicherung und-Verarbeitung** Workload oder als eine einzelne Komponente.

2. Installieren der Northwind-Beispieldatenbank mit folgenden Schritten:

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

     Das Projekt **UpdatingwithSProcsWalkthrough** wird erstellt und zum **Projektmappen-Explorer** hinzugefügt.

4. Klicken Sie im Menü **Projekt** auf **Neues Element hinzufügen**.

5. Klicken Sie auf die Vorlage **LINQ to SQL-Klassen**, und geben Sie im Feld **Name** den Namen **Northwind.dbml** ein.

6. Klicken Sie auf **Hinzufügen**.

     Eine leere LINQ to SQL-Klassendatei (**Northwind.dbml**) wird dem Projekt hinzugefügt und die **O/R Designer** wird geöffnet.

## <a name="create-the-customer-entity-class-and-object-data-source"></a>Erstellen Sie die Customer-Entität-Klasse und Objekt-Datenquelle

Erstellen von LINQ to SQL-Klassen, Datenbanktabellen zugeordnet sind, ziehen Sie Tabellen aus **Server-Explorer** oder **Datenbank-Explorer** auf die **O/R Designer**. Sie erhalten LINQ to SQL-Entitätsklassen, die den Tabellen in der Datenbank zugeordnet sind. Nachdem die Entitätsklassen erstellt wurden, können sie wie andere Klassen mit öffentlichen Eigenschaften als Objektdatenquellen dienen.

### <a name="to-create-a-customer-entity-class-and-configure-a-data-source-with-it"></a>So erstellen Sie eine Customer-Entitätsklasse und konfigurieren damit eine Datenquelle

1. In **Server-Explorer** oder **Datenbank-Explorer**, suchen Sie die **Kunden** -Tabelle in SQL Server-Version der Northwind-Beispieldatenbank.

2. Ziehen Sie die **Kunden** aus **Server-Explorer** oder **Datenbank-Explorer** auf der **O/R Designer* Oberfläche.

     Eine Entitätsklasse mit dem Namen **Customer** wird erstellt. Sie verfügt über Eigenschaften, die den Spalten in der Tabelle Customers entsprechen. Die Entitätsklasse wird **Customer** (nicht **Customers**) genannt, da sie einem einzelnen Kunden aus der Tabelle „Customers“ entspricht.

    > [!NOTE]
    > Dieses Umbenennungsverhalten wird als *Pluralisierung* bezeichnet. Sie können aktiviert oder deaktiviert die [Abonnementoptionen](../ide/reference/options-dialog-box-visual-studio.md). Weitere Informationen finden Sie unter [Vorgehensweise: Aktivieren/Deaktivieren der Pluralisierung (O/R-Designer)](../data-tools/how-to-turn-pluralization-on-and-off-o-r-designer.md).

3. Klicken Sie im Menü **Erstellen** auf **UpdatingwithSProcsWalkthrough erstellen**, um das Projekt zu erstellen.

4. Zum Öffnen der **Datenquellen** Fenster auf die **Daten** Menü klicken Sie auf **Datenquellen anzeigen**.

5. Klicken Sie im **Datenquellenfenster** auf **Neue Datenquelle hinzufügen**.

6. Klicken Sie auf der Seite **Datenquellentyp auswählen** auf **Objekt**, und klicken Sie dann auf **Weiter**.

7. Erweitern Sie den Knoten **UpdatingwithSProcsWalkthrough**, suchen Sie die Klasse **Customer**, und wählen Sie diese aus.

    > [!NOTE]
    > Wenn die Klasse **Customer** nicht verfügbar ist, beenden Sie den Assistenten, erstellen Sie das Projekt, und führen Sie den Assistenten erneut aus.
8. Klicken Sie auf **Fertig stellen**, um die Datenquelle zu erstellen, und fügen Sie die Entitätsklasse **Customer** zum Fenster **Datenquellen** hinzu.

## <a name="create-a-datagridview-to-display-the-customer-data-on-a-windows-form"></a>Erstellen einer DataGridView, um die Kundendaten in einem Windows Form anzuzeigen

Erstellen Sie Steuerelemente, die an Entitätsklassen gebunden sind, durch Ziehen von LINQ zu SQL-Datenquellenelemente aus der **Datenquellen** in ein Windows-Formular.

### <a name="to-add-controls-that-are-bound-to-the-entity-classes"></a>So fügen Sie Steuerelemente hinzu, die an Entitätsklassen gebunden sind

1. Öffnen Sie **Form1** in der Designansicht.

2. Ziehen Sie den Knoten **Customer** aus dem Fenster **Datenquellen** auf **Form1**.

    > [!NOTE]
    > Klicken Sie im Menü **Daten** auf **Datenquellen anzeigen**, um das Fenster **Datenquellen** anzuzeigen.

3. Öffnen Sie **Form1** im Code-Editor.

4. Fügen Sie den folgenden Code in das Formular, die global für das Formular, außerhalb einer bestimmten Methode, jedoch innerhalb der `Form1` Klasse:

    ```vb
    Private NorthwindDataContext1 As New NorthwindDataContext
    ```

    ```csharp
    private NorthwindDataContext northwindDataContext1
        = new NorthwindDataContext();
    ```

5. Erstellen Sie einen Ereignishandler für das `Form_Load`-Ereignis, und fügen Sie dem Handler den folgenden Code hinzu:

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

1. Öffnen Sie **Form1** in der Designansicht.

2. Wählen Sie im **CustomersBindingNavigator** die Schaltfläche zum Speichern (die Schaltfläche mit dem Diskettensymbol) aus.

3. Legen Sie im Fenster **Eigenschaften** die Eigenschaft **Aktiviert** auf **True** fest.

4. Doppelklicken Sie auf die Schaltfläche zum Speichern, um einen Ereignishandler zu erstellen und zum Code-Editor zu wechseln.

5. Fügen Sie dem Ereignishandler für die Schaltfläche zum Speichern den folgenden Code hinzu:

    ```vb
    NorthwindDataContext1.SubmitChanges()
    ```

    ```csharp
    northwindDataContext1.SubmitChanges();
    ```

## <a name="override-the-default-behavior-for-performing-updates-inserts-updates-and-deletes"></a>Überschreiben Sie das Standardverhalten für Aktualisierungen (einfügungen, Updates und löschungen)

### <a name="to-override-the-default-update-behavior"></a>So überschreiben Sie das standardmäßige Updateverhalten

1. Öffnen Sie die LINQ to SQL-Datei in die **O/R Designer**. (Doppelklicken Sie im **Projektmappen-Explorer** auf die Datei **Northwind.dbml**.)

2. Erweitern Sie im **Server-Explorer** oder **Datenbank-Explorer** den Knoten **Gespeicherte Prozeduren** der Datenbank „Northwind“, und suchen Sie die gespeicherten Prozeduren **InsertCustomers**, **UpdateCustomers** und **DeleteCustomers**.

3. Ziehen Sie alle drei gespeicherte Prozeduren auf die **O/R Designer**.

     Die gespeicherten Prozeduren werden dem Methodenbereich als <xref:System.Data.Linq.DataContext>-Methoden hinzugefügt. Weitere Informationen finden Sie unter [DataContext-Methoden (O/R Designer)](../data-tools/datacontext-methods-o-r-designer.md).

4. Wählen Sie die **Kunden** Entitätsklasse in der **O/R Designer**.

5. Wählen Sie im Fenster **Eigenschaften** die Eigenschaft **Einfügen** aus.

6. Klicken Sie auf die Auslassungszeichen (**...**) neben **Laufzeit verwenden**, um das Dialogfeld **Verhalten konfigurieren** zu öffnen.

7. Wählen Sie **Anpassen** aus.

8. Wählen Sie aus der Liste **Anpassen** die **InsertCustomers**-Methode aus.

9. Klicken Sie auf **Anwenden**, um die Konfiguration für die ausgewählte Klasse und das ausgewählte Verhalten zu speichern.

    > [!NOTE]
    > Sie können mit der Konfiguration des Verhaltens jeder Klasse/Verhalten-Kombination fortfahren, solange Sie nach jeder Änderung auf **Anwenden** klicken. Wenn Sie die Klasse oder das Verhalten ändern, bevor Sie auf **übernehmen**, ein Warnungsdialogfeld angezeigt, wird eine Möglichkeit zum Anwenden von Änderungen.

10. Wählen Sie aus der Liste **Verhalten** die Option **Aktualisieren** aus.

11. Wählen Sie **Anpassen** aus.

12. Wählen Sie in der Liste **Anpassen** die **UpdateCustomers**-Methode aus.

     Überprüfen Sie die Liste der **Methodenargumente** und **Klasseneigenschaften**, und beachten Sie, dass für einige Spalten in der Tabelle zwei **Methodenargumente** sowie zwei **Klasseneigenschaften** vorhanden sind. Dies macht es einfacher, Änderungen zu verfolgen und Anweisungen zur Überprüfung von Parallelitätsverletzungen zu erstellen.

13. Ordnen Sie das **Original_CustomerID**-Methodenargument der Klasseneigenschaft **CustomerID (Original)** zu.

    > [!NOTE]
    > Standardmäßig werden Methodenargumente Klasseneigenschaften zugeordnet, wenn die Namen übereinstimmen. Wenn Eigenschaftennamen geändert werden und die Namen von Tabelle und Entitätsklasse nicht mehr übereinstimmen, kann es erforderlich sein, die entsprechende zuzuordnende Klasseneigenschaft auszuwählen, wenn die korrekte Zuordnung vom **O/R-Designer** nicht festgestellt werden kann. Wenn die Methodenargumente nicht über gültige Klasseneigenschaften für die Zuordnung verfügen, können Sie zusätzlich den Wert **Klasseneigenschaften** auf **(Keine)** festlegen.

14. Klicken Sie auf **Anwenden**, um die Konfiguration für die ausgewählte Klasse und das ausgewählte Verhalten zu speichern.

15. Wählen Sie aus der Liste **Verhalten** die Option **Löschen** aus.

16. Wählen Sie **Anpassen** aus.

17. Wählen Sie in der Liste **Anpassen** die **DeleteCustomers**-Methode aus.

18. Ordnen Sie das **Original_CustomerID**-Methodenargument der Klasseneigenschaft **CustomerID (Original)** zu.

19. Klicken Sie auf **OK**.

> [!NOTE]
> Obwohl es sich nicht um ein Problem in dieser exemplarischen Vorgehensweise ist, ist anzumerken, dass LINQ to SQL-Datenbank generierte Werte für die Identität (automatisch inkrementierten), ROWGUID-(datenbankgenerierte GUID) und Timestamp-Spalten automatisch während des Einfügens verarbeitet und aktualisiert. Datenbankgenerierte Werte in anderen Spaltentypen führen unerwartet zu einem NULL-Wert. Sie sollten manuell festlegen, um die datenbankgenerierten Werte zurückzugeben, <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A> zu `true` und <xref:System.Data.Linq.Mapping.ColumnAttribute.AutoSync%2A> auf einen der folgenden: [AutoSync.Always](<xref:System.Data.Linq.Mapping.AutoSync.Always>), [AutoSync.OnInsert](<xref:System.Data.Linq.Mapping.AutoSync.OnInsert>), oder [AutoSync.OnUpdate](<xref:System.Data.Linq.Mapping.AutoSync.OnUpdate>).

## <a name="test-the-application"></a>Testen der Anwendung

Führen Sie die Anwendung erneut aus, um zu überprüfen, ob der Kundendatensatz in der Datenbank von der gespeicherten Prozedur **UpdateCustomers** ordnungsgemäß aktualisiert wird.

1. Drücken Sie **F5**.

2. Ändern Sie einen Datensatz im Raster, um das Updateverhalten zu testen.

3. Fügen Sie einen neuen Datensatz hinzu, um das Einfügeverhalten zu testen.

4. Klicken Sie auf die Speichern-Schaltfläche, um die Änderungen in der Datenbank zu speichern.

5. Schließen Sie das Formular.

6. Drücken Sie **F5**, und überprüfen Sie, ob der aktualisierte Datensatz und der neu eingefügte Datensatz erhalten bleiben.

7. Löschen Sie den in Schritt 3 erstellten neuen Datensatz, um das Löschverhalten zu testen.

8. Klicken Sie auf die Schaltfläche „Speichern“, um die Änderungen zu übermitteln und den gelöschten Datensatz aus der Datenbank zu entfernen.

9. Schließen Sie das Formular.

10. Drücken Sie **F5** und überprüfen Sie, ob der gelöschte Datensatz aus der Datenbank entfernt wurde.

    > [!NOTE]
    > Wenn Ihre Anwendung SQL Server Express Edition verwendet, werden beim Drücken von **F5** in Schritt 10 die Änderungen möglicherweise nicht angezeigt. Dies ist abhängig vom Wert der Eigenschaft **Ins Ausgabeverzeichnis kopieren** der Datenbankdatei.

## <a name="next-steps"></a>Nächste Schritte

Je nach den Anforderungen Ihrer Anwendung sind mehrere Schritte, die Sie nach dem Erstellen von LINQ to SQL-Entitätsklassen ausführen möchten. Hier sind einige Verbesserungen, die Sie an dieser Anwendung vornehmen können:

- Implementieren der Parallelitätsprüfung während der Durchführung von Updates. Weitere Informationen finden Sie unter [optimistische Parallelität: Übersicht über die](/dotnet/framework/data/adonet/sql/linq/optimistic-concurrency-overview).

- Hinzufügen von LINQ-Abfragen, um Daten zu filtern. Weitere Informationen finden Sie unter [Einführung in LINQ-Abfragen (c#)](/dotnet/csharp/programming-guide/concepts/linq/introduction-to-linq-queries).

## <a name="see-also"></a>Siehe auch

- [LINQ to SQL-Tools in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [DataContext-Methoden](../data-tools/datacontext-methods-o-r-designer.md)
- [Vorgehensweise: Zuweisen von gespeicherten Prozeduren zum Durchführen von Aktionen zum Aktualisieren, Einfügen und Löschen](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)
- [LINQ to SQL-Abfragen](/dotnet/framework/data/adonet/sql/linq/linq-to-sql-queries)