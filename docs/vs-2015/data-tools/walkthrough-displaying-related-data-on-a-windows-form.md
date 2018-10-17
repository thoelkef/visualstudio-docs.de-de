---
title: 'Exemplarische Vorgehensweise: Anzeigen verknüpfter Daten in einem Windows Form | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- displaying data on forms, walkthroughs
- Windows Forms, displaying data
- data [Visual Studio], displaying on Windows Forms
- master-details lists, displaying on Windows Forms
- data [Visual Studio], master-details
- displaying tables, related data
- displaying table data
- displaying table information
ms.assetid: fc4b9055-2bf3-4028-8aad-9489820d69f6
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 882c8229c105920efe247a54e9525a262e6a3246
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49282671"
---
# <a name="walkthrough-displaying-related-data-on-a-windows-form"></a>Exemplarische Vorgehensweise: Anzeigen verknüpfter Daten in einem Windows Form
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In vielen Anwendungsszenarios ist die Verwendung von Daten aus mehreren Tabellen und häufig von Daten aus verknüpften Tabellen erforderlich. Das bedeutet, dass Sie mit einer Beziehung zwischen übergeordneten und untergeordneten Elementen arbeiten müssen. Sie möchten z. B. ein Formular erstellen, in dem bei der Auswahl eines Kundendatensatzes die Aufträge dieses Kunden angezeigt werden. Die verknüpften Datensätze im Formular können angezeigt werden, indem die <xref:System.Windows.Forms.BindingSource.DataSource%2A>-Eigenschaft der untergeordneten<xref:System.Windows.Forms.BindingSource> auf die übergeordnete <xref:System.Windows.Forms.BindingSource> (nicht auf die untergeordnete Tabelle) festgelegt wird und indem die <xref:System.Windows.Forms.BindingSource.DataMember%2A>-Eigenschaft der untergeordneten <xref:System.Windows.Forms.BindingSource> auf die Datenbeziehung festgelegt wird, die die über- und untergeordneten Tabellen miteinander verknüpft.  
  
 In dieser exemplarischen Vorgehensweise werden u. a. folgende Aufgaben veranschaulicht:  
  
-   Erstellen einer **Windows-Anwendung** Projekt.  
  
-   Erstellen und Konfigurieren eines Datasets in Ihrer Anwendung basierend auf den `Customers` und `Orders` Tabellen in der Datenbank Northwind mithilfe der [Assistenten zur Datenquellenkonfiguration](http://msdn.microsoft.com/library/c4df7de5-5da0-4064-940c-761dd6d9e28f).  
  
-   Hinzufügen von Steuerelementen zum Anzeigen von Daten aus der `Customers`-Tabelle.  
  
-   Hinzufügen von Steuerelementen zum Anzeigen von `Orders` auf der Grundlage des ausgewählten `Customer`.  
  
-   Testen der Anwendung durch Auswählen verschiedener Kunden und Überprüfen der Anzeige der richtigen Aufträge für den ausgewählten Kunden.  
  
## <a name="prerequisites"></a>Vorraussetzungen  
 Für die Durchführung dieser exemplarischen Vorgehensweise benötigen Sie Folgendes:  
  
-   Zugriff auf die Beispieldatenbank Northwind. Zum Installieren von Beispieldatenbanken finden Sie unter [Vorgehensweise: Installieren von Beispieldatenbanken](../data-tools/how-to-install-sample-databases.md).  
  
## <a name="creating-the-project"></a>Erstellen des Projekts  
 Der erste Schritt ist die Erstellung einer **Windows-Anwendung**.  
  
#### <a name="to-create-the-windows-application-project"></a>So erstellen Sie ein Projekt vom Typ Windows-Anwendung  
  
1.  Von der **Datei** Menü ein neues Projekt erstellen.  
  
2.  Benennen Sie das Projekt mit `RelatedDataWalkthrough`.  
  
3.  Wählen Sie **Windows-Anwendung** , und klicken Sie auf **OK**. Weitere Informationen finden Sie unter [Clientanwendungen](http://msdn.microsoft.com/library/2dfb50b7-5af2-4e12-9bbb-c5ade0e39a68).  
  
     Die **RelatedDataWalkthrough** Projekt wird erstellt und hinzugefügt **Projektmappen-Explorer**.  
  
## <a name="creating-the-data-source"></a>Erstellen der Datenquelle  
 In diesem Schritt wird auf der Grundlage der in der Beispieldatenbank Northwind enthaltenen `Customers`-Tabelle und der `Orders`-Tabelle ein Dataset erstellt.  
  
#### <a name="to-create-the-data-source"></a>So erstellen Sie die Datenquelle  
  
1.  Klicken Sie im Menü **Daten** auf **Datenquellen anzeigen**.  
  
2.  In der **Datenquellen** wählen Sie im Fenster **neue Datenquelle hinzufügen** zum Starten der **Assistenten zur Datenquellenkonfiguration**.  
  
3.  Wählen Sie auf der Seite **Datenquellentyp auswählen** die Option **Datenbank** aus, und klicken Sie auf **Weiter**.  
  
4.  Auf der **wählen Sie Ihre Datenverbindung** Seite führen Sie einen der folgenden:  
  
    -   Wenn in der Dropdownliste eine Datenverbindung zur Beispieldatenbank „Northwind“ verfügbar ist, wählen Sie diese aus.  
  
         - oder -   
  
    -   Wählen Sie **neue Verbindung** zum Starten der **Verbindung hinzufügen/ändern** Dialogfeld.  
  
5.  Wenn Ihre Datenbank ein Kennwort erfordert, wählen Sie die Option Einbeziehung vertraulicher Daten, und klicken Sie dann auf **Weiter**.  
  
6.  Klicken Sie auf **Weiter** auf die **Verbindungszeichenfolge in der Programmkonfigurationsdatei speichern** Seite.  
  
7.  Erweitern Sie die **Tabellen** Knoten auf den **Datenbankobjekte auswählen** Seite.  
  
8.  Wählen Sie die **Kunden** und **Bestellungen** Tabellen, und klicken Sie dann auf **Fertig stellen**.  
  
     Die **NorthwindDataSet** wird dem Projekt hinzugefügt und die **Kunden** Tabelle angezeigt wird, der **Datenquellen** Fenster.  
  
## <a name="creating-controls-to-display-data-from-the-customers-table"></a>Erstellen von Steuerelementen zum Anzeigen von Daten aus der Customers-Tabelle  
  
#### <a name="to-create-controls-to-display-the-customer-data-parent-records"></a>So erstellen Sie Steuerelemente zum Anzeigen der Kundendaten (übergeordnete Datensätze)  
  
1.  In der **Datenquellen** wählen Sie im Fenster der **Kunden** Tabelle, und klicken Sie dann auf den Dropdown-Pfeil.  
  
2.  Wählen Sie **Details** aus dem Menü.  
  
3.  Ziehen Sie den Hauptknoten **Kunden** Knoten aus der **Datenquellen** in den oberen Bereich des **Form1**.  
  
     Auf dem Formular werden datengebundene Steuerelemente mit beschreibenden Bezeichnungen sowie ein Toolstrip (<xref:System.Windows.Forms.BindingNavigator>) für die Navigation in den Datensätzen angezeigt. Ein [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), [CustomersTableAdapter](../data-tools/tableadapter-overview.md), <xref:System.Windows.Forms.BindingSource>, und <xref:System.Windows.Forms.BindingNavigator> werden in der Komponentenleiste angezeigt.  
  
## <a name="creating-controls-to-display-data-from-the-orders-table"></a>Erstellen von Steuerelementen zum Anzeigen von Daten aus der Orders-Tabelle  
 ![Datenquellen-Fenster mit der Beziehung](../data-tools/media/datasources2.gif "DataSources2")  
  
#### <a name="to-create-controls-to-display-the-orders-for-each-customer-child-records"></a>So erstellen Sie Steuerelemente zum Anzeigen der Aufträge der einzelnen Kunden (untergeordnete Datensätze)  
  
-   In der **Datenquellen** Fenster, erweitern Sie die **Kunden** Knoten, und wählen Sie die letzte Spalte in der **Kunden** Tabelle, die einem erweiterbaren **Bestellungen** Knoten, und ziehen Sie es in den unteren Rand **Form1**.  
  
     Dem Formular wird eine <xref:System.Windows.Forms.DataGridView> hinzugefügt, und der Komponentenleiste werden eine neue <xref:System.Windows.Forms.BindingSource> (`OrdersBindingSource`) und ein neuer TableAdapter (`OrdersTableAdapter`) hinzugefügt.  
  
    > [!NOTE]
    >  Öffnen der [Fenster "Eigenschaften"](../ide/reference/properties-window.md) , und wählen Sie die **OrdersBindingSource**. Überprüfen Sie die <xref:System.Windows.Forms.BindingSource.DataSource%2A>-Eigenschaft und <xref:System.Windows.Forms.BindingSource.DataMember%2A>-Eigenschaft, um festzustellen, wie die Bindung konfiguriert wird, um verknüpfte Datensätze anzuzeigen. <xref:System.Windows.Forms.BindingSource.DataSource%2A> wird auf `CustomersBindingSource` (<xref:System.Windows.Forms.BindingSource> der übergeordneten Tabelle) anstatt auf die `Orders`-Tabelle festgelegt. Die <xref:System.Windows.Forms.BindingSource.DataMember%2A>-Eigenschaft ist auf `FK_Orders_Customers` festgelegt. Hierbei handelt es sich um den Namen des <xref:System.Data.DataRelation>-Objekts, durch das die Tabellen miteinander verknüpft sind.  
  
## <a name="testing-the-application"></a>Testen der Anwendung  
  
#### <a name="to-test-the-application"></a>So testen Sie die Anwendung  
  
1.  Drücken Sie F5, um die Anwendung auszuführen.  
  
2.  Wählen Sie verschiedene Kunden, die mit der **CustomersBindingNavigator** So überprüfen die richtigen Aufträge angezeigt werden, der <xref:System.Windows.Forms.DataGridView>.  
  
## <a name="next-steps"></a>Nächste Schritte  
 Entsprechend den Anforderungen an Ihre Anwendung können Sie nach der Erstellung eines Master-Detail-Formulars noch weitere Schritte ausführen. Sie können an dieser exemplarischen Vorgehensweise beispielsweise folgende Verbesserung vornehmen:  
  
-   Filtern der `Customers`-Datensätze, indem der `Customers`-Tabelle Parametrisierung hinzugefügt wird. Zu diesem Zweck wählen Sie jedes Steuerelement, das Daten aus der `Customers` Tabelle, klicken Sie auf das Smarttag, und wählen **Abfrage hinzufügen**. Abschließen der [suchen Sie im Dialogfeld "Generator" Kriterien](http://msdn.microsoft.com/library/0b306b92-f35e-45ef-a4be-3f653cd00c3d). Weitere Informationen finden Sie unter [Vorgehensweise: Hinzufügen einer parametrisierten Abfrage auf einer Windows Forms-Anwendung](http://msdn.microsoft.com/library/13db4ad3-56b9-4a0b-b3a5-6a4ff84d4416).  
  
## <a name="see-also"></a>Siehe auch  
 [Exemplarische Vorgehensweisen für Daten](http://msdn.microsoft.com/library/15a88fb8-3bee-4962-914d-7a1f8bd40ec4)   
 [Datenquellenfenster](http://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992)   
 [Binden von Windows Forms-Steuerelementen an Daten in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Neue Datenquelle hinzufügen](../data-tools/add-new-data-sources.md)   
 [Übersicht über TableAdapters](../data-tools/tableadapter-overview.md)   
 [Vorgehensweise: Anzeigen von verknüpften Daten in einer Windows Forms-Anwendung](../data-tools/how-to-display-related-data-in-a-windows-forms-application.md)   
 [Übersicht über die BindingSource-Komponente](http://msdn.microsoft.com/library/be838caf-fcb0-4b68-827f-58b2c04b747f)   
 [Übersicht über das BindingNavigator-Steuerelement](http://msdn.microsoft.com/library/4423eede-f8d1-4d02-822f-5bf8432680d0)