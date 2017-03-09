---
title: "Exemplarische Vorgehensweise: Herstellen einer Verbindung mit Daten in einer lokalen Datenbankdatei (Windows Forms) | Microsoft Docs"
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
  - "Daten [Visual Studio], Verbinden mit SQL Express"
  - "Daten [Visual Studio], Lokal"
  - "Datenbanken, Verbinden mit"
  - "Lokale Daten, SQL Express"
  - "SQL Express, Verbindung herstellen"
  - "SQL Express, Exemplarische Vorgehensweisen"
ms.assetid: 5e16b7da-3fdc-4e69-bdb4-e8e700481811
caps.latest.revision: 35
caps.handback.revision: 35
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
robots: noindex,nofollow
---
# Exemplarische Vorgehensweise: Herstellen einer Verbindung mit Daten in einer lokalen Datenbankdatei (Windows Forms)
Sie können Daten aus einer lokalen Datenbankdatei in der Anwendung schnell und problemlos anzeigen, indem Sie ein DataSet erstellen und der Anwendung datengebundene Steuerelemente hinzufügen.  Im Verlauf dieser exemplarischen Vorgehensweise zeigen Sie Daten aus der lokalen Datenbankdatei an, die Sie durch Ausführung der Schritte unter [Exemplarische Vorgehensweise: Erstellen einer lokalen Datenbankdatei in Visual Studio](../data-tools/create-a-sql-database-by-using-a-designer.md) erstellt haben.  Nachdem Sie ein Windows Forms\-Projekt erstellt haben, stellen Sie eine Verbindung mit dieser Datenbank her, und legen fest, dass Sie Daten aus der Tabelle "Customers" in einem Datenraster auf dem Formular für die Anwendung angezeigt werden sollen.  
  
 Wenn Sie eine Datenbank in Visual Studio 2013 erstellen, wird das SQL Server Express LocalDB\-Modul verwendet, um auf eine Datenbankdatei \(MDF\) in SQL Server 2012 zuzugreifen.  In früheren Versionen von Visual Studio wird das SQL Server Express\-Modul verwendet, um auf eine Datenbankdatei \(MDF\) zuzugreifen.  [Übersicht über lokale Daten](../data-tools/local-data-overview.md)  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
 Diese exemplarische Vorgehensweise umfasst die folgenden Aufgaben:  
  
-   [Erstellen und Konfigurieren eines DataSets](../data-tools/walkthrough-connecting-to-data-in-a-local-database-file-windows-forms.md#BKMK_CreateDataset)  
  
-   [Hinzufügen datengebundener Steuerelemente](../data-tools/walkthrough-connecting-to-data-in-a-local-database-file-windows-forms.md#BKMK_AddCtrls)  
  
## Vorbereitungsmaßnahmen  
 Um diese exemplarische Vorgehensweise auszuführen, benötigen Sie Zugriff auf die Datenbank "SampleDatabase.mdf", die Sie mit den unter [Exemplarische Vorgehensweise: Erstellen einer lokalen Datenbankdatei in Visual Studio](../data-tools/create-a-sql-database-by-using-a-designer.md) beschriebenen Schritten erstellen.  
  
##  <a name="BKMK_CreateDataset"></a> Erstellen und Konfigurieren eines DataSets  
  
#### So erstellen und konfigurieren Sie ein Dataset  
  
1.  Erstellen Sie Windows Forms\-Projekt, und benennen Sie es "ConnectLocalData".  
  
     [Clientanwendungen](../Topic/Developing%20Client%20Applications%20with%20the%20.NET%20Framework.md)  
  
2.  Wenn das Fenster **Datenquellen** nicht angezeigt wird, drücken Sie die Tasten UMSCHALT\+ALT\+D, oder wählen Sie in der Menüleiste die Optionen **Ansicht**, **Weitere Fenster**, **Datenquellen anzeigen** aus.  
  
3.  Wählen Sie im Fenster **Datenquellen** den Link **Neue Datenquelle hinzufügen** aus.  
  
     Klicken Sie im Dialogfeld **Assistent zum Konfigurieren von Datenquellen** zweimal auf die Schaltfläche **Weiter**, um die Standardeinstellungen zu übernehmen.  
  
4.  Klicken Sie auf der Seite **Wählen Sie Ihre Datenverbindung aus** auf die Schaltfläche **Neue Verbindung**.  
  
     Das Dialogfeld **Datenquelle auswählen** wird angezeigt.  
  
5.  Wählen Sie in der Liste **Datenquelle** den Eintrag **Microsoft SQL Server\-Datenbankdatei** aus, und klicken Sie dann auf die Schaltfläche **Weiter**.  
  
     Das Dialogfeld **Verbindung hinzufügen** wird angezeigt.  
  
6.  Geben Sie im Feld **Name der Datenbankdatei** die Datei an, die Sie mit den unter [Exemplarische Vorgehensweise: Erstellen einer lokalen Datenbankdatei in Visual Studio](../data-tools/create-a-sql-database-by-using-a-designer.md) aufgeführten Schritte erstellt haben, oder klicken Sie auf die Schaltfläche **Durchsuchen**, und wechseln Sie dann zu der Datei.  
  
     Standardmäßig befindet sich die Datei unter "Benutzer\\*Ihr Konto*\\Dokumente\\Visual Studio *Version*\\Projects\\SampleDatabaseWalkthrough\\SampleDatabaseWalkthrough".  
  
7.  Übernehmen Sie unter **Beim Server anmelden** die Standardwerte, wählen Sie die Schaltfläche **OK**, und wählen Sie dann die Schaltfläche **Weiter** aus.  
  
    > [!NOTE]
    >  Beim Herstellen einer Verbindung mit einer lokalen Datenbankdatei können Sie entweder eine Kopie der Datenbank in Ihrem Projekt erstellen oder eine Verbindung mit der vorhandenen Datenbankdatei an ihrem aktuellen Speicherort herstellen.  [Gewusst wie: Verwalten von lokalen Datendateien im Projekt](../data-tools/how-to-manage-local-data-files-in-your-project.md)  
  
8.  Im angezeigten Dialogfeld klicken Sie auf **Ja**, um die Datenbankdatei in das Projekt zu kopieren.  
  
9. Klicken Sie auf der Seite **Verbindungszeichenfolge in der Anwendungskonfigurationsdatei speichern** auf die Schaltfläche **Weiter**.  
  
10. Erweitern Sie auf der Seite **Datenbankobjekte auswählen** den Knoten **Tabellen**, aktivieren Sie die Kontrollkästchen **Customers** und **Orders**, und klicken Sie dann auf die Schaltfläche **Fertig stellen**.  
  
     **SampleDatabaseDataSet** wird dem Projekt hinzugefügt, und die Tabellen **Customers** und **Orders** werden im Fenster **Datenquellen** angezeigt.  
  
##  <a name="BKMK_AddCtrls"></a> Hinzufügen datengebundener Steuerelemente  
  
#### So fügen Sie datengebundene Steuerelemente hinzu  
  
1.  Verschieben Sie den Hauptknoten **Customers** aus dem Fenster **Datenquellen** auf **Form1**.  
  
     Auf dem Formular werden <xref:System.Windows.Forms.DataGridView> und ein ToolStrip\-Element \(<xref:System.Windows.Forms.BindingNavigator>\) angezeigt, mit denen Sie durch die Datensätze auf dem Formular navigieren können.  Ein [SampleDatabaseDataSet](../data-tools/dataset-tools-in-visual-studio.md), ein [CustomersTableAdapter](../data-tools/tableadapter-overview.md), eine <xref:System.Windows.Forms.BindingSource> und ein <xref:System.Windows.Forms.BindingNavigator> werden auf der Komponentenleiste angezeigt.  
  
2.  Um die Anwendung auszuführen und die Daten anzuzeigen, die Sie in der vorherigen exemplarischen Vorgehensweise hinzugefügt haben, drücken Sie die Taste F5.  
  
3.  Wählen Sie das gelbe Symbol zum Hinzufügen aus \(![Schaltfläche "Hinzufügen" in Windows Form](../data-tools/media/addrecord.png "AddRecord")\), fügen Sie einen Kundendatensatz hinzu, und speichern Sie anschließend die Änderungen, indem Sie auf das Datenträgersymbol \(![Schaltfläche "Speichern" in Windows Form](../data-tools/media/saveinwf.png "SaveInWF")\) klicken.  
  
4.  Löschen Sie den Datensatz, den Sie gerade erstellt haben, indem Sie ihn auswählen und dann auf das rote Symbol zum Löschen klicken \(![Schaltfläche "Löschen" in Windows Form](../data-tools/media/deleterecord.png "DeleteRecord")\).  
  
## Nächste Schritte  
 Sie können Objekte im Dataset erstellen oder ändern, wenn Sie die Datenquelle im  [Erstellen und Bearbeiten von typisierten Datasets](../data-tools/creating-and-editing-typed-datasets.md) öffnen.  Sie können dem Ereignis <xref:System.Data.DataTable.ColumnChanging> oder <xref:System.Data.DataTable.RowChanging> der Datentabellen im DataSet auch eine Validierungslogik hinzufügen.  [Überprüfen von Daten in Datasets](../data-tools/validate-data-in-datasets.md).  
  
## Siehe auch  
 [Übersicht über lokale Daten](../data-tools/local-data-overview.md)   
 [Gewusst wie: Verwalten von lokalen Datendateien im Projekt](../data-tools/how-to-manage-local-data-files-in-your-project.md)   
 [Binden von Windows Forms\-Steuerelementen an Daten in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Herstellen von Datenverbindungen in Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Vorbereiten der Anwendung auf den Empfang von Daten](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [Abrufen von Daten für die Anwendung](../data-tools/fetching-data-into-your-application.md)   
 [Binden von Steuerelementen an Daten in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Bearbeiten von Daten in der Anwendung](../data-tools/editing-data-in-your-application.md)   
 [Überprüfen von Daten](../Topic/Validating%20Data.md)   
 [Speichern von Daten](../data-tools/saving-data.md)