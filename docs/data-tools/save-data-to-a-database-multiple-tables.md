---
title: Speichern von Daten in einer Datenbank (mehrere Tabellen) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- updating datasets, walkthroughs
- data [Visual Studio], saving
- saving data, walkthroughs
- data [Visual Studio], updating
ms.assetid: 7ebe03da-ce8c-4cbc-bac0-a2fde4ae4d07
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 2d47bd0bf619294aa577fdb2e42bed4e912907fc
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="save-data-to-a-database-multiple-tables"></a>Speichern von Daten in einer Datenbank (mehrere Tabellen)
Eines der häufigsten Szenarios in der Anwendungsentwicklung ist das Anzeigen von Daten auf einem Formular in einer Windows-Anwendung, das Bearbeiten der Daten und das Senden der aktualisierten Daten zurück an die Datenbank. In dieser exemplarischen Vorgehensweise wird ein Formular erstellt, in dem Daten aus zwei verknüpften Tabellen angezeigt werden. Darüber hinaus wird gezeigt, wie Datensätze bearbeitet und Änderungen wieder in der Datenbank gespeichert werden. In diesem Beispiel werden die Tabellen `Customers` und `Orders` aus der Beispieldatenbank Northwind verwendet.  
  
 Sie können Daten in der Anwendung wieder in der Datenbank speichern, indem Sie die `Update`-Methode eines TableAdapter aufrufen. Beim Ziehen von Tabellen aus der **Datenquellen** auf das Formular, den Code, der zum Speichern von Daten erforderlich ist, wird automatisch hinzugefügt. Alle weiteren Tabellen, die zu einem Formular hinzugefügt werden muss das manuelle Hinzufügen dieses Codes. In dieser exemplarischen Vorgehensweise wird veranschaulicht, wie Code hinzugefügt wird, um Aktualisierungen aus mehreren Tabellen zu speichern.  
  
> [!NOTE]
>  Die angezeigten Dialogfelder und Menübefehle, die Sie sehen möglicherweise unterscheiden sich von denen je nach Ihren aktiven Einstellungen oder der Edition, die Sie verwenden in der Hilfe beschriebenen. Klicken Sie im Menü **Extras** auf **Einstellungen importieren und exportieren** , um die Einstellungen zu ändern. Weitere Informationen finden Sie unter [Personalisieren von Visual Studio-IDE](../ide/personalizing-the-visual-studio-ide.md).  
  
 In dieser exemplarischen Vorgehensweise werden u. a. folgende Aufgaben veranschaulicht:  
  
-   Erstellen eines neuen **Windows Forms-Anwendung** Projekt.  
  
-   Erstellen und Konfigurieren einer Datenquelle in Ihrer Anwendung mit der [Datenquellen Konfigurations-Assistenten](../data-tools/media/data-source-configuration-wizard.png).  
  
-   Festlegen der Steuerelemente für die Elemente in der [Datenquellenfenster](add-new-data-sources.md). Weitere Informationen finden Sie unter [festlegen, welches Steuerelement erstellt werden, beim Ziehen aus Datenquellenfenster](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).  
  
-   Erstellen datengebundene Steuerelemente durch Ziehen von Elementen aus der **Datenquellen** auf das Formular.  
  
-   Ändern einige Datensätze in jeder Tabelle im Dataset.  
  
-   Ändern von Code zum Zurücksenden der aktualisierten Daten des Datasets an die Datenbank.  
  
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
 Der erste Schritt ist die Erstellung einer **Windows Forms-Anwendung**. Während dieses Schritts ist ein Name zugewiesen, um das Projekt optional, aber wir müssen Geben sie einen Namen, da wir das Projekt später speichern zu müssen.  
  
#### <a name="to-create-the-new-windows-forms-application-project"></a>Um das neue Windows Forms-Anwendungsprojekt zu erstellen.  
  
1. In Visual Studio auf die **Datei** klicken Sie im Menü **neu**, **Projekt...** .  
  
2. Erweitern Sie entweder **Visual C#-** oder **Visual Basic** im linken Bereich, und wählen Sie dann **klassische Windows-Desktop**.  

3. Wählen Sie im mittleren Bereich die **Windows Forms-App** Projekttyp.  

4. Nennen Sie das Projekt **UpdateMultipleTablesWalkthrough**, und wählen Sie dann **OK**. 
  
     Die **UpdateMultipleTablesWalkthrough** Projekt wird erstellt und hinzugefügt **Projektmappen-Explorer**.  
  
## <a name="create-the-data-source"></a>Die Datenquelle erstellen  
 Dieser Schritt wird eine Datenquelle erstellt, aus der Northwind-Datenbank mithilfe der **Datenquellen Konfigurations-Assistenten**. Sie benötigen Zugriff auf die Beispieldatenbank Northwind, um die Verbindung herstellen zu können. Informationen zum Einrichten der Northwind-Beispieldatenbank, finden Sie unter [Vorgehensweise: Installieren von Beispieldatenbanken](../data-tools/installing-database-systems-tools-and-samples.md).  
  
#### <a name="to-create-the-data-source"></a>So erstellen Sie die Datenquelle  
  
1.  Auf der **Daten** klicken Sie im Menü **Datenquellen anzeigen**.  
  
2.  In der **Datenquellen** wählen**neue Datenquelle hinzufügen** zum Starten der **Datenquellen Konfigurations-Assistenten**.  
  
3.  Auf der **wählen Sie einen Datenquellentyp** wählen **Datenbank**, und wählen Sie dann **Weiter**.  
  
4.  Auf der **wählen Sie Ihre Datenverbindung** Bildschirm führen Sie einen der folgenden:  
  
    -   Wenn in der Dropdownliste eine Datenverbindung zur Beispieldatenbank „Northwind“ verfügbar ist, wählen Sie diese aus.  
  
         - oder -   
  
    -   Wählen Sie **neue Verbindung** So öffnen die **Verbindung hinzufügen/ändern** (Dialogfeld).  
  
5.  Wenn die Datenbank ein Kennwort erfordern sollte, wählen Sie die Option auf Einbeziehung vertraulicher Daten, und wählen Sie dann **Weiter**.  
  
6.  Auf der **Verbindungszeichenfolge in der Programmkonfigurationsdatei speichern**Option **Weiter**.  
  
7.  Auf der **Datenbankobjekte auswählen**Bildschirm, erweitern Sie die **Tabellen** Knoten.  
  
8.  Wählen Sie die **Kunden** und **Aufträge** Tabellen, und wählen Sie dann **Fertig stellen**.  
  
     Die **NorthwindDataSet** wird dem Projekt hinzugefügt und die Tabellen werden der **Datenquellen** Fenster.  
  
## <a name="set-the-controls-to-be-created"></a>Legen Sie die zu erstellenden Steuerelemente  
 Für diese exemplarische Vorgehensweise, die Daten in der `Customers` Tabelle befindet sich in einem **Details** Layout, in dem die Daten in einzelnen Steuerelementen angezeigt. Die Daten aus der `Orders` Tabelle befindet sich in einem **Raster** Layouts, das angezeigt wird ein <xref:System.Windows.Forms.DataGridView> Steuerelement.  
  
#### <a name="to-set-the-drop-type-for-the-items-in-the-data-sources-window"></a>So legen Sie den Ablagetyp für die Elemente im Datenquellenfenster fest  
  
1.  In der **Datenquellen** Fenster, erweitern Sie die **Kunden** Knoten.  
  
2.  Auf der **Kunden** Knoten **Details** aus der Steuerungsliste so ändern Sie die Kontrolle über die **Kunden** Tabelle in einzelne Steuerelemente. Weitere Informationen finden Sie unter [festlegen, welches Steuerelement erstellt werden, beim Ziehen aus Datenquellenfenster](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).  
  
## <a name="create-the-data-bound-form"></a>Erstellen des datengebundenen Formulars  
 Sie können die datengebundenen Steuerelemente erstellen, durch Ziehen von Elementen aus der **Datenquellen** auf das Formular.  
  
#### <a name="to-create-data-bound-controls-on-the-form"></a>So erstellen Sie datengebundene Steuerelemente auf dem Formular  
  
1.  Ziehen Sie den Hauptknoten **Kunden** Knoten aus der **Datenquellen** auf **Form1**.  
  
     Auf dem Formular werden datengebundene Steuerelemente mit beschreibenden Bezeichnungen sowie ein Toolstrip (<xref:System.Windows.Forms.BindingNavigator>) für die Navigation in den Datensätzen angezeigt. Ein [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), `CustomersTableAdapter`, <xref:System.Windows.Forms.BindingSource>, und <xref:System.Windows.Forms.BindingNavigator> auf der Komponentenleiste angezeigt.  
  
2.  Ziehen Sie den zugehörigen **Aufträge** Knoten aus der **Datenquellen** auf **Form1**.  
  
    > [!NOTE]
    >  Den zugehörigen **Aufträge** Knoten befindet sich unterhalb der **Fax** Spalte und ist ein untergeordneter Knoten der **Kunden** Knoten.  
  
     Auf dem Formular wird ein <xref:System.Windows.Forms.DataGridView>-Steuerelement und ein Toolstrip (<xref:System.Windows.Forms.BindingNavigator>) für die Navigation in den Datensätzen angezeigt. Ein `OrdersTableAdapter` und <xref:System.Windows.Forms.BindingSource> auf der Komponentenleiste angezeigt.  
  
## <a name="add-code-to-update-the-database"></a>Fügen Sie Code zum Aktualisieren der Datenbank hinzu  
 Sie aktualisieren die Datenbank durch Aufrufen der `Update` Methoden die **Kunden** und **Aufträge** TableAdapters. Standardmäßig wird ein Ereignishandler für die **speichern** Schaltfläche der<xref:System.Windows.Forms.BindingNavigator> Code des Formulars zum Senden von Updates an der Datenbank hinzugefügt. Dieses Verfahren ändert den Code, um Updates in der richtigen Reihenfolge zu senden. Dies verhindert, dass durch das Auslösen Fehler der referenziellen Integrität. Mit dem Code wird außerdem die Fehlerbehandlung implementiert, indem der Aktualisierungsaufruf mit einem Try-Catch-Block umschlossen wird. Sie können den Code entsprechend den Anforderungen der Anwendung anpassen.  
  
> [!NOTE]
>  Aus Gründen der Übersichtlichkeit wird in dieser exemplarischen Vorgehensweise keine Transaktion verwendet. Allerdings werden Sie aktualisiert, zwei oder mehr verknüpfte Tabellen, enthalten Sie alle Aktualisierungslogik einer Transaktion. Eine Transaktion ist ein Prozess, der sicherstellt, dass alle zugehörige Änderungen an einer Datenbank erfolgreich sind, bevor ein Commit für Änderungen ausgeführt wird. Weitere Informationen finden Sie unter [Transaktionen und Parallelität](/dotnet/framework/data/adonet/transactions-and-concurrency).  
  
#### <a name="to-add-update-logic-to-the-application"></a>So fügen Sie der Anwendung Aktualisierungslogik hinzu  
  
1.  Wählen Sie die **speichern** Schaltfläche auf der <xref:System.Windows.Forms.BindingNavigator>. Dies öffnet den Code-Editor die `bindingNavigatorSaveItem_Click` -Ereignishandler.  
  
2.  Ändern Sie den Code im Ereignishandler, sodass die `Update`-Methoden der verknüpften TableAdapters aufgerufen werden. Mit folgendem Code werden zunächst drei temporäre Datentabellen zum Speichern der aktualisierten Informationen für jeden <xref:System.Data.DataRowState> (<xref:System.Data.DataRowState.Deleted>, <xref:System.Data.DataRowState.Added> und <xref:System.Data.DataRowState.Modified>) erstellt. Updates werden dann in der richtigen Reihenfolge ausgeführt. Der Code sollte wie folgt aussehen:  
  
     [!code-vb[VbRaddataSaving#10](../data-tools/codesnippet/VisualBasic/save-data-to-a-database-multiple-tables_1.vb)]
     [!code-csharp[VbRaddataSaving#10](../data-tools/codesnippet/CSharp/save-data-to-a-database-multiple-tables_1.cs)]  
  
## <a name="test-the-application"></a>Testen der Anwendung  
  
#### <a name="to-test-the-application"></a>So testen Sie die Anwendung  
  
1.  Wählen Sie **F5**.  
  
2.  Nehmen Sie in jeder Tabelle einige Änderungen an den Daten eines oder mehrerer Datensätze vor.  
  
3.  Wählen Sie die **speichern** Schaltfläche.  
  
4.  Überprüfen Sie die Werte in der Datenbank, um sicherzustellen, dass die Änderungen gespeichert wurden.  
  
  
## <a name="see-also"></a>Siehe auch  
 [Rückspeichern von Daten in der Datenbank](../data-tools/save-data-back-to-the-database.md)