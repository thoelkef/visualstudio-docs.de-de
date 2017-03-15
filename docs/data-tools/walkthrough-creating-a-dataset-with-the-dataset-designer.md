---
title: "Exemplarische Vorgehensweise: Erstellen eines Datasets mit dem DataSet-Designer | Microsoft Docs"
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
  - "Daten [Visual Studio], DataSet-Designer"
  - "DataSet-Designer, Exemplarische Vorgehensweisen"
  - "Datasets [Visual Basic], Erstellen"
  - "Datasets [Visual Basic], Exemplarische Vorgehensweisen"
  - "XML-Schemas, Erstellen von Datasets"
ms.assetid: 12360f54-db6c-45d2-a91f-fee43214b555
caps.latest.revision: 19
caps.handback.revision: 19
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
robots: noindex,nofollow
---
# Exemplarische Vorgehensweise: Erstellen eines Datasets mit dem DataSet-Designer
In dieser exemplarischen Vorgehensweise erstellen Sie mit dem **DataSet\-Designer** ein Dataset.  Es wird Schritt für Schritt erläutert, wie ein neues Projekt erstellt und diesem ein neues **Dataset** hinzugefügt wird.  Sie erfahren, wie Sie auf den Tabellen einer Datenbank basierende Tabellen erstellen können, ohne einen Assistenten zu verwenden.  
  
 Zu den Aufgaben in dieser exemplarischen Vorgehensweise gehören:  
  
-   Erstellen eines neuen **Windows\-Anwendung**\-Projekts  
  
-   Hinzufügen eines leeren **DataSet**\-Elements zum Projekt  
  
-   Erstellen und Konfigurieren einer Datenquelle in der Anwendung durch die Erstellung eines Datasets mit dem **DataSet\-Designer**  
  
-   Herstellen einer Verbindung mit der Datenbank Northwind im **Server\-Explorer**  
  
-   Erstellen von Tabellen mit TableAdapters im Dataset, auf der Grundlage von Tabellen der Datenbank  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
## Vorbereitungsmaßnahmen  
 Für die Durchführung dieser exemplarischen Vorgehensweise benötigen Sie Folgendes:  
  
-   Zugriff auf die Beispieldatenbank Northwind \(SQL Server\- oder Access\-Version\).  Weitere Informationen finden Sie unter [Gewusst wie: Installieren von Beispieldatenbanken](../data-tools/how-to-install-sample-databases.md).  
  
## Erstellen eines neuen Windows\-Anwendungsprojekts  
  
#### So erstellen Sie ein neues Windows\-Anwendungsprojekt  
  
1.  Erstellen Sie im Menü **Datei** ein neues Projekt.  
  
2.  Wählen Sie im Bereich **Projekttypen** eine Programmiersprache aus.  
  
3.  Klicken Sie im Bereich **Vorlagen** auf **Windows\-Anwendung**.  
  
4.  Nennen Sie das Projekt `DatasetDesignerWalkthrough`, und klicken Sie dann auf **OK**.  
  
     [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] fügt das Projekt dem **Projektmappen\-Explorer** hinzu und zeigt im Designer ein neues Formular an.  
  
## Hinzufügen eines neuen Datasets zur Anwendung  
  
#### So fügen Sie dem Projekt ein neues Dataset\-Element hinzu  
  
1.  Klicken Sie im Menü **Projekt** auf **Neues Element hinzufügen**.  
  
     Das Dialogfeld **Neues Element hinzufügen** wird angezeigt.  
  
2.  Klicken Sie im Feld **Vorlagen** des Dialogfelds **Neues Element hinzufügen** auf **DataSet**.  
  
3.  Nennen Sie das Dataset `NorthwindDataset`, und klicken Sie dann auf **Hinzufügen**.  
  
     [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] fügt dem Projekt eine Datei mit dem Namen **NorthwindDataset.xsd** hinzu und öffnet sie im **DataSet\-Designer**.  
  
## Erstellen einer Datenverbindung im Server\-Explorer  
  
#### So stellen Sie eine Verbindung mit der Datenbank Northwind her  
  
1.  Klicken Sie im Menü **Ansicht** auf **Server\-Explorer**.  
  
2.  Klicken Sie im **Server\-Explorer** auf die Schaltfläche **Mit Datenbank verbinden**.  
  
3.  Erstellen Sie eine Verbindung mit der Beispieldatenbank Northwind.  
  
    > [!NOTE]
    >  Sie können in dieser exemplarischen Vorgehensweise eine Verbindung mit der SQL Server\-Version oder der Access\-Version von Northwind herstellen.  
  
## Erstellen von Tabellen im Dataset  
 In diesem Abschnitt wird erklärt, wie dem Dataset Tabellen hinzugefügt werden.  
  
#### So erstellen Sie die Tabelle Customers  
  
1.  Erweitern Sie die Datenverbindung, die Sie im **Server\-Explorer** erstellt haben, und erweitern Sie dann den Knoten **Tabellen**.  
  
2.  Ziehen Sie die Tabelle **Customers** aus dem **Server\-Explorer** auf den **DataSet\-Designer**.  
  
     Dem Dataset werden die Datentabelle **Customers** und ein **CustomersTableAdapter** hinzugefügt.  
  
#### So erstellen Sie die Tabelle Orders  
  
-   Ziehen Sie die Tabelle **Orders** aus dem **Server\-Explorer** auf den **DataSet\-Designer**.  
  
     Dem Dataset werden die Datentabelle **Orders**, ein **OrdersTableAdapter** und eine Datenbeziehung zwischen den Tabellen **Customers** und **Orders** hinzugefügt.  
  
#### So erstellen Sie die Tabelle OrderDetails  
  
-   Ziehen Sie die Tabelle **Order Details** aus dem **Server\-Explorer** auf den **DataSet\-Designer**.  
  
     Dem Dataset werden die Datentabelle **Order Details**, ein **Order DetailsTableAdapter** und eine Datenbeziehung zwischen den Tabellen **Orders** und **Order Details** hinzugefügt.  
  
## Nächste Schritte  
  
### So fügen Sie der Anwendung Funktionen hinzu  
  
-   Speichern Sie das DataSet.  
  
-   Wählen Sie im **Datenquellenfenster** Elemente aus, und ziehen Sie sie auf ein Formular.  Weitere Informationen finden Sie unter [Binden von Windows Forms\-Steuerelementen an Daten in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md).  
  
-   Fügen Sie den TableAdapters weitere Abfragen hinzu.  Weitere Informationen finden Sie unter [Gewusst wie: Erstellen von TableAdapter\-Abfragen](../data-tools/how-to-create-tableadapter-queries.md).  
  
-   Fügen Sie dem <xref:System.Data.DataTable.ColumnChanging>\-Ereignis oder dem <xref:System.Data.DataTable.RowChanging>\-Ereignis der im Dataset enthaltenen Datentabellen Anweisungen für eine Validierung hinzu.  Weitere Informationen finden Sie unter [Überprüfen von Daten in Datasets](../data-tools/validate-data-in-datasets.md).  
  
## Siehe auch  
 [Exemplarische Vorgehensweisen zur Arbeit mit Daten](../Topic/Data%20Walkthroughs.md)   
 [Binden von Windows Forms\-Steuerelementen an Daten in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Herstellen von Datenverbindungen in Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Vorbereiten der Anwendung auf den Empfang von Daten](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [Abrufen von Daten für die Anwendung](../data-tools/fetching-data-into-your-application.md)   
 [Binden von Steuerelementen an Daten in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Bearbeiten von Daten in der Anwendung](../data-tools/editing-data-in-your-application.md)   
 [Überprüfen von Daten](../Topic/Validating%20Data.md)   
 [Speichern von Daten](../data-tools/saving-data.md)