---
title: 'Exemplarische Vorgehensweise: Erstellen eines Datasets mit Dataset-Designer | Microsoft-Dokumentation'
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
- datasets [Visual Basic], walkthroughs
- XML schemas, creating datasets
- data [Visual Studio], Dataset Designer
- Dataset Designer, walkthroughs
- datasets [Visual Basic], creating
ms.assetid: 12360f54-db6c-45d2-a91f-fee43214b555
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 7c17a93a5d250ce620c37a2a0a89472bf760750b
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47513931"
---
# <a name="walkthrough-creating-a-dataset-with-the-dataset-designer"></a>Exemplarische Vorgehensweise: Erstellen eines Datasets mit dem DataSet-Designer
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In dieser exemplarischen Vorgehensweise erstellen Sie ein Dataset mithilfe der **Dataset-Designer**. Gelangen Sie durch den Prozess der Erstellung eines neuen Projekts und Hinzufügen eines neuen **DataSet** wird. Sie erfahren, wie Sie auf den Tabellen einer Datenbank basierende Tabellen erstellen können, ohne einen Assistenten zu verwenden.  
  
 In dieser exemplarischen Vorgehensweise werden u. a. folgende Aufgaben veranschaulicht:  
  
-   Erstellen eines neuen **Windows-Anwendung** Projekt.  
  
-   Hinzufügen eines leeren **DataSet** Elements zum Projekt.  
  
-   Erstellen und konfigurieren eine Datenquelle in Ihrer Anwendung, durch die Erstellung eines Datasets mit dem **Dataset-Designer**.  
  
-   Herstellen einer Verbindung mit der Datenbank Northwind in **Server-Explorer**.  
  
-   Erstellen von Tabellen mit TableAdapters im Dataset, auf der Grundlage von Tabellen der Datenbank  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
 Für die Durchführung dieser exemplarischen Vorgehensweise benötigen Sie Folgendes:  
  
-   Zugriff auf die Beispieldatenbank Northwind (SQL Server- oder Access-Version). Weitere Informationen finden Sie unter [Vorgehensweise: Installieren von Beispieldatenbanken](../data-tools/how-to-install-sample-databases.md).  
  
## <a name="creating-a-new-windows-application-project"></a>Erstellen eines neuen Windows-Anwendungsprojekts  
  
#### <a name="to-create-a-new-windows-application-project"></a>So erstellen Sie ein neues Windows-Anwendungsprojekt  
  
1.  Von der **Datei** Menü ein neues Projekt erstellen.  
  
2.  Wählen Sie eine Programmiersprache, in der **Projekttypen** Bereich.  
  
3.  Klicken Sie auf **Windows-Anwendung** in die **Vorlagen** Bereich.  
  
4.  Nennen Sie das Projekt `DatasetDesignerWalkthrough`, und klicken Sie dann auf **OK**.  
  
     [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Fügt das Projekt, um **Projektmappen-Explorer** und ein neues Formular im Designer anzuzeigen.  
  
## <a name="adding-a-new-dataset-to-the-application"></a>Hinzufügen eines neuen Datasets zur Anwendung  
  
#### <a name="to-add-a-new-dataset-item-to-the-project"></a>So fügen Sie dem Projekt ein neues Dataset-Element hinzu  
  
1.  Klicken Sie im Menü **Projekt** auf **Neues Element hinzufügen**.  
  
     Das Dialogfeld **Neues Element hinzufügen** wird angezeigt.  
  
2.  In der **Vorlagen** im Feld der **neues Element hinzufügen** Dialogfeld klicken Sie auf **DataSet**.  
  
3.  Nennen Sie das Dataset `NorthwindDataset`, und klicken Sie dann auf **hinzufügen**.  
  
     [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Fügt eine Datei namens **NorthwindDataset.xsd** auf das Projekt, und öffnen sie in der **Dataset-Designer**.  
  
## <a name="creating-a-data-connection-in-server-explorer"></a>Erstellen einer Datenverbindung im Server-Explorer  
  
#### <a name="to-create-a-connection-to-the-northwind-database"></a>So stellen Sie eine Verbindung mit der Datenbank Northwind her  
  
1.  Auf der **Ansicht** Menü klicken Sie auf **Server-Explorer**.  
  
2.  In **Server-Explorer**, klicken Sie auf die **Herstellen einer Verbindung mit Datenbank** Schaltfläche.  
  
3.  Erstellen Sie eine Verbindung mit der Beispieldatenbank Northwind.  
  
    > [!NOTE]
    >  Sie können in dieser exemplarischen Vorgehensweise eine Verbindung mit der SQL Server-Version oder der Access-Version von Northwind herstellen.  
  
## <a name="creating-the-tables-in-the-dataset"></a>Erstellen von Tabellen im Dataset  
 In diesem Abschnitt wird erklärt, wie dem Dataset Tabellen hinzugefügt werden.  
  
#### <a name="to-create-the-customers-table"></a>So erstellen Sie die Tabelle Customers  
  
1.  Erweitern Sie die Datenverbindung, die Sie erstellt, im haben **Server-Explorer**, und erweitern Sie dann die **Tabellen** Knoten.  
  
2.  Ziehen Sie die **Kunden** Tabelle **Server-Explorer** auf die **Dataset-Designer**.  
  
     Ein **Kunden** Datentabelle und **CustomersTableAdapter** zum Dataset hinzugefügt werden.  
  
#### <a name="to-create-the-orders-table"></a>So erstellen Sie die Tabelle Orders  
  
-   Ziehen Sie die **Bestellungen** Tabelle **Server-Explorer** auf die **Dataset-Designer**.  
  
     Ein **Bestellungen** Datentabelle **OrdersTableAdapter**, und eine datenbeziehung zwischen den **Kunden** und **Bestellungen** Tabellen hinzugefügt werden die das DataSet.  
  
#### <a name="to-create-the-orderdetails-table"></a>So erstellen Sie die Tabelle OrderDetails  
  
-   Ziehen Sie die **Bestelldetails** Tabelle **Server-Explorer** auf die **Dataset-Designer**.  
  
     Ein **Bestelldetails** Datentabelle **Order DetailsTableAdapter**, und eine datenbeziehung zwischen den **Bestellungen** und **Order Details** Tabellen dem Dataset hinzugefügt werden.  
  
## <a name="next-steps"></a>Nächste Schritte  
  
### <a name="to-add-functionality-to-your-application"></a>So fügen Sie der Anwendung Funktionalität hinzu  
  
-   Speichern Sie das DataSet.  
  
-   Wählen Sie Elemente in der **Datenquellen** Fenster, und ziehen Sie sie in einem Formular. Weitere Informationen finden Sie unter [Binden von Windows Forms-Steuerelementen an Daten in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md).  
  
-   Fügen Sie den TableAdapters weitere Abfragen hinzu. Weitere Informationen finden Sie unter [Vorgehensweise: Erstellen von TableAdapter-Abfragen](../data-tools/how-to-create-tableadapter-queries.md).  
  
-   Fügen Sie dem <xref:System.Data.DataTable.ColumnChanging>-Ereignis oder dem <xref:System.Data.DataTable.RowChanging>-Ereignis der im Dataset enthaltenen Datentabellen Anweisungen für eine Validierung hinzu. Weitere Informationen finden Sie unter [Überprüfen von Daten in Datasets](../data-tools/validate-data-in-datasets.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Exemplarische Vorgehensweisen für Daten](http://msdn.microsoft.com/library/15a88fb8-3bee-4962-914d-7a1f8bd40ec4)   
 [Binden von Windows Forms-Steuerelementen an Daten in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Herstellen einer Verbindung mit Daten in Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Vorbereiten der Anwendung zum Empfangen von Daten](http://msdn.microsoft.com/library/c17bdb7e-c234-4f2f-9582-5e55c27356ad)   
 [Abrufen von Daten für Ihre Anwendung](../data-tools/fetching-data-into-your-application.md)   
 [Binden von Steuerelementen an Daten in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Bearbeiten von Daten in Ihrer Anwendung](../data-tools/editing-data-in-your-application.md)   
 [Überprüfen von Daten](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)   
 [Speichern von Daten](../data-tools/saving-data.md)