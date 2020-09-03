---
title: 'Exemplarische Vorgehensweise: Anpassen des Einfüge-, Aktualisierungs-und Lösch Verhaltens von Entitäts Klassen | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: 03ff1146-706e-4780-91cb-56a83df63eea
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 9901d917de2babf4992519ffe6b360454542aad1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72602570"
---
# <a name="walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes"></a>Exemplarische Vorgehensweise: Anpassen des Einfüge-, Update- und Löschverhaltens in Entitätsklassen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die [LINQ to SQL-Tools in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) stellen eine visuelle Entwurfs Oberfläche zum Erstellen und Bearbeiten von [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] Klassen (Entitäts Klassen) bereit, die auf Objekten in einer Datenbank basieren. Mithilfe [LINQ to SQL](https://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655)können Sie die LINQ-Technologie verwenden, um auf SQL-Datenbanken zuzugreifen. Weitere Informationen finden Sie unter [LINQ (Language-Integrated Query, sprachintegrierte Abfrage)](https://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d).

 Standardmäßig wird die Logik für die Durchführung von Updates von der [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)]-Laufzeit bereitgestellt. Basierend auf dem Schema der Tabelle (den Spaltendefinitionen und den Primärschlüsselinformationen) werden von der Laufzeit Standardanweisungen für Einfüge-, Update- und Löschvorgänge erstellt. Wenn Sie das Standardverhalten nicht verwenden möchten, können Sie das Updateverhalten konfigurieren und für erforderliche Einfüge-, Update- und Löschvorgänge, die für das Arbeiten mit Daten in der Datenbank notwendig sind, spezielle gespeicherte Prozeduren festlegen. Diese Vorgehensweise ist auch dann sinnvoll, wenn kein Standardverhalten erzeugt wird, z. B. wenn die Entitätsklassen Ansichten zugeordnet sind. Das standardmäßige Updateverhalten kann auch dann überschrieben werden, wenn für die Datenbank der Tabellenzugriff über gespeicherte Prozeduren erforderlich ist. Weitere Informationen finden Sie unter [Anpassen von Vorgängen mithilfe von gespeicherten Prozeduren](https://msdn.microsoft.com/library/aedbecc1-c33c-4fb4-8861-fdf7e1dc6b8a).

> [!NOTE]
> Für diese exemplarische Vorgehensweise ist die Verfügbarkeit der gespeicherten Prozeduren **InsertCustomer**, **UpdateCustomer** und **DeleteCustomer** für die Datenbank „Northwind“ erforderlich.

 In dieser exemplarischen Vorgehensweise werden die zu befolgenden Schritte dargestellt, um mithilfe von gespeicherten Prozeduren das LINQ to SQL-Standardlaufzeitverhalten für das Speichern von Daten in einer Datenbank zu überschreiben.

 In dieser exemplarischen Vorgehensweise wird gezeigt, wie Sie die folgenden Aufgaben ausführen:

- Erstellen einer neuen Windows Forms-Anwendung und Hinzufügen einer [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)]-Datei.

- Erstellen einer Entitätsklasse, die der Tabelle Customers der Datenbank Northwind zugeordnet ist.

- Erstellen einer Objektdatenquelle, die auf die Customer-Klasse LINQ to SQL verweist.

- Erstellen eines Windows Form, das eine <xref:System.Windows.Forms.DataGridView> enthält, die an die Customer-Klasse gebunden ist.

- Implementieren der Speicherfunktion für das Formular.

- Erstellen von <xref:System.Data.Linq.DataContext>-Methoden durch Hinzufügen von gespeicherten Prozeduren zum [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)].

- Konfigurieren der Customer-Klasse, sodass sie gespeicherte Prozeduren für Einfüge-, Update- und Löschvorgänge verwendet.

## <a name="prerequisites"></a>Voraussetzungen
 Zum Durchführen dieser exemplarischen Vorgehensweise benötigen Sie Folgendes:

- Zugriff auf die SQL Server-Version der Beispieldatenbank Northwind.

- Die gespeicherten Prozeduren **InsertCustomer**, **UpdateCustomer**und **DeleteCustomer** für die Northwind-Datenbank.

## <a name="creating-an-application-and-adding-linq-to-sql-classes"></a>Erstellen einer Anwendung und Hinzufügen von LINQ to SQL-Klassen
 Da Sie mit [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)]-Klassen arbeiten und die Daten in einem Windows Form angezeigt werden, erstellen Sie eine neue Windows Forms-Anwendung, und fügen Sie eine LINQ to SQL-Klassendatei hinzu.

 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]

#### <a name="to-create-a-new-windows-application-project-that-contains-linq-to-sql-classes"></a>So erstellen Sie ein neues Windows-Anwendungsprojekt, das LINQ to SQL-Klassen enthält

1. Erstellen Sie im Menü **Datei** ein neues Projekt.

2. Nennen Sie das Projekt **UpdatingwithSProcsWalkthrough**.

    > [!NOTE]
    > Der [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] wird in [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]- und C#-Projekten unterstützt. Erstellen Sie das neue Projekt daher in einer der beiden Sprachen.

3. Klicken Sie auf die **Windows Forms Anwendungs** Vorlage, und klicken Sie auf **OK**. Weitere Informationen finden Sie unter [Client Anwendungen](https://msdn.microsoft.com/library/2dfb50b7-5af2-4e12-9bbb-c5ade0e39a68).

     Das Projekt UpdatingwithSProcsWalkthrough wird erstellt und zu **Projektmappen-Explorer**hinzugefügt.

4. Klicken Sie im Menü **Projekt** auf **Neues Element hinzufügen**.

5. Klicken Sie auf die Vorlage **LINQ to SQL-Klassen**, und geben Sie im Feld **Name** den Namen **Northwind.dbml** ein.

6. Klicken Sie auf **Hinzufügen**.

     Dem Projekt wird eine leere LINQ to SQL-Klassendatei (Northwind.dbml) hinzugefügt, und der [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] wird geöffnet.

## <a name="creating-the-customer-entity-class-and-object-data-source"></a>Erstellen der Entitätsklasse Customer und einer Objektdatenquelle
 Erstellen [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] Sie Klassen, die Datenbanktabellen zugeordnet sind, indem Sie Tabellen aus **Server-Explorer** / **Datenbank-Explorer** auf das ziehen [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] . Sie erhalten LINQ to SQL-Entitätsklassen, die den Tabellen in der Datenbank zugeordnet sind. Nachdem die Entitätsklassen erstellt wurden, können sie wie andere Klassen mit öffentlichen Eigenschaften als Objektdatenquellen dienen.

#### <a name="to-create-a-customer-entity-class-and-configure-a-data-source-with-it"></a>So erstellen Sie eine Customer-Entitätsklasse und konfigurieren damit eine Datenquelle

1. Suchen Sie in **Server-Explorer** / **Datenbank-Explorer**die Customer-Tabelle in der SQL Server-Version der Beispieldatenbank Northwind.

2. Ziehen Sie den Knoten **Customers** von **Server-Explorer** / **Datenbank-Explorer** auf die [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] Oberfläche.

     Eine Entitätsklasse mit dem Namen **Customer** wird erstellt. Sie verfügt über Eigenschaften, die den Spalten in der Tabelle Customers entsprechen. Die Entitätsklasse wird **Customer** (nicht **Customers**) genannt, da sie einem einzelnen Kunden aus der Tabelle „Customers“ entspricht.

    > [!NOTE]
    > Dieses Umbenennungsverhalten wird als *Pluralisierung* bezeichnet. Sie kann im [Dialog Feld Optionen](../ide/reference/options-dialog-box-visual-studio.md)aktiviert oder deaktiviert werden. Weitere Informationen finden Sie unter Gewusst [wie: Aktivieren und Deaktivieren der Pluralisierung (O/R-Designer)](../data-tools/how-to-turn-pluralization-on-and-off-o-r-designer.md).

3. Klicken Sie im Menü **Erstellen** auf **UpdatingwithSProcsWalkthrough erstellen**, um das Projekt zu erstellen.

4. Klicken Sie im Menü **Daten** auf **Datenquellen anzeigen**.

5. Klicken Sie im **Datenquellenfenster** auf **Neue Datenquelle hinzufügen**.

6. Klicken Sie auf der Seite **Datenquellentyp auswählen** auf **Objekt**, und klicken Sie dann auf **Weiter**.

7. Erweitern Sie den Knoten **UpdatingwithSProcsWalkthrough**, suchen Sie die Klasse **Customer**, und wählen Sie diese aus.

    > [!NOTE]
    > Wenn die Klasse **Customer** nicht verfügbar ist, beenden Sie den Assistenten, erstellen Sie das Projekt, und führen Sie den Assistenten erneut aus.

8. Klicken Sie auf **Fertig stellen**, um die Datenquelle zu erstellen, und fügen Sie die Entitätsklasse **Customer** zum Fenster **Datenquellen** hinzu.

## <a name="creating-a-datagridview-to-display-the-customer-data-on-a-windows-form"></a>Erstellen einer DataGridView, um die Kundendaten auf einem Windows Form anzuzeigen
 Erstellen Sie Steuerelemente, die an Entitäts Klassen gebunden sind, indem Sie [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] Datenquellen Elemente aus dem **Datenquellen** Fenster auf ein Windows Form ziehen.

#### <a name="to-add-controls-that-are-bound-to-the-entity-classes"></a>So fügen Sie Steuerelemente hinzu, die an Entitätsklassen gebunden sind

1. Öffnen Sie Form1 in der Entwurfsansicht.

2. Ziehen Sie den Knoten **Customer** aus dem Fenster **Datenquellen** auf Form1.

    > [!NOTE]
    > Klicken Sie im Menü **Daten** auf **Datenquellen anzeigen**, um das Fenster **Datenquellen** anzuzeigen.

3. Öffnen Sie im Code-Editor Form1.

4. Fügen Sie dem Formular den folgenden Code hinzu, sodass er global für das Formular gilt und außerhalb einer bestimmten Methode, jedoch innerhalb der Klasse Form1 steht:

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

## <a name="implementing-save-functionality"></a>Implementieren der Speicherfunktionalität
 Die Schaltfläche zum Speichern ist standardmäßig nicht aktiviert, und die Speicherfunktionalität ist nicht implementiert. Auch wird bei Erstellung datengebundener Steuerelemente für Objektdatenquellen nicht automatisch Code hinzugefügt, um geänderte Daten in der Datenbank zu speichern. In diesem Abschnitt wird erklärt, wie die Schaltfläche zum Speichern aktiviert und die Speicherfunktionalität für [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)]-Objekte implementiert wird.

#### <a name="to-implement-save-functionality"></a>So implementieren Sie die Speicherfunktionalität

1. Öffnen Sie Form1 in der Entwurfsansicht.

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

## <a name="overriding-the-default-behavior-for-performing-updates-inserts-updates-and-deletes"></a>Überschreiben des Standardverhaltens für Aktualisierungen (Einfüge-, Aktualisierungs- und Löschvorgänge)

#### <a name="to-override-the-default-update-behavior"></a>So überschreiben Sie das standardmäßige Updateverhalten

1. Öffnen Sie im [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] die LINQ to SQL-Datei. (Doppelklicken Sie im **Projektmappen-Explorer** auf die Datei **Northwind.dbml**.)

2. Erweitern Sie in **Server-Explorer** / **Datenbank-Explorer**den Knoten **gespeicherte Prozeduren** Northwind-Datenbanken, und suchen Sie die gespeicherten Prozeduren **InsertCustomers**, **updatecustomzer**und **DeleteCustomers** .

3. Ziehen Sie alle drei gespeicherten Prozeduren auf den [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)].

     Die gespeicherten Prozeduren werden dem Methodenbereich als <xref:System.Data.Linq.DataContext>-Methoden hinzugefügt. Weitere Informationen finden Sie unter [DataContext-Methoden (O/R-Designer)](../data-tools/datacontext-methods-o-r-designer.md).

4. Wählen Sie im die Entitäts Klasse **Customer** aus [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] .

5. Wählen Sie im Fenster **Eigenschaften** die Eigenschaft **Einfügen** aus.

6. Klicken Sie auf die Auslassungszeichen (...) neben **Laufzeit verwenden**, um das Dialogfeld **Verhalten konfigurieren** zu öffnen.

7. Klicken Sie auf **Anpassen**.

8. Wählen Sie aus der Liste **Anpassen** die **InsertCustomers**-Methode aus.

9. Klicken Sie auf **Anwenden**, um die Konfiguration für die ausgewählte Klasse und das ausgewählte Verhalten zu speichern.

    > [!NOTE]
    > Sie können mit der Konfiguration des Verhaltens jeder Klasse/Verhalten-Kombination fortfahren, solange Sie nach jeder Änderung auf **Anwenden** klicken. Wenn Sie die Klasse oder das Verhalten ändern, bevor **Sie auf Übernehmen klicken,** wird ein Warn Dialogfeld angezeigt, in dem eine Gelegenheit zum Anwenden von Änderungen angezeigt wird.

10. Wählen Sie aus der Liste **Verhalten** die Option **Aktualisieren** aus.

11. Klicken Sie auf **Anpassen**.

12. Wählen Sie in der Liste **Anpassen** die **UpdateCustomers**-Methode aus.

     Überprüfen Sie die Liste der **Methodenargumente** und **Klasseneigenschaften**, und beachten Sie, dass für einige Spalten in der Tabelle zwei **Methodenargumente** sowie zwei **Klasseneigenschaften** vorhanden sind. Dies macht es einfacher, Änderungen zu verfolgen und Anweisungen zur Überprüfung von Parallelitätsverletzungen zu erstellen.

13. Ordnen Sie das **Original_CustomerID**-Methodenargument der Klasseneigenschaft **CustomerID (Original)** zu.

    > [!NOTE]
    > Standardmäßig werden Methodenargumente Klasseneigenschaften zugeordnet, wenn die Namen übereinstimmen. Wenn Eigenschaftennamen geändert werden und die Namen von Tabelle und Entitätsklasse nicht mehr übereinstimmen, kann es erforderlich sein, die entsprechende zuzuordnende Klasseneigenschaft auszuwählen, wenn die korrekte Zuordnung vom O/R-Designer nicht festgestellt werden kann. Wenn die Methodenargumente nicht über gültige Klasseneigenschaften für die Zuordnung verfügen, können Sie zusätzlich den Wert **Klasseneigenschaften** auf **(Keine)** festlegen.

14. Klicken Sie auf **Anwenden**, um die Konfiguration für die ausgewählte Klasse und das ausgewählte Verhalten zu speichern.

15. Wählen Sie aus der Liste **Verhalten** die Option **Löschen** aus.

16. Klicken Sie auf **Anpassen**.

17. Wählen Sie in der Liste **Anpassen** die **DeleteCustomers**-Methode aus.

18. Ordnen Sie das **Original_CustomerID**-Methodenargument der Klasseneigenschaft **CustomerID (Original)** zu.

19. Klicken Sie auf **OK**.

> [!NOTE]
> Auch wenn es kein Problem in dieser exemplarischen Vorgehensweise darstellt, ist Folgendes zu beachten: [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] behandelt bei Einfüge- und Updatevorgängen die datenbankgenerierten Werte bei Identitätsspalten (automatische Inkrementierung) sowie bei ROWGUID- (datenbankgenerierte GUID) und Timestamp-Spalten automatisch. Datenbankgenerierte Werte in anderen Spaltentypen führen unerwartet zu einem NULL-Wert. Um die datenbankgenerierten Werte zurückzugeben, sollte manuell <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A> auf `true` und <xref:System.Data.Linq.Mapping.ColumnAttribute.AutoSync%2A> auf eine der folgenden Einstellungen festgelegt werden: <xref:System.Data.Linq.Mapping.AutoSync>, <xref:System.Data.Linq.Mapping.AutoSync> oder <xref:System.Data.Linq.Mapping.AutoSync>.

## <a name="testing-the-application"></a>Testen der Anwendung
 Führen Sie die Anwendung erneut aus, um zu überprüfen, ob der Kundendatensatz in der Datenbank von der gespeicherten Prozedur **UpdateCustomers** ordnungsgemäß aktualisiert wird.

#### <a name="to-test-the-application"></a>So testen Sie die Anwendung

1. Drücken Sie F5.

2. Ändern Sie einen Datensatz im Raster, um das Updateverhalten zu testen.

3. Fügen Sie einen neuen Datensatz hinzu, um das Einfügeverhalten zu testen.

4. Klicken Sie auf die Speichern-Schaltfläche, um die Änderungen in der Datenbank zu speichern.

5. Schließen Sie das Formular.

6. Drücken Sie F5, und überprüfen Sie, ob der aktualisierte Datensatz und der neu eingefügte Datensatz erhalten bleiben.

7. Löschen Sie den in Schritt 3 erstellten neuen Datensatz, um das Löschverhalten zu testen.

8. Klicken Sie auf die Speichern-Schaltfläche, um die Änderungen zu übermitteln und den gelöschten Datensatz aus der Datenbank zu entfernen.

9. Schließen Sie das Formular.

10. Drücken Sie F5 und überprüfen Sie, ob der gelöschte Datensatz aus der Datenbank entfernt wurde.

    > [!NOTE]
    > Wenn Ihre Anwendung SQL Server Express Edition verwendet, werden beim Drücken von F5 in Schritt 10 die Änderungen möglicherweise nicht angezeigt. Dies ist abhängig vom Wert der Eigenschaft **Ins Ausgabeverzeichnis kopieren** der Datenbankdatei.

## <a name="next-steps"></a>Nächste Schritte
 Je nach den Anforderungen Ihrer Anwendung sollten Sie nach dem Erstellen von [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)]-Entitätsklassen mehrere Schritte ausführen. Hier sind einige Verbesserungen, die Sie an dieser Anwendung vornehmen können:

- Implementieren der Parallelitätsprüfung während der Durchführung von Updates. Weitere Informationen finden Sie unter vollständige Parallelität [: Übersicht](https://msdn.microsoft.com/library/c2e38512-d0c8-4807-b30a-cb7e30338694).

- Hinzufügen von LINQ-Abfragen, um Daten zu filtern. Weitere Informationen finden [Sie unter Einführung in LINQ-Abfragen (c#)](https://msdn.microsoft.com/library/37895c02-268c-41d5-be39-f7d936fa88a8).

## <a name="see-also"></a>Weitere Informationen
 [LINQ to SQL Tools in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) [LINQ to SQL](https://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655) [LINQ to SQL Abfragen](https://msdn.microsoft.com/library/f4897aaa-7f44-4c20-a471-b948c2971aae) [DataContext-Methoden (o/r-Designer)](../data-tools/datacontext-methods-o-r-designer.md) Gewusst [wie: Zuweisen von gespeicherten Prozeduren zum Durchführen von Aktualisierungen, Einfügungen und Löschungen (o/r-Designer)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md) [Pave What es New for Data Application Development in Visual Studio 2012](https://msdn.microsoft.com/3d50d68f-5f44-4915-842f-6d42fce793f1)
