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
author: jillre
ms.author: jillfra
manager: jillfra
robots: noindex,nofollow
ms.openlocfilehash: c44b949daabf587dbca5d8a5d1d932afca2c1f9c
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72602469"
---
# <a name="walkthrough-displaying-related-data-in-a-wpf-application"></a>Exemplarische Vorgehensweise: Anzeigen verknüpfter Daten in einer WPF-Anwendung
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In dieser exemplarischen Vorgehensweise erstellen Sie eine WPF-Anwendung, die Daten aus Datenbanktabellen anzeigt, die über eine Beziehung zwischen über-und untergeordneten Elementen verfügen. Die Daten werden in Entitäten in einem Entity Data Model gekapselt. Die übergeordnete Entität enthält Übersichts Informationen für eine Reihe von Aufträgen. Jede Eigenschaft dieser Entität wird an ein anderes Steuerelement in der Anwendung gebunden. Die untergeordnete Entität enthält Details für jede Bestellung. Diese Datenmenge ist an ein <xref:System.Windows.Controls.DataGrid> Steuerelement gebunden.

 In dieser exemplarischen Vorgehensweise werden die folgenden Aufgaben veranschaulicht:

- Erstellen einer WPF-Anwendung und eines Entity Data Model, das aus Daten in der AdventureWorksLT-Beispieldatenbank generiert wird.

- Erstellen eines Satzes Daten gebundener Steuerelemente, die Übersichts Informationen für eine Reihe von Aufträgen anzeigen. Sie erstellen die Steuerelemente, indem Sie eine übergeordnete Entität aus dem **Datenquellen** Fenster in **den WPF-Designer**ziehen.

- Erstellen eines <xref:System.Windows.Controls.DataGrid>-Steuer Elements, das verwandte Details für jede ausgewählte Bestellung anzeigt. Sie erstellen die Steuerelemente, indem Sie eine untergeordnete Entität aus dem **Datenquellen** Fenster in ein Fenster im **WPF-Designer**ziehen.

   [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Erforderliche Voraussetzungen
 Zum Durchführen dieser exemplarischen Vorgehensweise benötigen Sie die folgenden Komponenten:

- [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]

- Zugriff auf eine laufende Instanz von SQL Server oder SQL Server Express, an die eine AdventureWorksLT-Beispieldatenbank angefügt ist. Sie können die AdventureWorksLT-Datenbank von der [CodePlex-Website](http://go.microsoft.com/fwlink/?linkid=87843)herunterladen.

  Vorkenntnisse der folgenden Konzepte sind ebenfalls hilfreich, wenn auch für die Durchführung der exemplarischen Vorgehensweise nicht erforderlich:

- Entity Data Models und der ADO.NET Entity Framework. Weitere Informationen finden Sie unter [Entity Framework Übersicht](https://msdn.microsoft.com/library/a2166b3d-d8ba-4a0a-8552-6ba1e3eaaee0).

- Arbeiten mit dem WPF-Designer. Weitere Informationen finden Sie unter [Übersicht über WPF-und Silverlight-Designer](https://msdn.microsoft.com/570b7a5c-0c86-4326-a371-c9b63378fc62).

- WPF-Datenbindung. Weitere Informationen finden Sie in der [Übersicht über die Datenbindung](https://msdn.microsoft.com/library/c707c95f-7811-401d-956e-2fffd019a211).

## <a name="creating-the-project"></a>Erstellen des Projekts
 Erstellen Sie ein neues WPF-Projekt, um die Bestelldaten Sätze anzuzeigen.

#### <a name="to-create-a-new-wpf-project"></a>So erstellen Sie ein neues WPF-Projekt

1. Starten Sie Visual Studio.

2. Zeigen Sie im Menü **Datei** auf **Neu**, und klicken Sie dann auf **Projekt**.

3. Erweitern **Sie C# Visual** oder **Visual Basic**, und wählen Sie dann **Windows**aus.

4. Stellen Sie sicher, dass **.NET Framework 4** im Kombinations Feld am oberen Rand des Dialog Felds ausgewählt ist. Das <xref:System.Windows.Controls.DataGrid> Steuerelement, das Sie in dieser exemplarischen Vorgehensweise verwenden, ist nur in der .NET Framework 4 verfügbar.

5. Wählen Sie die Projektvorlage **WPF-Anwendung** aus.

6. Geben Sie im Feld **Name** `AdventureWorksOrdersViewer`ein.

7. Klicken Sie auf **OK**.

     Visual Studio erstellt das `AdventureWorksOrdersViewer` Projekt.

## <a name="creating-an-entity-data-model-for-the-application"></a>Erstellen eines Entity Data Model für die Anwendung
 Ehe Sie datengebundene Steuerelemente erstellen können, müssen Sie ein Datenmodell für die Anwendung definieren und es dem **Datenquellenfenster** hinzufügen. In dieser exemplarischen Vorgehensweise ist das Datenmodell eine Entity Data Model.

#### <a name="to-create-an-entity-data-model"></a>So erstellen Sie ein Entity Data Model

1. Klicken Sie im Menü **Daten** auf **neue Datenquelle hinzufügen** , um den **Assistenten zum Konfigurieren von Datenquellen**zu öffnen.

2. Klicken Sie auf der Seite **Daten Quellentyp auswählen** auf **Datenbank**, und klicken Sie dann auf **weiter**.

3. Klicken Sie auf der Seite **Datenbankmodell auswählen** auf **Entity Data Model**, und klicken Sie dann auf **weiter**.

4. Klicken Sie auf der Seite **Modell Inhalte auswählen** auf **aus Datenbank generieren**, und klicken Sie dann auf **weiter**.

5. Führen Sie auf der Seite **Wählen Sie Ihre Datenverbindung** aus einen der folgenden Schritte aus:

   - Wenn in der Dropdownliste eine Datenverbindung zur Beispieldatenbank "AdventureWorksLT" verfügbar ist, wählen Sie diese aus.

      - oder -

   - Klicken Sie auf **neue Verbindung** , und erstellen Sie eine Verbindung mit der AdventureWorksLT-Datenbank.

     Stellen Sie sicher, dass die Option **Entitäts Verbindungseinstellungen in app. config speichern als** ausgewählt ist, und klicken Sie dann auf **weiter**.

6. Erweitern Sie auf der Seite **Datenbankobjekte auswählen** den Knoten **Tabellen**, und wählen Sie dann die folgenden Tabellen aus:

   - **SalesOrderDetail**

   - **SalesOrderHeader**

7. Klicken Sie auf **Fertig stellen**.

8. Erstellen Sie das Projekt.

## <a name="creating-data-bound-controls-that-display-the-orders"></a>Erstellen Daten gebundener Steuerelemente, die die Bestellungen anzeigen
 Erstellen Sie Steuerelemente, die Bestelldaten Sätze anzeigen, indem Sie die `SalesOrderHeaders` Entität aus dem **Datenquellen** Fenster in den WPF-Designer ziehen.

#### <a name="to-create-data-bound-controls-that-display-the-order-records"></a>So erstellen Sie Daten gebundene Steuerelemente, die die Bestelldaten Sätze anzeigen

1. Doppelklicken Sie in **Projektmappen-Explorer**auf die Datei MainWindow. XAML.

    Das Fenster wird automatisch im WPF-Designer geöffnet.

2. Bearbeiten Sie den XAML-Code, sodass die Eigenschaften **height** und **Width** auf 800 festgelegt sind.

3. Klicken Sie im Fenster **Datenquellen** auf das Dropdown Menü für den Knoten **SalesOrderHeaders** , und wählen Sie **Details**aus.

4. Erweitern Sie den Knoten **SalesOrderHeaders**.

5. Klicken Sie auf das Dropdown Menü neben **SalesOrderID** , und wählen Sie **ComboBox**aus.

6. Klicken Sie für jeden der folgenden untergeordneten Knoten des Knotens **SalesOrderHeaders** auf das Dropdown Menü neben dem Knoten, und wählen Sie **keine**aus:

   - **RevisionNumber**

   - **OnlineOrderFlag**

   - **Ship-adressssid**

   - **Abrechnungs-SSID**

   - **CreditCardApprovalCode**

   - **Teilergebnis**

   - **TaxAmt**

   - **FRA**

   - **Rowguid**

   - **ModifiedDate**

     Durch diese Aktion wird Visual Studio daran gehindert, im nächsten Schritt datengebundene Steuerelemente für diese Knoten zu erstellen. Bei dieser exemplarischen Vorgehensweise wird davon ausgegangen, dass der Endbenutzer diese Daten nicht sehen muss.

7. Ziehen Sie aus dem Fenster **Datenquellen** den Knoten **SalesOrderHeaders** in das Fenster im **WPF-Designer**.

    Visual Studio generiert XAML, das eine Reihe von Steuerelementen erstellt, die an Daten in der **SalesOrderHeaders** -Entität gebunden sind, und Code, der die Daten lädt. Weitere Informationen über den generierten XAML-Code und Code finden [Sie unterbinden von WPF-Steuerelementen an Daten in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).

8. Klicken Sie im Designer auf das Kombinations Feld neben der Bezeichnung **Sales Order ID** .

9. Aktivieren Sie im Fenster **Eigenschaften** das Kontrollkästchen neben der Eigenschaft **IsReadOnly**.

## <a name="creating-a-datagrid-that-displays-the-order-details"></a>Erstellen eines DataGrid-Steuerelement, das die Bestell Details anzeigt
 Erstellen Sie ein <xref:System.Windows.Controls.DataGrid> Steuerelement, das Bestelldetails anzeigt, indem Sie die `SalesOrderDetails` Entität aus dem **Datenquellen** Fenster in den WPF-Designer ziehen.

#### <a name="to-create-a-datagrid-that-displays-the-order-details"></a>So erstellen Sie ein DataGrid-Steuerelement, das die Bestelldetails anzeigt

1. Suchen Sie im Fenster **Datenquellen** den Knoten **SalesOrderDetails** , der ein untergeordnetes Element des Knotens **SalesOrderHeaders** ist.

   > [!NOTE]
   > Es gibt auch einen **SalesOrderDetails** -Knoten, der ein Peer des **SalesOrderHeaders** -Knotens ist. Stellen Sie sicher, dass Sie den untergeordneten Knoten des Knotens **SalesOrderHeaders** auswählen.

2. Erweitern Sie den untergeordneten Knoten **SalesOrderDetails** .

3. Klicken Sie für jeden der folgenden untergeordneten Knoten des Knotens **SalesOrderDetails** auf das Dropdown Menü neben dem Knoten, und wählen Sie **keine**aus:

   - **SalesOrderID**

   - **SalesOrderDetailID**

   - **Rowguid**

   - **ModifiedDate**

     Durch diese Aktion wird verhindert, dass Visual Studio diese Daten in das <xref:System.Windows.Controls.DataGrid> Steuerelement einschließt, das Sie im nächsten Schritt erstellen. Bei dieser exemplarischen Vorgehensweise wird davon ausgegangen, dass der Endbenutzer diese Daten nicht sehen muss.

4. Ziehen Sie den untergeordneten Knoten **SalesOrderDetails** aus dem Fenster **Datenquellen** in das Fenster des **WPF-Designers**.

    Visual Studio generiert XAML, um ein neues Daten gebundenes <xref:System.Windows.Controls.DataGrid> Steuerelement zu definieren, und das Steuerelement wird im Designer angezeigt. Visual Studio aktualisiert auch die generierte `GetSalesOrderHeadersQuery`-Methode in der Code Behind-Datei, um die Daten in der **SalesOrderDetails** -Entität einzubeziehen.

## <a name="testing-the-application"></a>Testen der Anwendung
 Erstellen Sie die Anwendung, und führen Sie Sie aus.

#### <a name="to-test-the-application"></a>So testen Sie die Anwendung

1. Drücken Sie **F5**.

     Die Anwendung wird erstellt und ausgeführt. Überprüfen Sie Folgendes:

    - Im Kombinations Feld **Sales Order ID** wird **71774**angezeigt. Dies ist die erste Bestell-ID in der Entität.

    - Für jede von Ihnen im Kombinations Feld **Sales Order ID** ausgewählte Reihenfolge werden ausführliche Bestellinformationen in der <xref:System.Windows.Controls.DataGrid> angezeigt.

2. Schließen Sie die Anwendung.

## <a name="next-steps"></a>Nächste Schritte
 Nachdem Sie diese exemplarische Vorgehensweise abgeschlossen haben, erfahren Sie, wie Sie das **Datenquellen** Fenster in Visual Studio verwenden, um WPF-Steuerelemente an andere Arten von Datenquellen zu binden. Weitere Informationen finden Sie unter [Binden von WPF-Steuerelementen an einen WCF-Datendienst](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md) und [Binden von WPF-Steuerelementen an ein DataSet](../data-tools/bind-wpf-controls-to-a-dataset.md).

## <a name="see-also"></a>Siehe auch
 [Binden von WPF-Steuerelementen an Daten in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md) [Anzeigen verwandter Daten in WPF-Anwendungen](../data-tools/display-related-data-in-wpf-applications.md)