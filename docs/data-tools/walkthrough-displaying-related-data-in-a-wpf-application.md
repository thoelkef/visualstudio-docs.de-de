---
title: "Exemplarische Vorgehensweise: Anzeigen verkn&#252;pfter Daten in einer WPF-Anwendung | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
helpviewer_keywords: 
  - "WPF-Datenbindung [Visual Studio], Exemplarische Vorgehensweisen"
  - "WPF-Designer, Datenbindung"
  - "WPF, Datenbindung in Visual Studio"
ms.assetid: 5c48f188-e9c4-40a6-97d9-67cdb2f90127
caps.latest.revision: 25
caps.handback.revision: 25
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
robots: noindex,nofollow
---
# Exemplarische Vorgehensweise: Anzeigen verkn&#252;pfter Daten in einer WPF-Anwendung
In dieser exemplarischen Vorgehensweise erstellen Sie eine WPF\-Anwendung, die Daten aus Datenbanktabellen anzeigt, die einander über\- bzw. untergeordnet sind.  Die Daten werden in Entitäten in einem Entity Data Model gekapselt.  Die übergeordnete Entität enthält Übersichtsinformationen für eine Gruppe von Aufträgen.  Jede Eigenschaft dieser Entität ist an ein jeweils anderes Steuerelement in der Anwendung gebunden.  Die untergeordnete Entität enthält Details für jeden Auftrag.  Dieser Satz von Daten ist an ein <xref:System.Windows.Controls.DataGrid>\-Steuerelement gebunden.  
  
 In dieser exemplarischen Vorgehensweise werden die folgenden Aufgaben veranschaulicht:  
  
-   Erstellen einer WPF\-Anwendung und eines Entity Data Model, das aus den Daten in der Beispieldatenbank AdventureWorksLT generiert wird.  
  
-   Erstellen eines Satzes von datengebundenen Steuerelementen, die Übersichtsinformationen für eine Gruppe von Aufträgen anzeigen.  Sie erstellen die Steuerelemente, indem Sie eine übergeordnete Entität aus dem **Datenquellenfenster** in den **WPF\-Designer** ziehen.  
  
-   Erstellen eines <xref:System.Windows.Controls.DataGrid>\-Steuerelements, das Details für jeden ausgewählten Auftrag anzeigt.  Sie erstellen die Steuerelemente, indem Sie eine untergeordnete Entität aus dem **Datenquellenfenster** in ein Fenster im **WPF\-Designer** ziehen.  
  
     [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
## Vorbereitungsmaßnahmen  
 Zum Durchführen dieser exemplarischen Vorgehensweise benötigen Sie die folgenden Komponenten:  
  
-   [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
-   Zugriff auf eine gegenwärtig ausgeführte Instanz von SQL Server oder SQL Server Express, die mit der AdventureWorksLT\-Beispieldatenbank verknüpft ist.  Sie können die AdventureWorksLT\-Datenbank von der [CodePlex\-Website](http://go.microsoft.com/fwlink/?linkid=87843) herunterladen.  
  
 Vorkenntnisse in folgenden Konzepten sind außerdem hilfreich, wenn auch für die Durchführung der exemplarischen Vorgehensweise nicht erforderlich:  
  
-   Entity Data Models und ADO.NET Entity Framework.  Weitere Informationen finden Sie unter [Übersicht über das Entity Framework](../Topic/Entity%20Framework%20Overview.md).  
  
-   Arbeiten mit dem WPF\-Designer.  Weitere Informationen finden Sie unter [Übersicht über den WPF\- und Silverlight\-Designer](http://msdn.microsoft.com/de-de/570b7a5c-0c86-4326-a371-c9b63378fc62).  
  
-   WPF\-Datenbindung.  Weitere Informationen finden Sie unter [Übersicht über Datenbindung](../Topic/Data%20Binding%20Overview.md).  
  
## Erstellen des Projekts  
 Erstellen Sie ein neues WPF\-Projekt, um die Auftragsdatensätze anzuzeigen.  
  
#### So erstellen Sie ein neues WPF\-Projekt  
  
1.  Starten Sie Visual Studio.  
  
2.  Zeigen Sie im Menü **Datei** auf **Neu**, und klicken Sie dann auf **Projekt**.  
  
3.  Erweitern Sie **Visual C\#** oder **Visual Basic**, und wählen Sie dann **Windows** aus.  
  
4.  Stellen Sie sicher, dass im Kombinationsfeld am oberen Rand des Dialogfelds **.NET Framework 4** ausgewählt ist.  Das <xref:System.Windows.Controls.DataGrid>\-Steuerelement, das Sie in dieser exemplarischen Vorgehensweise verwenden, ist nur in .NET Framework 4 verfügbar.  
  
5.  Wählen Sie die Projektvorlage **WPF\-Anwendung** aus.  
  
6.  Geben Sie im Feld **Name** Folgendes ein: `AdventureWorksOrdersViewer`.  
  
7.  Klicken Sie auf **OK**.  
  
     Visual Studio erstellt das Projekt `AdventureWorksOrdersViewer`.  
  
## Erstellen eines Entity Data Model für die Anwendung  
 Bevor Sie datengebundene Steuerelemente erstellen können, müssen Sie ein Datenmodell für die Anwendung definieren und es dem **Datenquellenfenster** hinzufügen.  In dieser exemplarischen Vorgehensweise ist das Datenmodell ein Entity Data Model.  
  
#### So erstellen Sie ein Entity Data Model  
  
1.  Klicken Sie im Menü **Daten** auf **Neue Datenquelle hinzufügen**, um den **Assistenten zum Konfigurieren von Datenquellen** zu öffnen.  
  
2.  Klicken Sie auf der Seite **Datenquellentyp auswählen** nacheinander auf **Datenbank** und dann auf **Weiter**.  
  
3.  Klicken Sie auf der Seite **Wählen Sie ein Datenbankmodell aus** auf **Entity Data Model** und dann auf **Weiter**.  
  
4.  Klicken Sie auf der Seite **Modellinhalt auswählen** auf **Aus Datenbank generieren** und dann auf **Weiter**.  
  
5.  Führen Sie auf der Seite **Wählen Sie Ihre Datenverbindung aus** einen der folgenden Schritte aus:  
  
    -   Wenn in der Dropdownliste eine Datenverbindung mit der AdventureWorksLT\-Beispieldatenbank verfügbar ist, wählen Sie diese aus.  
  
         \- oder \-  
  
    -   Klicken Sie auf **Neue Verbindung**, und erstellen Sie eine Verbindung mit der AdventureWorksLT\-Datenbank.  
  
     Stellen Sie sicher, dass die Option **Speichern Sie die Entitätsverbindungseinstellungen in App.Config als** aktiviert ist, und klicken Sie dann auf **Weiter**.  
  
6.  Erweitern Sie auf der Seite **Datenbankobjekte auswählen** den Knoten **Tabellen**, und wählen Sie dann die folgenden Tabellen aus:  
  
    -   **SalesOrderDetail**  
  
    -   **SalesOrderHeader**  
  
7.  Klicken Sie auf **Fertig stellen**.  
  
8.  Erstellen Sie das Projekt.  
  
## Erstellen von datengebundenen Steuerelementen, die Aufträge anzeigen  
 Erstellen Sie Steuerelemente, die Auftragsdatensätze anzeigen, indem Sie die Entität `SalesOrderHeaders` aus dem **Datenquellenfenster** in den WPF\-Designer ziehen.  
  
#### So erstellen Sie datengebundene Steuerelemente, die Auftragsdatensätze anzeigen  
  
1.  Doppelklicken Sie im **Projektmappen\-Explorer** auf MainWindow.xaml.  
  
     Das Fenster wird im WPF\-Designer geöffnet.  
  
2.  Bearbeiten Sie das XAML, um die Eigenschaften **Höhe** und **Breite** auf 800 festzulegen.  
  
3.  Klicken Sie im **Datenquellenfenster** auf das Dropdownmenü für den Knoten **SalesOrderHeaders**, und wählen Sie **Details** aus.  
  
4.  Erweitern Sie den Knoten **SalesOrderHeaders**.  
  
5.  Klicken Sie auf das Dropdownmenü neben **SalesOrderID**, und wählen Sie **ComboBox** aus.  
  
6.  Klicken Sie für jeden der folgenden untergeordneten Knoten des Knotens **SalesOrderHeaders** auf das Dropdownmenü neben dem Knoten, und wählen Sie **Keine** aus:  
  
    -   **RevisionNumber**  
  
    -   **OnlineOrderFlag**  
  
    -   **ShipToAddressID**  
  
    -   **BillToAddressID**  
  
    -   **CreditCardApprovalCode**  
  
    -   **SubTotal**  
  
    -   **TaxAmt**  
  
    -   **Freight**  
  
    -   **rowguid**  
  
    -   **ModifiedDate**  
  
     Diese Aktion verhindert, dass Visual Studio im nächsten Schritt datengebundene Steuerelemente für diese Knoten erstellt.  Bei dieser exemplarischen Vorgehensweise wird davon ausgegangen, dass diese Daten dem Endbenutzer nicht angezeigt werden müssen.  
  
7.  Ziehen Sie den Knoten **SalesOrderHeaders** aus dem **Datenquellenfenster** in das Fenster im **WPF\-Designer**.  
  
     Visual Studio generiert XAML, das einen Satz von Steuerelementen erstellt, die an Daten in der Entität **SalesOrderHeaders** gebunden werden, und Code, der die Daten lädt.  Weitere Informationen zum generierten XAML und Code finden Sie unter [Binden von WPF\-Steuerelementen an Daten in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).  
  
8.  Klicken Sie im Designer auf das Kombinationsfeld neben der Bezeichnung **Sales Order ID**.  
  
9. Aktivieren Sie im Fenster **Eigenschaften** das Kontrollkästchen neben der **IsReadOnly**\-Eigenschaft.  
  
## Erstellen eines DataGrid, das die Auftragsdetails anzeigt  
 Erstellen Sie ein <xref:System.Windows.Controls.DataGrid>\-Steuerelement, das Auftragsdetails anzeigt, indem Sie die Entität `SalesOrderDetails` aus dem **Datenquellenfenster** in den WPF\-Designer ziehen.  
  
#### So erstellen Sie ein DataGrid, das die Auftragsdetails anzeigt  
  
1.  Suchen Sie im **Datenquellenfenster** den Knoten **SalesOrderDetails**, der ein untergeordnetes Element des Knotens **SalesOrderHeaders** ist.  
  
    > [!NOTE]
    >  Es ist auch ein Knoten mit dem Namen **SalesOrderDetails** vorhanden, der ein nebengeordneter Knoten von **SalesOrderHeaders** ist.  Stellen Sie sicher, dass Sie den untergeordneten Knoten des Knotens **SalesOrderHeaders** auswählen.  
  
2.  Erweitern Sie den untergeordneten Knoten **SalesOrderDetails**.  
  
3.  Klicken Sie für jeden der folgenden untergeordneten Knoten des Knotens **SalesOrderDetails** auf das Dropdownmenü neben dem Knoten, und wählen Sie **Keine** aus:  
  
    -   **SalesOrderID**  
  
    -   **SalesOrderDetailID**  
  
    -   **rowguid**  
  
    -   **ModifiedDate**  
  
     Diese Aktion verhindert, dass Visual Studio diese Daten in das <xref:System.Windows.Controls.DataGrid>\-Steuerelement einschließt, das Sie im nächsten Schritt erstellen.  Bei dieser exemplarischen Vorgehensweise wird davon ausgegangen, dass diese Daten dem Endbenutzer nicht angezeigt werden müssen.  
  
4.  Ziehen Sie den untergeordneten Knoten **SalesOrderDetails** aus dem **Datenquellenfenster** in das Fenster im **WPF\-Designer**.  
  
     Visual Studio generiert XAML, um ein neues datengebundenes <xref:System.Windows.Controls.DataGrid>\-Steuerelement zu definieren, und das Steuerelement wird im Designer angezeigt.  Visual Studio aktualisiert außerdem die generierte `GetSalesOrderHeadersQuery`\-Methode in der Code\-Behind\-Datei, um die Daten in die Entität **SalesOrderDetails** einzuschließen.  
  
## Testen der Anwendung  
 Erstellen Sie die Anwendung, und führen Sie sie aus, um zu überprüfen, ob die Auftragsdatensätze angezeigt werden.  
  
#### So testen Sie die Anwendung  
  
1.  Drücken Sie **F5**.  
  
     Die Anwendung wird erstellt und ausgeführt.  Überprüfen Sie Folgendes:  
  
    -   Im Kombinationsfeld **Sales Order ID** wird **71774** angezeigt.  Dies ist die erste Auftrags\-ID in der Entität.  
  
    -   Für jeden Auftrag, den Sie im Kombinationsfeld **Sales Order ID** auswählen, werden im <xref:System.Windows.Controls.DataGrid> detaillierte Auftragsinformationen angezeigt.  
  
2.  Schließen Sie die Anwendung.  
  
## Nächste Schritte  
 Nach dem Abschluss dieser exemplarischen Vorgehensweise erfahren Sie, wie Sie mit dem **Datenquellenfenster** in Visual Studio WPF\-Steuerelemente an andere Typen von Datenquellen binden.  Weitere Informationen finden Sie unter [Exemplarische Vorgehensweise: Binden von WPF\-Steuerelementen an einen WCF\-Datendienst](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md) und [Exemplarische Vorgehensweise: Binden von WPF\-Steuerelementen an ein Dataset](../data-tools/bind-wpf-controls-to-a-dataset.md).  
  
## Siehe auch  
 [Binden von WPF\-Steuerelementen an Daten in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)   
 [Gewusst wie: Anzeigen verknüpfter Daten in WPF\-Anwendungen](../data-tools/display-related-data-in-wpf-applications.md)