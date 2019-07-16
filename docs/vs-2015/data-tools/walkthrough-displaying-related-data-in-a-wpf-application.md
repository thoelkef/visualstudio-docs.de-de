---
title: 'Exemplarische Vorgehensweise: Anzeigen verknüpfter Daten in einer WPF-Anwendung | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- WPF, data binding in Visual Studio
- WPF data binding [Visual Studio], walkthroughs
- WPF Designer, data binding
ms.assetid: 5c48f188-e9c4-40a6-97d9-67cdb2f90127
caps.latest.revision: 25
author: gewarren
ms.author: gewarren
manager: jillfra
robots: noindex,nofollow
ms.openlocfilehash: 560852fc25a3e00134e4ed8b6bd06205248b208d
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/15/2019
ms.locfileid: "65688423"
---
# <a name="walkthrough-displaying-related-data-in-a-wpf-application"></a>Exemplarische Vorgehensweise: Anzeigen verknüpfter Daten in einer WPF-Anwendung
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In dieser exemplarischen Vorgehensweise erstellen Sie eine WPF-Anwendung, in dem Daten aus Datenbanktabellen angezeigt, die eine über-/unterordnungsbeziehung aufweisen. Die Daten in Entitäten in einem Entity Data Model eingekapselt. Die übergeordnete Entität enthält eine Übersicht für eine Gruppe von Bestellungen. Jede Eigenschaft dieser Entität ist an ein anderes Steuerelement in der Anwendung gebunden. Die untergeordnete Entität enthält Details für jede Bestellung. Dieser Satz von Daten gebunden ist, um eine <xref:System.Windows.Controls.DataGrid> Steuerelement.  
  
 In dieser exemplarischen Vorgehensweise werden die folgenden Aufgaben veranschaulicht:  
  
- Erstellen einer WPF-Anwendung und eines Entity Data Model, die aus Daten in der Beispieldatenbank AdventureWorksLT generiert wird.  
  
- Erstellen eines Satzes von datengebundenen Steuerelementen, die Übersicht die Übersichtsinformationen für eine Gruppe von Aufträgen anzeigen. Erstellen Sie die Steuerelemente durch Ziehen einer übergeordneten Entität wird von der **Datenquellen** Fenster **WPF-Designer**.  
  
- Erstellen einer <xref:System.Windows.Controls.DataGrid> -Steuerelement, das zugehörige Details für jede zeigt ausgewählten Auftrag. Erstellen Sie die Steuerelemente durch Ziehen eine untergeordnete Entität aus der **Datenquellen** zum Fenster in **WPF-Designer**.  
  
   [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Vorraussetzungen  
 Zum Durchführen dieser exemplarischen Vorgehensweise benötigen Sie die folgenden Komponenten:  
  
- [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
- Zugriff auf eine laufende Instanz von SQL Server oder SQL Server Express, an die eine AdventureWorksLT-Beispieldatenbank angefügt ist. Sie können die AdventureWorksLT-datenbankvon der [CodePlex-Website](http://go.microsoft.com/fwlink/?linkid=87843).  
  
  Vorkenntnisse der folgenden Konzepte sind ebenfalls hilfreich, wenn auch für die Durchführung der exemplarischen Vorgehensweise nicht erforderlich:  
  
- Entity Data Models und der ADO.NET Entity Framework. Weitere Informationen finden Sie unter [Übersicht über Entity Framework](https://msdn.microsoft.com/library/a2166b3d-d8ba-4a0a-8552-6ba1e3eaaee0).  
  
- Arbeiten mit dem WPF-Designer. Weitere Informationen finden Sie unter [WPF- und Silverlight Designer Overview](https://msdn.microsoft.com/570b7a5c-0c86-4326-a371-c9b63378fc62).  
  
- WPF-Datenbindung. Weitere Informationen finden Sie unter [Übersicht über Datenbindung](https://msdn.microsoft.com/library/c707c95f-7811-401d-956e-2fffd019a211).  
  
## <a name="creating-the-project"></a>Erstellen des Projekts  
 Erstellen Sie ein neues WPF-Projekt, um die Datensätze anzuzeigen.  
  
#### <a name="to-create-a-new-wpf-project"></a>So erstellen Sie ein neues WPF-Projekt  
  
1. Starten Sie Visual Studio.  
  
2. Zeigen Sie im Menü **Datei** auf **Neu**, und klicken Sie dann auf **Projekt**.  
  
3. Erweitern Sie **Visual C#-** oder **Visual Basic**, und wählen Sie dann **Windows**.  
  
4. Stellen Sie sicher, dass **.NET Framework 4** im Kombinationsfeld am oberen Rand des Dialogfelds ausgewählt ist. Die <xref:System.Windows.Controls.DataGrid> -Steuerelement, das Sie in dieser exemplarischen Vorgehensweise verwenden, ist nur in .NET Framework 4 verfügbar.  
  
5. Wählen Sie die Projektvorlage **WPF-Anwendung** aus.  
  
6. Geben Sie im Feld **Name** `AdventureWorksOrdersViewer`ein.  
  
7. Klicken Sie auf **OK**.  
  
     Visual Studio erstellt die `AdventureWorksOrdersViewer` Projekt.  
  
## <a name="creating-an-entity-data-model-for-the-application"></a>Erstellen eines Entity Data Models für die Anwendung  
 Ehe Sie datengebundene Steuerelemente erstellen können, müssen Sie ein Datenmodell für die Anwendung definieren und es dem **Datenquellenfenster** hinzufügen. In dieser exemplarischen Vorgehensweise wird das Datenmodell ein Entity Data Model.  
  
#### <a name="to-create-an-entity-data-model"></a>So erstellen Sie ein Entity Data Model  
  
1. Auf der **Daten** Menü klicken Sie auf **neue Datenquelle hinzufügen** zum Öffnen der **Assistenten zur Datenquellenkonfiguration**.  
  
2. Auf der **wählen Sie einen Datenquellentyp** auf **Datenbank**, und klicken Sie dann auf **Weiter**.  
  
3. Auf der **Auswählen eines Datenbankmodells** auf **Entity Data Model**, und klicken Sie dann auf **Weiter**.  
  
4. Auf der **auswählen des Modellinhalts** auf **aus Datenbank generieren**, und klicken Sie dann auf **Weiter**.  
  
5. Auf der **wählen Sie Ihre Datenverbindung** eine der folgenden:  
  
   - Wenn in der Dropdownliste eine Datenverbindung zur Beispieldatenbank "AdventureWorksLT" verfügbar ist, wählen Sie diese aus.  
  
      - oder -   
  
   - Klicken Sie auf **neue Verbindung** , und erstellen Sie eine Verbindung mit der AdventureWorksLT-Datenbank.  
  
     Stellen Sie sicher, dass die **Entitätsverbindungseinstellungen in App.Config speichern als** Option ausgewählt ist, und klicken Sie dann auf **Weiter**.  
  
6. Auf der **Datenbankobjekte auswählen** Seite **Tabellen**, und wählen Sie dann die folgenden Tabellen:  
  
   - **SalesOrderDetail**  
  
   - **SalesOrderHeader**  
  
7. Klicken Sie auf **Fertig stellen**.  
  
8. Erstellen Sie das Projekt.  
  
## <a name="creating-data-bound-controls-that-display-the-orders"></a>Erstellen datengebundene Steuerelemente zur Anzeige von Bestellungen  
 Erstellen Sie Steuerelemente zum Anzeigen der Datensätze durch Ziehen der `SalesOrderHeaders` Entität aus der **Datenquellen** in den WPF-Designer.  
  
#### <a name="to-create-data-bound-controls-that-display-the-order-records"></a>Um datengebundene Steuerelemente zu erstellen, die Datensätze anzeigen  
  
1. In **Projektmappen-Explorer**, doppelklicken Sie auf "MainWindow.xaml".  
  
    Das Fenster wird automatisch im WPF-Designer geöffnet.  
  
2. Bearbeiten der XAML daher **Höhe** und **Breite** auf 800 Eigenschaften festgelegt werden  
  
3. In der **Datenquellen** Fenster, klicken Sie auf das Dropdownmenü für die **SalesOrderHeaders** Knoten, und wählen **Details**.  
  
4. Erweitern Sie den Knoten **SalesOrderHeaders**.  
  
5. Klicken Sie auf das Dropdownmenü neben **SalesOrderID** , und wählen Sie **"ComboBox"**.  
  
6. Für jede der folgenden untergeordneten Knoten von der **SalesOrderHeaders** Knoten, klicken Sie auf dem Dropdownmenü neben den Knoten, und wählen Sie **keine**:  
  
   - **RevisionNumber**  
  
   - **OnlineOrderFlag**  
  
   - **ShipToAddressID**  
  
   - **BillToAddressID**  
  
   - **CreditCardApprovalCode**  
  
   - **SubTotal**  
  
   - **TaxAmt**  
  
   - **Freight**  
  
   - **Rowguid**  
  
   - **ModifiedDate**  
  
     Durch diese Aktion wird Visual Studio daran gehindert, im nächsten Schritt datengebundene Steuerelemente für diese Knoten zu erstellen. Bei dieser exemplarischen Vorgehensweise wird davon ausgegangen, dass der Endbenutzer diese Daten nicht sehen muss.  
  
7. Von der **Datenquellen** ziehen Sie die **SalesOrderHeaders** Knoten aus, um das Fenster in **WPF-Designer**.  
  
    Visual Studio generiert XAML, die einen Satz von Steuerelementen, die an Daten gebunden werden, erstellt die **SalesOrderHeaders** Entität und Code, der die Daten lädt. Weitere Informationen zu den generierten XAML und Code finden Sie unter [Binden von WPF-Steuerelementen an Daten in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).  
  
8. Im Designer, klicken Sie auf das Kombinationsfeld neben dem **Sales Order ID** Bezeichnung.  
  
9. Aktivieren Sie im Fenster **Eigenschaften** das Kontrollkästchen neben der Eigenschaft **IsReadOnly**.  
  
## <a name="creating-a-datagrid-that-displays-the-order-details"></a>Erstellen ein DataGrid-Steuerelement, das den Details der Bestellung anzeigt  
 Erstellen Sie eine <xref:System.Windows.Controls.DataGrid> -Steuerelement, das zeigt Auftragsdetails durch Ziehen der `SalesOrderDetails` Entität aus der **Datenquellen** in den WPF-Designer.  
  
#### <a name="to-create-a-datagrid-that-displays-the-order-details"></a>Ein DataGrid-Steuerelement zu erstellen, die die Auftragsdetails werden angezeigt.  
  
1. In der **Datenquellen** Fenster Suchen der **SalesOrderDetails** Knoten, der ein untergeordnetes Element der **SalesOrderHeaders** Knoten.  
  
   > [!NOTE]
   > Es gibt auch eine **SalesOrderDetails** Knoten, die einen Peer der **SalesOrderHeaders** Knoten. Stellen Sie sicher, dass Sie den untergeordneten Knoten des Auswählen der **SalesOrderHeaders** Knoten.  
  
2. Erweitern Sie das untergeordnete Element **SalesOrderDetails** Knoten.  
  
3. Für jede der folgenden untergeordneten Knoten von der **SalesOrderDetails** Knoten, klicken Sie auf dem Dropdownmenü neben den Knoten, und wählen Sie **keine**:  
  
   - **SalesOrderID**  
  
   - **SalesOrderDetailID**  
  
   - **Rowguid**  
  
   - **ModifiedDate**  
  
     Diese Aktion verhindert, dass Visual Studio einschließlich diese Daten in die <xref:System.Windows.Controls.DataGrid> Kontrolle, die Sie im nächsten Schritt erstellen. Bei dieser exemplarischen Vorgehensweise wird davon ausgegangen, dass der Endbenutzer diese Daten nicht sehen muss.  
  
4. Von der **Datenquellen** Fenster ziehen Sie das untergeordnete Element **SalesOrderDetails** Knoten aus, um das Fenster in **WPF-Designer**.  
  
    Visual Studio generiert XAML zum Definieren einer neuen datengebundenes <xref:System.Windows.Controls.DataGrid> -Steuerelement, und das Steuerelement im Designer angezeigt. Visual Studio aktualisiert auch die generierte `GetSalesOrderHeadersQuery` -Methode in der CodeBehind-Datei die Daten in die **SalesOrderDetails** Entität.  
  
## <a name="testing-the-application"></a>Testen der Anwendung  
 Erstellen Sie und führen Sie die Anwendung aus, um sicherzustellen, dass die Datensätze angezeigt.  
  
#### <a name="to-test-the-application"></a>So testen Sie die Anwendung  
  
1. Drücken Sie **F5**.  
  
     Die Anwendung wird erstellt und ausgeführt. Überprüfen Sie Folgendes:  
  
    - Die **Sales Order ID** Kombinationsfeld zeigt **71774**. Dies ist die erste Bestell-ID in der Entität.  
  
    - Für jede Bestellung wählen Sie in der **Sales Order ID** Kombinationsfeld, detaillierte Bestellinformationen wird angezeigt, der <xref:System.Windows.Controls.DataGrid>.  
  
2. Schließen Sie die Anwendung.  
  
## <a name="next-steps"></a>Nächste Schritte  
 Nach Abschluss dieser exemplarischen Vorgehensweise können Sie Informationen zum Verwenden der **Datenquellen** Fenster in Visual Studio zum Binden von WPF-Steuerelementen an andere Typen von Datenquellen. Weitere Informationen finden Sie unter [Binden von WPF-Steuerelemente an einen WCF-Datendienst](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md) und [Binden von WPF-Steuerelemente zu einem Dataset](../data-tools/bind-wpf-controls-to-a-dataset.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Binden von WPF-Steuerelementen an Daten in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)   
 [Anzeigen zugehöriger Daten in WPF-Anwendungen](../data-tools/display-related-data-in-wpf-applications.md)