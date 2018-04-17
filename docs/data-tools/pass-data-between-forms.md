---
title: Übergeben von Daten zwischen Formularen | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- walkthroughs [Windows Forms], data
- walkthroughs [Visual Studio], data
- data [Visual Studio], passing between forms
- forms, passing data between
- Windows Forms, walkthroughs
ms.assetid: 78bf038b-9296-4fbf-b0e8-d881d1aff0df
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 87fdd9c898b0705c2a3463cb8f9932fda22734ea
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="pass-data-between-forms"></a>Übergeben von Daten zwischen Formularen
Diese exemplarische Vorgehensweise enthält eine Schritt-für-Schritt-Anleitung für die Datenübergabe von einem Formular zum anderen. Verwenden die Tabellen Customers und Orders von Northwind an, ein Formular ermöglicht Benutzern, einen Kunden auszuwählen, und ein zweites Formulars zeigt die ausgewählte Bestellungen des Kunden. In dieser exemplarischen Vorgehensweise wird gezeigt, wie eine Methode für die zweite Form zu erstellen, die Daten aus dem ersten Formular empfängt.  
  
> [!NOTE]
>  Diese exemplarische Vorgehensweise zeigt nur eine Möglichkeit der Datenübergabe zwischen Formularen. Es gibt andere Optionen für die Übergabe von Daten zu einem Formular, einschließlich der Erstellung eines zweiten Konstruktors zum Empfangen von Daten, oder erstellen eine öffentliche Eigenschaft, die mit Daten aus dem ersten Formular festgelegt werden.  
  
 In dieser exemplarischen Vorgehensweise werden u. a. folgende Aufgaben veranschaulicht:  
  
-   Erstellen eines neuen **Windows Forms-Anwendung** Projekt.  
  
-   Erstellen und Konfigurieren eines Datasets mit dem [Datenquellen Konfigurations-Assistenten](../data-tools/media/data-source-configuration-wizard.png).  
  
-   Auswählen des Steuerelements, das für das Formular erstellt werden, beim Ziehen von Elementen aus der **Datenquellen** Fenster. Weitere Informationen finden Sie unter [festlegen, welches Steuerelement erstellt werden, beim Ziehen aus Datenquellenfenster](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).  
  
-   Erstellen eines datengebundenen Steuerelements durch Ziehen von Elementen aus der **Datenquellen** auf das Formular.  
  
-   Erstellen eines zweiten Formulars mit einem Raster für die Datenanzeige.  
  
-   Erstellen einer TableAdapter-Abfrage für das Abrufen der Bestellungen eines bestimmten Kunden.  
  
-   Übergeben von Daten zwischen Formularen.  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
In dieser exemplarischen Vorgehensweise werden die SQL Server Express LocalDB und der Beispieldatenbank Northwind verwendet.  
  
1.  Wenn Sie nicht über SQL Server Express LocalDB verfügen, installieren Sie es entweder aus der [Downloadseite für SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express), oder über die **Installer für Visual Studio**. In der Visual Studio-Installer können SQL Server Express LocalDB installiert werden als Teil der **datenspeicherung und Verarbeitung** arbeitsauslastung oder als eine einzelne Komponente.  
  
2.  Installieren Sie die Beispieldatenbank Northwind, indem folgende Schritte:  

    1. Öffnen Sie in Visual Studio die **Objekt-Explorer von SQL Server** Fenster. (Objekt-Explorer von SQL Server installiert ist, als Teil der **datenspeicherung und Verarbeitung** arbeitsauslastung in der Visual Studio-Installer.) Erweitern Sie die **SQL Server** Knoten. Rechtsklicken Sie auf der LocalDB-Instanz, und wählen Sie **neue Abfrage...** .  

       Ein Abfrage-Editorfenster wird geöffnet.  

    2. Kopieren der [Northwind Transact-SQL-Skript](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) in die Zwischenablage. Dieses T-SQL-Skript die Northwind-Datenbank von Grund auf neu erstellt und mit Daten aufgefüllt.  

    3. Fügen Sie das T-SQL-Skript im Abfrage-Editor, und wählen Sie dann die **Execute** Schaltfläche.  

       Nach kurzer Zeit die Abfrage die Ausführung abgeschlossen ist, und die Northwind-Datenbank wird erstellt.  
  
## <a name="create-the-windows-forms-application"></a>Erstellen Sie die Windows Forms-Anwendung  
  
#### <a name="to-create-the-new-windows-project"></a>So erstellen Sie ein neues Windows-Projekt  
  
1. In Visual Studio auf die **Datei** klicken Sie im Menü **neu**, **Projekt...** .  
  
2. Erweitern Sie entweder **Visual C#-** oder **Visual Basic** im linken Bereich, und wählen Sie dann **klassische Windows-Desktop**.  

3. Wählen Sie im mittleren Bereich die **Windows Forms-App** Projekttyp.  

4. Nennen Sie das Projekt **PassingDataBetweenForms**, und wählen Sie dann **OK**. 
  
     Die **PassingDataBetweenForms** Projekt wird erstellt und hinzugefügt **Projektmappen-Explorer**.  
  
## <a name="create-the-data-source"></a>Die Datenquelle erstellen  
  
#### <a name="to-create-the-data-source"></a>So erstellen Sie die Datenquelle  
  
1.  Klicken Sie im Menü **Daten** auf **Datenquellen anzeigen**.  
  
2.  In der **Datenquellen** wählen **neue Datenquelle hinzufügen** zum Starten der **Datenquellenkonfiguration** Assistenten.  
  
3.  Wählen Sie auf der Seite **Datenquellentyp auswählen** die Option **Datenbank** aus, und klicken Sie auf **Weiter**.  
  
4.  Auf der **Auswählen eines Datenbankmodells** Seite, überprüfen Sie, ob **Dataset** angegeben ist, und klicken Sie dann auf **Weiter**.  
  
5.  Auf der **wählen Sie Ihre Datenverbindung** Seite, führen Sie eine der folgenden:  
  
    -   Wenn in der Dropdownliste eine Datenverbindung zur Beispieldatenbank „Northwind“ verfügbar ist, wählen Sie diese aus.  
  
    -   Wählen Sie **neue Verbindung** zum Starten der **Verbindung hinzufügen/ändern** (Dialogfeld).  
  
6.  Wenn die Datenbank ein Kennwort erfordern sollte und die Option zum Einschließen von sensiblen Daten aktiviert ist, wählen Sie die Option, und klicken Sie dann auf **Weiter**.  
  
7.  Auf der **Verbindungszeichenfolge in der Programmkonfigurationsdatei speichern** auf **Weiter**.  
  
8.  Auf der **Datenbankobjekte auswählen** Seite, erweitern Sie die **Tabellen** Knoten.  
  
9. Wählen Sie die **Kunden** und **Aufträge** Tabellen, und klicken Sie dann auf **Fertig stellen**.  
  
     Die **NorthwindDataSet** wird dem Projekt hinzugefügt und die **Kunden** und **Aufträge** Tabellen angezeigt werden, der **Datenquellen** Fenster.  
  
## <a name="create-the-first-form-form1"></a>Erstellen Sie das erste Formular (Form1)  
 Sie können ein datengebundenes Raster erstellen (eine <xref:System.Windows.Forms.DataGridView> Steuerelement), durch Ziehen der **Kunden** Knoten aus der **Datenquellen** auf das Formular.  
  
#### <a name="to-create-a-data-bound-grid-on-the-form"></a>So erstellen Sie ein datengebundenes Raster auf dem Formular  
  
-   Ziehen Sie den Hauptknoten **Kunden** Knoten aus der **Datenquellen** auf **Form1**.  
  
     Ein <xref:System.Windows.Forms.DataGridView> und ein ToolStrip (<xref:System.Windows.Forms.BindingNavigator>) für die Navigation in den Datensätzen angezeigt werden, auf **Form1**. Ein [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), CustomersTableAdapter <xref:System.Windows.Forms.BindingSource>, und <xref:System.Windows.Forms.BindingNavigator> auf der Komponentenleiste angezeigt.  
  
## <a name="create-the-second-form-form2"></a>Erstellen Sie die zweite Form (Form2)  
  
#### <a name="to-create-a-second-form-to-pass-the-data-to"></a>Erstellen eines zweiten Formulars, an das die Daten übergeben werden  
  
1.  Wählen Sie aus dem Menü **Projekt** die Option **Windows Form hinzufügen** aus.  
  
2.  Lassen Sie den Standardnamen des **Form2**, und klicken Sie auf **hinzufügen**.  
  
3.  Ziehen Sie den Hauptknoten **Aufträge** Knoten aus der **Datenquellen** auf **Form2**.  
  
     Ein <xref:System.Windows.Forms.DataGridView> und ein ToolStrip (<xref:System.Windows.Forms.BindingNavigator>) für die Navigation in den Datensätzen angezeigt werden, auf **Form2**. Ein [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), CustomersTableAdapter <xref:System.Windows.Forms.BindingSource>, und <xref:System.Windows.Forms.BindingNavigator> auf der Komponentenleiste angezeigt.  
  
4.  Löschen der **OrdersBindingNavigator** aus der Komponentenleiste.  
  
     Die **OrdersBindingNavigator** wird nicht mehr in **Form2**.  
  
## <a name="add-a-tableadapter-query-to-form2-to-load-orders-for-the-selected-customer-on-form1"></a>Hinzufügen einer TableAdapter-Abfrage zu Form2 für das Laden von Aufträgen für den ausgewählten Kunden auf Form1  
  
#### <a name="to-create-a-tableadapter-query"></a>Zum Erstellen einer TableAdapter-Abfrage  
  
1.  Doppelklicken Sie auf die **NorthwindDataSet.xsd** Datei **Projektmappen-Explorer**.  
  
2.  Mit der rechten Maustaste die **OrdersTableAdapter**, und wählen Sie **Abfrage hinzufügen**.  
  
3.  Lassen Sie die Standardoption **SQL-Anweisungen**, und klicken Sie dann auf **Weiter**.  
  
4.  Lassen Sie die Standardoption **auswählen, welche Zeilen zurückgegeben, die**, und klicken Sie dann auf **Weiter**.  
  
5.  Hinzufügen eine WHERE-Klausel der Abfrage zurückzugebenden `Orders` basierend auf den `CustomerID`. Die Abfrage müsste ungefähr wie folgt aussehen:  
  
    ```  
    SELECT OrderID, CustomerID, EmployeeID, OrderDate, RequiredDate, ShippedDate, ShipVia, Freight, ShipName, ShipAddress, ShipCity, ShipRegion, ShipPostalCode, ShipCountry  
    FROM Orders   
    WHERE CustomerID = @CustomerID  
    ```  
  
    > [!NOTE]
    >  Überprüfen Sie die korrekte Parametersyntax für Ihre Datenbank. In Microsoft Access, würde die WHERE-Klausel beispielsweise wie folgt aussehen: `WHERE CustomerID = ?`.  
  
6.  Klicken Sie auf **Weiter**.  
  
7.  Für die **füllen Sie einen Namen für die DataTableMethod**, Typ `FillByCustomerID`.  
  
8.  Deaktivieren der **zurückgeben eine "DataTable"** aus, und klicken Sie dann auf **Weiter**.  
  
9. Klicken Sie auf **Fertig stellen**.  
  
## <a name="create-a-method-on-form2-to-pass-data-to"></a>Erstellen Sie eine Methode auf Form2 für das Übergeben von Daten an  
  
#### <a name="to-create-a-method-to-pass-data-to"></a>Erstellen einer Methode für das Übergeben von Daten an  
  
1.  Mit der rechten Maustaste **Form2**, und wählen Sie **Code anzeigen** öffnen **Form2** in der **Code-Editor**.  
  
2.  Fügen Sie folgenden Code zum **Form2** nach der `Form2_Load` Methode:  
  
     [!code-vb[VbRaddataDisplaying#1](../data-tools/codesnippet/VisualBasic/pass-data-between-forms_1.vb)]
     [!code-csharp[VbRaddataDisplaying#1](../data-tools/codesnippet/CSharp/pass-data-between-forms_1.cs)]  
  
## <a name="create-a-method-on-form1-to-pass-data-and-display-form2"></a>Erstellen Sie eine Methode auf Form1 für das Übergeben von Daten und Anzeige von Form2  
  
#### <a name="to-create-a-method-to-pass-data-to-form2"></a>Erstellen einer Methode für das Übergeben von Daten an Form2  
  
1.  In **Form1**mit der rechten Maustaste auf das Customer-Datenraster, und klicken Sie dann auf **Eigenschaften**.  
  
2.  In der **Eigenschaften** Fenster, klicken Sie auf **Ereignisse**.  
  
3.  Doppelklicken Sie auf die **CellDoubleClick** Ereignis.  
  
     Der Code-Editor wird angezeigt.  
  
4.  Aktualisieren Sie die Methodendefinition, sodass sie dem folgenden Beispiel entspricht:  
  
     [!code-csharp[VbRaddataDisplaying#2](../data-tools/codesnippet/CSharp/pass-data-between-forms_2.cs)]
     [!code-vb[VbRaddataDisplaying#2](../data-tools/codesnippet/VisualBasic/pass-data-between-forms_2.vb)]  
  
## <a name="run-the-application"></a>Ausführen der Anwendung  
  
#### <a name="to-run-the-application"></a>So führen Sie die Anwendung aus  
  
-   Drücken Sie F5, um die Anwendung auszuführen.  
  
-   Doppelklicken Sie auf einen Kundendatensatz in **Form1** öffnen **Form2** mit den Bestellungen dieses Kunden.  
  
## <a name="next-steps"></a>Nächste Schritte  
 Entsprechend den Anforderungen an Ihre Anwendung können Sie nach dem Übergeben der Daten zwischen den Formularen noch weitere Schritte ausführen. Sie können an dieser exemplarischen Vorgehensweise beispielsweise folgende Verbesserungen vornehmen:  
  
-   Hinzufügen oder Entfernen von Datenbankobjekten aus dem Dataset durch Bearbeiten. Weitere Informationen finden Sie unter [Erstellen und Konfigurieren von Datasets in Visual Studio](../data-tools/create-and-configure-datasets-in-visual-studio.md).  
  
-   Hinzufügen einer Funktion für das Zurückspeichern von Daten in der Datenbank. Weitere Informationen finden Sie unter [Daten wieder in der Datenbank speichern](../data-tools/save-data-back-to-the-database.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Binden von Windows Forms-Steuerelementen an Daten in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)