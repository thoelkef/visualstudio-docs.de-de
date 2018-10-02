---
title: 'Exemplarische Vorgehensweise: Erstellen eines TableAdapter mit mehreren Abfragen | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 2018-06-30
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
- TableAdapter queries, creating
- data [Visual Studio], TableAdapters
- TableAdapters, creating
- data [Visual Studio], walkthroughs
- queries [Visual Studio], TableAdapters
ms.assetid: f784dc4d-d514-4ade-8226-f8271c5b1ed8
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: e48750cf876f561b25802fd20b1e270215a1b605
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47515516"
---
# <a name="walkthrough-creating-a-tableadapter-with-multiple-queries"></a>Exemplarische Vorgehensweise: Erstellen eines TableAdapter mit mehreren Abfragen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In dieser exemplarischen Vorgehensweise erstellen Sie einen TableAdapter in ein Dataset mithilfe der [Assistenten zur Datenquellenkonfiguration](http://msdn.microsoft.com/library/c4df7de5-5da0-4064-940c-761dd6d9e28f). Die exemplarische Vorgehensweise führt Sie durch den Prozess der Erstellung einer zweiten Abfrage im der [TableAdapter](../data-tools/tableadapter-overview.md) mithilfe der [Bearbeiten von TableAdapters](../data-tools/editing-tableadapters.md) innerhalb der [Dataset-Designer](../data-tools/creating-and-editing-typed-datasets.md).  
  
 In dieser exemplarischen Vorgehensweise werden u. a. folgende Aufgaben veranschaulicht:  
  
-   Erstellen eines neuen **Windows-Anwendung** Projekt.  
  
-   Erstellen und konfigurieren Sie eine Datenquelle in Ihrer Anwendung durch die Erstellung eines Datasets mit dem **Assistenten zur Datenquellenkonfiguration**.  
  
-   Öffnen das neue Dataset in den **Dataset-Designer**.  
  
-   Hinzufügen von Abfragen zum TableAdapter mit dem **Konfigurations-Assistenten für TableAdapter-Abfragen**.  
  
## <a name="prerequisites"></a>Voraussetzungen  
 Für die Durchführung dieser exemplarischen Vorgehensweise benötigen Sie Folgendes:  
  
-   Zugriff auf die Beispieldatenbank Northwind (SQL Server- oder Access-Version). Weitere Informationen finden Sie unter [Vorgehensweise: Installieren von Beispieldatenbanken](../data-tools/how-to-install-sample-databases.md).  
  
## <a name="creating-a-new-windows-application"></a>Erstellen einer neuen Windows-Anwendung.  
 Im ersten Schritt wird eine Windows-Anwendung erstellt.  
  
#### <a name="to-create-a-new-windows-application-project"></a>So erstellen Sie ein neues Windows-Anwendungsprojekt  
  
1.  In [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], aus der **Datei** Menü ein neues Projekt erstellen.  
  
2.  Wählen Sie eine Programmiersprache, in der **Projekttypen** Bereich.  
  
3.  Klicken Sie auf **Windows-Anwendung** in die **Vorlagen** Bereich.  
  
4.  Nennen Sie das Projekt `TableAdapterQueriesWalkthrough`, und klicken Sie dann auf **OK**.  
  
     Visual Studio fügt das Projekt in **Projektmappen-Explorer** und ein neues Formular im Designer angezeigt.  
  
## <a name="creating-a-database-data-source-with-a-tableadapter"></a>Erstellen einer Datenbank-Datenquelle mit einem TableAdapter  
 Dieser Schritt wird erstellt, mit einer Datenquelle mithilfe der **Assistenten zur Datenquellenkonfiguration** basierend auf den `Customers` -Tabelle in der Beispieldatenbank Northwind. Sie benötigen Zugriff auf die Beispieldatenbank Northwind, um die Verbindung herstellen zu können. Informationen zum Einrichten der Beispieldatenbank Northwind finden Sie unter [Vorgehensweise: Installieren von Beispieldatenbanken](../data-tools/how-to-install-sample-databases.md).  
  
#### <a name="to-create-the-data-source"></a>So erstellen Sie die Datenquelle  
  
1.  Klicken Sie im Menü **Daten** auf **Datenquellen anzeigen**.  
  
2.  In der **Datenquellen** wählen Sie im Fenster **neue Datenquelle hinzufügen** zum Starten der **Assistenten zur Datenquellenkonfiguration**.  
  
3.  Wählen Sie auf der Seite **Datenquellentyp auswählen** die Option **Datenbank** aus, und klicken Sie auf **Weiter**.  
  
4.  Auf der **wählen Sie Ihre Datenverbindung** Seite führen Sie einen der folgenden:  
  
    -   Wenn in der Dropdownliste eine Datenverbindung zur Beispieldatenbank "Northwind" verfügbar ist, wählen Sie diese aus.  
  
         - oder -   
  
    -   Wählen Sie **neue Verbindung** zum Starten der **Verbindung hinzufügen/ändern** Dialogfeld.  
  
5.  Wenn Ihre Datenbank ein Kennwort erfordert, wählen Sie die Option Einbeziehung vertraulicher Daten, und klicken Sie dann auf **Weiter**.  
  
6.  Klicken Sie auf **Weiter** auf die **Verbindungszeichenfolge in der Programmkonfigurationsdatei speichern** Seite.  
  
7.  Erweitern Sie die **Tabellen** Knoten auf den **Datenbankobjekte auswählen** Seite.  
  
8.  Wählen Sie die **Kunden** Tabelle, und klicken Sie dann auf **Fertig stellen**.  
  
     Die **NorthwindDataSet** wird dem Projekt hinzugefügt und die **Kunden** Tabelle angezeigt wird, der **Datenquellen** Fenster.  
  
## <a name="opening-the-dataset-in-the-dataset-designer"></a>Öffnen des Datasets im Dataset-Designer  
  
#### <a name="to-open-the-dataset-in-the-dataset-designer"></a>So öffnen Sie das Dataset im Dataset-Designer.  
  
1.  Mit der rechten Maustaste **NorthwindDataset** in die **Datenquellen** Fenster.  
  
2.  Wählen Sie im Kontextmenü den Befehl **DataSet mit Designer bearbeiten**.  
  
     Das NorthwindDataset wird geöffnet, der **Dataset-Designer**.  
  
## <a name="adding-a-second-query-to-the-customerstableadapter"></a>Hinzufügen einer zweiten Abfrage zu CustomersTableAdapter  
 Der Assistent erstellt das Dataset mit einem **Kunden** Datentabelle und **CustomersTableAdapter**. In diesem Abschnitt der exemplarischen Vorgehensweise wird eine zweite Abfrage hinzugefügt. die **CustomersTableAdapter**.  
  
#### <a name="to-add-a-query-to-the-customerstableadapter"></a>So fügen Sie dem CustomersTableAdapter eine Abfrage hinzu  
  
1.  Ziehen Sie eine **Abfrage** aus der **DataSet** Registerkarte die **Toolbox** auf die **Kunden** Tabelle.  
  
     Die [Bearbeiten von TableAdapters](../data-tools/editing-tableadapters.md) wird geöffnet.  
  
2.  Wählen Sie **SQL-Anweisungen**, und klicken Sie dann auf **Weiter**.  
  
3.  Wählen Sie **wählen Sie die Zeilen zurückgibt**, und klicken Sie dann auf **Weiter**.  
  
4.  Fügen Sie der Abfrage eine WHERE-Klausel hinzu, sodass sie wie folgt aussieht:  
  
    ```  
    SELECT CustomerID, CompanyName, ContactName, ContactTitle, Address, City, Region, PostalCode, Country, Phone, Fax   
    FROM Customers   
    WHERE City = @City  
    ```  
  
    > [!NOTE]
    >  Wenn Sie die Access-Version von Northwind verwenden, ersetzen Sie die @City Parameter mit einem Fragezeichen. (`SELECT CustomerID, CompanyName, ContactName, ContactTitle, Address, City, Region, PostalCode, Country, Phone, Fax FROM Customers WHERE City = ?`)  
  
5.  Auf der **zu generierende** Namen der **DataTable füllen** Methode `FillByCity`.  
  
    > [!NOTE]
    >  Die Methode, die **DataTable zurückgeben** wird in dieser exemplarischen Vorgehensweise nicht verwendet, so können Sie das Kontrollkästchen deaktivieren, und übernehmen Sie den Standardnamen.  
  
6.  Klicken Sie auf **Weiter** und beenden Sie den Assistenten.  
  
     Die **FillByCity** Abfrage wird hinzugefügt, um die **CustomersTableAdapter**.  
  
## <a name="adding-code-to-execute-the-additional-query-on-the-form"></a>Hinzufügen von Code zum Ausführen der zusätzlichen Abfrage im Formular  
  
#### <a name="to-execute-the-query"></a>So führen Sie die Abfrage aus  
  
1.  Wählen Sie **Form1** in **Projektmappen-Explorer**, und klicken Sie auf **Ansicht-Designer**.  
  
2.  Ziehen Sie die **Kunden** Knoten aus der **Datenquellen** Fenster **Form1**.  
  
3.  Ändern Sie die Codeansicht dazu **Code** aus der **Ansicht** Menü.  
  
4.  Ersetzen Sie den Code im `Form1_Load`-Ereignishandler durch Folgendes, um die `FillByCity`-Abfrage auszuführen.  
  
     [!code-csharp[VbRaddataTableAdapters#1](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataTableAdapters/CS/Form1.cs#1)]
     [!code-vb[VbRaddataTableAdapters#1](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataTableAdapters/VB/Form1.vb#1)]  
  
## <a name="running-the-application"></a>Ausführen der Anwendung  
  
#### <a name="to-run-the-application"></a>So führen Sie die Anwendung aus  
  
-   Drücken Sie F5.  
  
-   Das Raster wird mit Kunden mit einem `City`-Wert von `Seattle` gefüllt.  
  
## <a name="next-steps"></a>Nächste Schritte  
  
### <a name="to-add-functionality-to-your-application"></a>So fügen Sie der Anwendung Funktionalität hinzu  
  
-   Fügen Sie ein <xref:System.Windows.Forms.TextBox>-Steuerelement und ein <xref:System.Windows.Forms.Button>-Steuerelement hinzu, und übergeben Sie den Wert im Textfeld an die Abfrage. (`CustomersTableAdapter.FillByCity(NorthwindDataSet.Customers, TextBox1.Text)`).  
  
-   Fügen Sie dem <xref:System.Data.DataTable.ColumnChanging>-Ereignis oder dem <xref:System.Data.DataTable.RowChanging>-Ereignis der Datentabellen im Dataset eine Validierungslogik hinzu. Weitere Informationen finden Sie unter [Überprüfen von Daten in Datasets](../data-tools/validate-data-in-datasets.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Übersicht über TableAdapters](../data-tools/tableadapter-overview.md)   
 [Erstellen und Konfigurieren eines TableAdapters](../data-tools/create-and-configure-tableadapters.md)   
 [Vorgehensweise: Erstellen von TableAdapter-Abfragen](../data-tools/how-to-create-tableadapter-queries.md)   
 [Exemplarische Vorgehensweisen für Daten](http://msdn.microsoft.com/library/15a88fb8-3bee-4962-914d-7a1f8bd40ec4)   
 [Herstellen einer Verbindung mit Daten in Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Vorbereiten der Anwendung zum Empfangen von Daten](http://msdn.microsoft.com/library/c17bdb7e-c234-4f2f-9582-5e55c27356ad)   
 [Abrufen von Daten für Ihre Anwendung](../data-tools/fetching-data-into-your-application.md)   
 [Binden von Steuerelementen an Daten in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Bearbeiten von Daten in der Anwendung](../data-tools/editing-data-in-your-application.md)