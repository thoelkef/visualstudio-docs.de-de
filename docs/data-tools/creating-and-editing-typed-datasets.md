---
title: "Erstellen und Bearbeiten von typisierten Datasets | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "Designer_Microsoft.VSDesigner.DataSource.Designer.DataSourceRootDesigner"
  - "vs.data.adddataset"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
  - "aspx"
helpviewer_keywords: 
  - "Daten [Visual Studio], DataSet-Designer"
  - "DataSet-Designer"
  - "Datasets [Visual Basic], Visueller Designer"
ms.assetid: cd0dbe93-be9b-41e4-bc39-e9300678c1f2
caps.latest.revision: 26
caps.handback.revision: 26
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
robots: noindex,nofollow
---
# Erstellen und Bearbeiten von typisierten Datasets
Der **DataSet\-Designer** besteht aus mehreren visuellen Tools zum Erstellen und Bearbeiten typisierter Datasets und der einzelnen Elemente, die sie enthalten.  
  
 Der **Dataset\-Designer** stellt visuelle Darstellungen der Objekte bereit, die in typisierten Datasets enthalten sind.  Mit dem **Dataset\-Designer** erstellen und ändern Sie [TableAdapters](../data-tools/tableadapter-overview.md), [TableAdapter\-Abfragen](../data-tools/how-to-create-tableadapter-queries.md), <xref:System.Data.DataTable>s, <xref:System.Data.DataColumn>s und <xref:System.Data.DataRelation>s.  
  
 Um den **Dataset\-Designer** zu öffnen, doppelklicken Sie im **Projektmappen\-Explorer** auf ein Dataset, oder klicken Sie mit der rechten Maustaste im **Datenquellenfenster** auf ein Dataset, und klicken Sie auf **DataSet mit Designer bearbeiten**.  Weitere Informationen finden Sie unter [Gewusst wie: Öffnen eines Datasets im DataSet\-Designer](../Topic/How%20to:%20Open%20a%20Dataset%20in%20the%20Dataset%20Designer.md).  Durch das Hinzufügen eines neuen <xref:System.Data.DataSet>\-Elements mit dem Dialogfeld **Neues Element hinzufügen** wird der **Dataset\-Designer** mit einem leeren Dataset geöffnet, das gleich bearbeitet werden kann.  
  
> [!NOTE]
>  Im **Dataset\-Designer** können die Funktionen eines Datasets erweitert werden.  Doppelklicken Sie auf die Entwurfsoberfläche, oder klicken Sie mit der rechten Maustaste, und wählen Sie **Code anzeigen** aus, um eine Datei für die partielle Klasse zu erstellen, in der Sie dem Dataset Code hinzufügen können, der vom Designer nicht geändert oder gelöscht wird.  Informationen zum Erweitern der Funktionen eines TableAdapter finden Sie unter [Gewusst wie: Erweitern der Funktionalität eines TableAdapter](../data-tools/extend-the-functionality-of-a-tableadapter.md).  
  
 Die folgende Tabelle enthält häufig auftretende Aufgaben, die mit dem **Dataset\-Designer** ausgeführt werden können.  
  
|Zweck|Siehe|  
|-----------|-----------|  
|Erstellen eines TableAdapter|[Gewusst wie: Erstellen von TableAdapters](../data-tools/create-and-configure-tableadapters.md)|  
|Bearbeiten eines TableAdapters|[Gewusst wie: Bearbeiten von TableAdapters](../Topic/How%20to:%20Edit%20TableAdapters.md)|  
|Erstellen einer TableAdapter\-Abfrage|[Gewusst wie: Erstellen von TableAdapter\-Abfragen](../data-tools/how-to-create-tableadapter-queries.md)|  
|Bearbeiten einer TableAdapter\-Abfrage|[Gewusst wie: Bearbeiten von TableAdapter\-Abfragen](../data-tools/how-to-edit-tableadapter-queries.md)|  
|Erstellen einer <xref:System.Data.DataTable>|[Gewusst wie: Erstellen von Datentabellen](../data-tools/how-to-create-data-tables.md)|  
|Bearbeiten einer <xref:System.Data.DataTable>|[Entwerfen von DataTables](../data-tools/designing-datatables.md)|  
|Erstellen einer <xref:System.Data.DataColumn>|[Gewusst wie: Hinzufügen von Spalten zu einer DataTable](../Topic/How%20to:%20Add%20Columns%20to%20a%20DataTable.md)|  
|Erstellen einer Beziehung zwischen zwei <xref:System.Data.DataTable>s|[Gewusst wie: Erstellen von DataRelations mit dem Dataset\-Designer](../Topic/How%20to:%20Create%20DataRelations%20with%20the%20Dataset%20Designer.md)|  
|Erweitern der Datasetfunktionen|[Gewusst wie: Erweitern der Funktionen eines Datasets](../Topic/How%20to:%20Extend%20the%20Functionality%20of%20a%20Dataset.md)|  
|Hinzufügen einer Validierung zum <xref:System.Data.DataTable.ColumnChanging>\-Ereignis einer Datentabelle|[Gewusst wie: Validieren von Daten während Spaltenänderungen](../Topic/How%20to:%20Validate%20Data%20During%20Column%20Changes.md)|  
|Hinzufügen einer Validierung zum <xref:System.Data.DataTable.RowChanging>\-Ereignis einer Datentabelle|[Gewusst wie: Validieren von Daten während Zeilenänderungen](../Topic/How%20to:%20Validate%20Data%20During%20Row%20Changes.md)|  
  
## Erstellen von Objekten auf der Entwurfsoberfläche  
 Sie können Datasets erstellen, indem Sie die einzelnen Objekte hinzufügen und bearbeiten, die ein Dataset bilden.  Die folgende Tabelle enthält Erläuterungen zu den unterschiedlichen Objekten auf der Registerkarte **DataSet** der **Toolbox**, die auf die Entwurfsoberfläche gezogen werden können:  
  
|Objekt|Beschreibung|  
|------------|------------------|  
|TableAdapter|Enthält eine Auflistung von Datenbefehlen und eine Datenverbindung für die Kommunikation mit der zugrunde liegenden Datenbank und zum Auffüllen einer Datentabelle.  Weitere Informationen finden Sie unter [Übersicht über TableAdapters](../data-tools/tableadapter-overview.md) und [Gewusst wie: Erstellen von TableAdapters](../data-tools/create-and-configure-tableadapters.md).|  
|Abfrage|TableAdapter\-Abfragen sind Methoden mit starker Typisierung, die SQL\-Anweisungen und gespeicherte Prozeduren ausführen.  Durch die Ausführung einer TableAdapter\-Abfrage werden Datentabellen mit Daten aufgefüllt oder andere Datenbankaufgaben ausgeführt.  Weitere Informationen finden Sie unter [Gewusst wie: Erstellen von TableAdapter\-Abfragen](../data-tools/how-to-create-tableadapter-queries.md).  Durch Ziehen einer Abfrage auf eine Tabelle wird die Abfrage dieser Tabelle hinzugefügt, während das Ziehen einer Abfrage auf einen leeren Bereich des **Dataset\-Designers** zum Erstellen einer globalen Abfrage führt.  Weitere Informationen finden Sie unter [Gewusst wie: Hinzufügen von globalen Abfragen zu einem Dataset](../data-tools/how-to-add-global-queries-to-a-tableadapter.md).|  
|<xref:System.Data.DataTable>|Stellt eine Auflistung der Zeilen im Arbeitspeicher dar, die von einer Datenbank zurückgegeben wird.|  
|Beziehung \(<xref:System.Data.DataRelation>\)|Stellt die hierarchische Beziehung zwischen zwei <xref:System.Data.DataTable>s dar.  Weitere Informationen finden Sie unter [Einführung in DataRelation\-Objekte](../Topic/Introduction%20to%20DataRelation%20Objects.md) und [Exemplarische Vorgehensweise: Erstellen einer Beziehung zwischen Datentabellen](../Topic/Walkthrough:%20Creating%20a%20Relationship%20between%20Data%20Tables.md).|  
  
> [!NOTE]
>  Der **DataSet\-Designer** stellt eine Verbindung mit einer zugrunde liegenden Datenbank nur dann her, wenn ein Dataset erstellt wird. Der Designer erkennt nicht automatisch spätere Änderungen an der Datenbank.  Um eine vorhandene XSD\-Datei zu aktualisieren, führen Sie **Konfigurations\-Assistenten** erneut aus.  Wenn sich die Tabellenbeziehungen geändert haben, entfernen Sie die relevanten Tabellen in der XSD\-Datei und fügen sie wieder hinzu.  
  
## LINQ to DataSet  
 [!INCLUDE[linq_dataset](../data-tools/includes/linq_dataset_md.md)] ermöglicht [LINQ \(Language\-Integrated Query\)](../Topic/LINQ%20\(Language-Integrated%20Query\).md) für Daten in einem <xref:System.Data.DataSet>\-Objekt.  Weitere Informationen finden Sie unter [LINQ to DataSet](../Topic/LINQ%20to%20DataSet.md).  
  
## Siehe auch  
 [Exemplarische Vorgehensweise: Erstellen eines Datasets mit dem DataSet\-Designer](../data-tools/walkthrough-creating-a-dataset-with-the-dataset-designer.md)   
 [Exemplarische Vorgehensweise: Erstellen eines TableAdapter mit mehreren Abfragen](../data-tools/walkthrough-creating-a-tableadapter-with-multiple-queries.md)   
 [Exemplarische Vorgehensweise: Erstellen einer DataTable im Dataset\-Designer](../data-tools/walkthrough-creating-a-datatable-in-the-dataset-designer.md)   
 [Exemplarische Vorgehensweise: Erstellen einer Beziehung zwischen Datentabellen](../Topic/Walkthrough:%20Creating%20a%20Relationship%20between%20Data%20Tables.md)   
 [Exemplarische Vorgehensweise: Anzeigen von Daten in einem Windows Form](../data-tools/walkthrough-displaying-data-on-a-windows-form.md)   
 [Datenquellenfenster](../Topic/Data%20Sources%20Window.md)   
 [Arbeiten mit Datasets in Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)   
 [Vorbereiten der Anwendung auf den Empfang von Daten](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [Abrufen von Daten für die Anwendung](../data-tools/fetching-data-into-your-application.md)   
 [Bearbeiten von Daten in der Anwendung](../data-tools/editing-data-in-your-application.md)   
 [Überprüfen von Daten](../Topic/Validating%20Data.md)   
 [Speichern von Daten](../data-tools/saving-data.md)