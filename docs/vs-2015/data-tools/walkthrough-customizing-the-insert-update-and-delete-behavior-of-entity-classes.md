---
title: 'Exemplarische Vorgehensweise: Anpassen des Einfüge-, Update- und delete-Verhalten von Entitätsklassen | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 03ff1146-706e-4780-91cb-56a83df63eea
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 4d8ef69258d9c672bb5deb01b9c2e0972d4e8303
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49193543"
---
# <a name="walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes"></a>Exemplarische Vorgehensweise: Anpassen des Einfüge-, Update- und delete-Verhalten von Entitätsklassen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Die [LINQ to SQL-Tools in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) bietet eine visuelle Entwurfsoberfläche zum Erstellen und bearbeiten [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] -Klassen (Entitätsklassen), die auf Objekte in einer Datenbank basieren. Mithilfe von [LINQ to SQL](http://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655), können Sie LINQ-Technologie für den Zugriff auf SQL-Datenbanken. Weitere Informationen finden Sie unter [LINQ (Language-Integrated Query, sprachintegrierte Abfrage)](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d).  
  
 Standardmäßig wird die Logik für die Durchführung von Updates von der [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)]-Laufzeit bereitgestellt. Basierend auf dem Schema der Tabelle (den Spaltendefinitionen und den Primärschlüsselinformationen) werden von der Laufzeit Standardanweisungen für Einfüge-, Update- und Löschvorgänge erstellt. Wenn Sie das Standardverhalten nicht verwenden möchten, können Sie das Updateverhalten konfigurieren und für erforderliche Einfüge-, Update- und Löschvorgänge, die für das Arbeiten mit Daten in der Datenbank notwendig sind, spezielle gespeicherte Prozeduren festlegen. Diese Vorgehensweise ist auch dann sinnvoll, wenn kein Standardverhalten erzeugt wird, z. B. wenn die Entitätsklassen Ansichten zugeordnet sind. Das standardmäßige Updateverhalten kann auch dann überschrieben werden, wenn für die Datenbank der Tabellenzugriff über gespeicherte Prozeduren erforderlich ist. Weitere Informationen finden Sie unter [anpassen Operations By Using Stored Procedures](http://msdn.microsoft.com/library/aedbecc1-c33c-4fb4-8861-fdf7e1dc6b8a).  
  
> [!NOTE]
>  Diese exemplarische Vorgehensweise setzt voraus, dass die **"InsertCustomer"**, **"UpdateCustomer"**, und **DeleteCustomer** gespeicherte Prozeduren für die Datenbank Northwind. Ausführliche Informationen zum Erstellen dieser gespeicherten Prozeduren finden Sie unter [Exemplarische Vorgehensweise: Erstellen von Update gespeicherte Prozeduren für die Northwind-Kundentabelle](../data-tools/walkthrough-creating-update-stored-procedures-for-the-northwind-customers-table.md).  
  
 In dieser exemplarischen Vorgehensweise werden die zu befolgenden Schritte dargestellt, um mithilfe von gespeicherten Prozeduren das LINQ to SQL-Standardlaufzeitverhalten für das Speichern von Daten in einer Datenbank zu überschreiben.  
  
 In dieser exemplarischen Vorgehensweise wird gezeigt, wie Sie die folgenden Aufgaben ausführen:  
  
-   Erstellen einer neuen Windows Forms-Anwendung und Hinzufügen einer [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)]-Datei.  
  
-   Erstellen einer Entitätsklasse, die der Tabelle Customers der Datenbank Northwind zugeordnet ist.  
  
-   Erstellen einer Objektdatenquelle, die auf die Customer-Klasse LINQ to SQL verweist.  
  
-   Erstellen eines Windows Form, das eine <xref:System.Windows.Forms.DataGridView> enthält, die an die Customer-Klasse gebunden ist.  
  
-   Implementieren der Speicherfunktion für das Formular.  
  
-   Erstellen von <xref:System.Data.Linq.DataContext>-Methoden durch Hinzufügen von gespeicherten Prozeduren zum [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)].  
  
-   Konfigurieren der Customer-Klasse, sodass sie gespeicherte Prozeduren für Einfüge-, Update- und Löschvorgänge verwendet.  
  
## <a name="prerequisites"></a>Vorraussetzungen  
 Zum Durchführen dieser exemplarischen Vorgehensweise benötigen Sie Folgendes:  
  
-   Zugriff auf die SQL Server-Version der Beispieldatenbank Northwind. Weitere Informationen finden Sie unter [Vorgehensweise: Installieren von Beispieldatenbanken](../data-tools/how-to-install-sample-databases.md).  
  
-   Die **"InsertCustomer"**, **"UpdateCustomer"**, und **DeleteCustomer** gespeicherte Prozeduren für die Datenbank Northwind. Weitere Informationen finden Sie unter [Exemplarische Vorgehensweise: Erstellen von Update gespeicherte Prozeduren für die Northwind-Kundentabelle](../data-tools/walkthrough-creating-update-stored-procedures-for-the-northwind-customers-table.md).  
  
## <a name="creating-an-application-and-adding-linq-to-sql-classes"></a>Erstellen einer Anwendung und Hinzufügen von LINQ to SQL-Klassen  
 Da Sie mit [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)]-Klassen arbeiten und die Daten in einem Windows Form angezeigt werden, erstellen Sie eine neue Windows Forms-Anwendung, und fügen Sie eine LINQ to SQL-Klassendatei hinzu.  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
#### <a name="to-create-a-new-windows-application-project-that-contains-linq-to-sql-classes"></a>So erstellen Sie ein neues Windows-Anwendungsprojekt, das LINQ to SQL-Klassen enthält  
  
1.  Von der **Datei** Menü ein neues Projekt erstellen.  
  
2.  Nennen Sie das Projekt **UpdatingwithSProcsWalkthrough**.  
  
    > [!NOTE]
    >  Der [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] wird in [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]- und C#-Projekten unterstützt. Erstellen Sie das neue Projekt daher in einer der beiden Sprachen.  
  
3.  Klicken Sie auf die **Windows Forms-Anwendung** Vorlage, und klicken Sie auf **OK**. Weitere Informationen finden Sie unter [Clientanwendungen](http://msdn.microsoft.com/library/2dfb50b7-5af2-4e12-9bbb-c5ade0e39a68).  
  
     Das Projekt UpdatingwithSProcsWalkthrough wird erstellt und hinzugefügt **Projektmappen-Explorer**.  
  
4.  Klicken Sie im Menü **Projekt** auf **Neues Element hinzufügen**.  
  
5.  Klicken Sie auf die **LINQ to SQL-Klassen** Vorlage, und geben **Northwind.dbml** in die **Namen** Feld.  
  
6.  Klicken Sie auf **Hinzufügen**.  
  
     Dem Projekt wird eine leere LINQ to SQL-Klassendatei (Northwind.dbml) hinzugefügt, und der [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] wird geöffnet.  
  
## <a name="creating-the-customer-entity-class-and-object-data-source"></a>Erstellen der Entitätsklasse Customer und einer Objektdatenquelle  
 Erstellen Sie [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] Klassen, Datenbanktabellen zugeordnet sind, ziehen Sie Tabellen aus **Server-Explorer**/**Datenbank-Explorer** auf die [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]. Sie erhalten LINQ to SQL-Entitätsklassen, die den Tabellen in der Datenbank zugeordnet sind. Nachdem die Entitätsklassen erstellt wurden, können sie wie andere Klassen mit öffentlichen Eigenschaften als Objektdatenquellen dienen.  
  
#### <a name="to-create-a-customer-entity-class-and-configure-a-data-source-with-it"></a>So erstellen Sie eine Customer-Entitätsklasse und konfigurieren damit eine Datenquelle  
  
1.  In **Server-Explorer**/**Datenbank-Explorer**, suchen Sie die Customer-Tabelle in SQL Server-Version der Northwind-Beispieldatenbank. Weitere Informationen finden Sie unter [Vorgehensweise: Verbinden mit der Datenbank Northwind](../data-tools/how-to-connect-to-the-northwind-database.md).  
  
2.  Ziehen Sie die **Kunden** aus **Server-Explorer**/**Datenbank-Explorer** auf die [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] Oberfläche.  
  
     Die Entitätsklasse **Kunden** erstellt wird. Sie verfügt über Eigenschaften, die den Spalten in der Tabelle Customers entsprechen. Die Entitätsklasse wird mit dem Namen **Kunden** (nicht **Kunden**) da es einen einzelnen Kunden aus der Customers-Tabelle darstellt.  
  
    > [!NOTE]
    >  Dieses Umbenennungsverhalten wird aufgerufen, *Pluralisierung*. Sie können aktiviert oder deaktiviert die [Abonnementoptionen](../ide/reference/options-dialog-box-visual-studio.md). Weitere Informationen finden Sie unter [Vorgehensweise: Aktivieren/Deaktivieren der Pluralisierung (O/R Designer)](../data-tools/how-to-turn-pluralization-on-and-off-o-r-designer.md).  
  
3.  Auf der **erstellen** Menü klicken Sie auf **UpdatingwithSProcsWalkthrough erstellen** zum Erstellen des Projekts.  
  
4.  Klicken Sie im Menü **Daten** auf **Datenquellen anzeigen**.  
  
5.  Klicken Sie im **Datenquellenfenster** auf **Neue Datenquelle hinzufügen**.  
  
6.  Klicken Sie auf **Objekt** auf die **wählen Sie einen Datenquellentyp** Seite, und klicken Sie dann auf **Weiter**.  
  
7.  Erweitern Sie die **UpdatingwithSProcsWalkthrough** Knoten, und wählen Sie die **Kunden** Klasse.  
  
    > [!NOTE]
    >  Wenn die **Kunden** Klasse ist nicht verfügbar, den Assistenten abbrechen, erstellen Sie das Projekt und führen Sie den Assistenten erneut aus.  
  
8.  Klicken Sie auf **Fertig stellen** zum Erstellen der Datenquelle und Hinzufügen der **Kunden** Entitätsklasse, um die **Datenquellen** Fenster.  
  
## <a name="creating-a-datagridview-to-display-the-customer-data-on-a-windows-form"></a>Erstellen einer DataGridView, um die Kundendaten auf einem Windows Form anzuzeigen  
 Erstellen Sie Steuerelemente, die an Entitätsklassen, durch Ziehen gebunden sind [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] -Datenquellenelemente vom die **Datenquellen** in ein Windows-Formular.  
  
#### <a name="to-add-controls-that-are-bound-to-the-entity-classes"></a>So fügen Sie Steuerelemente hinzu, die an Entitätsklassen gebunden sind  
  
1.  Öffnen Sie Form1 in der Entwurfsansicht.  
  
2.  Von der **Datenquellen** ziehen Sie die **Kunden** Knoten auf Form1.  
  
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
 Die Schaltfläche zum Speichern ist standardmäßig nicht aktiviert, und die Speicherfunktionalität ist nicht implementiert. Auch wird bei Erstellung datengebundener Steuerelemente für Objektdatenquellen nicht automatisch Code hinzugefügt, um geänderte Daten in der Datenbank zu speichern. In diesem Abschnitt wird erklärt, wie die Schaltfläche zum Speichern aktiviert und die Speicherfunktionalität für [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)]-Objekte implementiert wird.  
  
#### <a name="to-implement-save-functionality"></a>So implementieren Sie die Speicherfunktionalität  
  
1.  Öffnen Sie Form1 in der Entwurfsansicht.  
  
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
  
## <a name="overriding-the-default-behavior-for-performing-updates-inserts-updates-and-deletes"></a>Überschreiben des Standardverhaltens für Aktualisierungen (Einfüge-, Aktualisierungs- und Löschvorgänge)  
  
#### <a name="to-override-the-default-update-behavior"></a>So überschreiben Sie das standardmäßige Updateverhalten  
  
1.  Öffnen Sie im [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] die LINQ to SQL-Datei. (Doppelklicken Sie auf die **Northwind.dbml** Datei **Projektmappen-Explorer**.)  
  
2.  In **Server-Explorer**/**Datenbank-Explorer**, erweitern Sie die Datenbank Northwind **gespeicherte Prozeduren** Knoten, und suchen Sie die  **InsertCustomers**, **UpdateCustomers**, und **DeleteCustomers** gespeicherte Prozeduren.  
  
3.  Ziehen Sie alle drei gespeicherten Prozeduren auf den [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)].  
  
     Die gespeicherten Prozeduren werden dem Methodenbereich als <xref:System.Data.Linq.DataContext>-Methoden hinzugefügt. Weitere Informationen finden Sie unter [DataContext-Methoden (O/R Designer)](../data-tools/datacontext-methods-o-r-designer.md).  
  
4.  Wählen Sie die **Kunden** Entitätsklasse in der [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)].  
  
5.  In der **Eigenschaften** wählen Sie im Fenster der **einfügen** Eigenschaft.  
  
6.  Klicken Sie auf die Auslassungspunkte (...) neben **Laufzeit** zum Öffnen der **Verhalten konfigurieren** Dialogfeld.  
  
7.  Wählen Sie **anpassen**.  
  
8.  Wählen Sie die **InsertCustomers** -Methode in der die **anpassen** Liste.  
  
9. Klicken Sie auf **übernehmen** zum Speichern der Konfiguration für die ausgewählte Klasse und Verhalten.  
  
    > [!NOTE]
    >  Sie können das Verhalten für jede Klasse/Verhalten-Kombination zu konfigurieren, solange Sie klicken Sie auf Weiter **übernehmen** nach jeder Änderung. Wenn Sie die Klasse oder das Verhalten ändern, bevor Sie auf **übernehmen**, ein Warnungsdialogfeld eine Möglichkeit zum Anwenden von Änderungen wird angezeigt.  
  
10. Wählen Sie **Update** in die **Verhalten** Liste.  
  
11. Wählen Sie **anpassen**.  
  
12. Wählen Sie die **UpdateCustomers** -Methode in der die **anpassen** Liste.  
  
     Überprüfen Sie die Liste der **Methodenargumente** und **Klasseneigenschaften** , und beachten Sie, dass zwei **Methodenargumente** und zwei **Klasseneigenschaften**für einige Spalten in der Tabelle. Dies macht es einfacher, Änderungen zu verfolgen und Anweisungen zur Überprüfung von Parallelitätsverletzungen zu erstellen.  
  
13. Zuordnung der **Original_CustomerID** Methodenargument für die **CustomerID (Original)** Klasseneigenschaft.  
  
    > [!NOTE]
    >  Standardmäßig werden Methodenargumente Klasseneigenschaften zugeordnet, wenn die Namen übereinstimmen. Wenn Eigenschaftennamen geändert werden und die Namen von Tabelle und Entitätsklasse nicht mehr übereinstimmen, kann es erforderlich sein, die entsprechende zuzuordnende Klasseneigenschaft auszuwählen, wenn die korrekte Zuordnung vom O/R-Designer nicht festgestellt werden kann. Darüber hinaus Wenn Methodenargumente nicht über gültige Klasseneigenschaften für das Zuordnen zu verfügen, legen Sie die **Klasseneigenschaften** Wert **(keine)**.  
  
14. Klicken Sie auf **übernehmen** zum Speichern der Konfiguration für die ausgewählte Klasse und Verhalten.  
  
15. Wählen Sie **löschen** in die **Verhalten** Liste.  
  
16. Wählen Sie **anpassen**.  
  
17. Wählen Sie die **DeleteCustomers** -Methode in der die **anpassen** Liste.  
  
18. Zuordnung der **Original_CustomerID** Methodenargument für die **CustomerID (Original)** Klasseneigenschaft.  
  
19. Klicken Sie auf **OK**.  
  
> [!NOTE]
>  Auch wenn es kein Problem in dieser exemplarischen Vorgehensweise darstellt, ist Folgendes zu beachten: [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] behandelt bei Einfüge- und Updatevorgängen die datenbankgenerierten Werte bei Identitätsspalten (automatische Inkrementierung) sowie bei ROWGUID- (datenbankgenerierte GUID) und Timestamp-Spalten automatisch. Datenbankgenerierte Werte in anderen Spaltentypen führen unerwartet zu einem NULL-Wert. Um die datenbankgenerierten Werte zurückzugeben, sollte manuell <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A> auf `true` und <xref:System.Data.Linq.Mapping.ColumnAttribute.AutoSync%2A> auf eine der folgenden Einstellungen festgelegt werden: <xref:System.Data.Linq.Mapping.AutoSync>, <xref:System.Data.Linq.Mapping.AutoSync> oder <xref:System.Data.Linq.Mapping.AutoSync>.  
  
## <a name="testing-the-application"></a>Testen der Anwendung  
 Führen Sie die Anwendung erneut aus, um zu überprüfen, ob die **UpdateCustomers** gespeicherten Prozedur wird ordnungsgemäß aktualisiert den Kundendatensatz in der Datenbank.  
  
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
    >  Wenn Ihre Anwendung SQL Server Express Edition, abhängig vom Wert verwendet die **in Ausgabeverzeichnis kopieren** Eigenschaft der Datenbankdatei, die Änderungen möglicherweise nicht angezeigt werden beim Drücken von F5 in Schritt 10. Weitere Informationen finden Sie unter [Vorgehensweise: Verwalten von lokalen Datendateien in Ihr Projekt](../data-tools/how-to-manage-local-data-files-in-your-project.md).  
  
## <a name="next-steps"></a>Nächste Schritte  
 Je nach den Anforderungen Ihrer Anwendung sollten Sie nach dem Erstellen von [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)]-Entitätsklassen mehrere Schritte ausführen. Hier sind einige Verbesserungen, die Sie an dieser Anwendung vornehmen können:  
  
-   Implementieren der Parallelitätsprüfung während der Durchführung von Updates. Weitere Informationen finden Sie unter [optimistische Parallelität: Übersicht über die](http://msdn.microsoft.com/library/c2e38512-d0c8-4807-b30a-cb7e30338694).  
  
-   Hinzufügen von LINQ-Abfragen, um Daten zu filtern. Weitere Informationen finden Sie unter [Introduction to LINQ Queries (c#)](http://msdn.microsoft.com/library/37895c02-268c-41d5-be39-f7d936fa88a8).  
  
## <a name="see-also"></a>Siehe auch  
 [LINQ to SQL-Tools in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [LINQ to SQL](http://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655)   
 [LINQ to SQL-Abfragen](http://msdn.microsoft.com/library/f4897aaa-7f44-4c20-a471-b948c2971aae)   
 [DataContext-Methoden (O/R-Designer)](../data-tools/datacontext-methods-o-r-designer.md)   
 [Gewusst wie: Zuweisen von gespeicherten Prozeduren zum Ausführen von Updates, einfügungen und löschen (O/R Designer)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md)   
 [PAVE Neues in den Daten-Anwendungsentwicklung in Visual Studio 2012](http://msdn.microsoft.com/en-us/3d50d68f-5f44-4915-842f-6d42fce793f1)

