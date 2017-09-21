---
title: "Exemplarische Vorgehensweise: Erstellen einer DataTable im Dataset-Designer | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
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
  - "DataSet-Designer, Erstellen von Datentabellen"
  - "DataTable-Objekte, Erstellen"
  - "Tabellen [Visual Studio], Erstellen"
ms.assetid: abf0a2b5-e4e5-422e-97ef-55a0e35a82df
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
robots: noindex,nofollow
---
# Exemplarische Vorgehensweise: Erstellen einer DataTable im Dataset-Designer
In dieser exemplarischen Vorgehensweise wird erklärt, wie <xref:System.Data.DataTable> \(ohne einen TableAdapter\) mit dem **Dataset\-Designer** erstellt wird.  Informationen über die Erstellung von Datentabellen, die TableAdapters enthalten, finden Sie unter [Gewusst wie: Erstellen von TableAdapters](../data-tools/create-and-configure-tableadapters.md).  
  
 In dieser exemplarischen Vorgehensweise werden u. a. folgende Aufgaben veranschaulicht:  
  
-   Erstellen eines neuen Windows\-Anwendungsprojekts.  
  
-   Hinzufügen eines neuen Datasets zur Anwendung  
  
-   Hinzufügen einer neuen Datentabelle zum Dataset  
  
-   Hinzufügen von Spalten zur Datentabelle  
  
-   Festlegen des Primärschlüssels für die Tabelle  
  
## Erstellen einer neuen Windows\-Anwendung.  
  
#### So erstellen Sie ein neues Windows\-Anwendungsprojekt  
  
1.  Erstellen Sie über das Menü **Datei** ein neues Projekt.  
  
2.  Wählen Sie im Bereich **Projekttypen** eine Programmiersprache aus.  
  
3.  Klicken Sie im Bereich **Vorlagen** auf **Windows\-Anwendung**.  
  
4.  Nennen Sie das Projekt `DataTableWalkthrough`, und klicken Sie anschließend auf **OK**.  
  
     Visual Studio fügt das Projekt dem **Projektmappen\-Explorer** hinzu und zeigt im Designer **Form1** an.  
  
## Hinzufügen eines neuen Datasets zur Anwendung  
  
#### So fügen Sie dem Projekt ein neues Dataset\-Element hinzu  
  
1.  Klicken Sie im Menü **Projekt** auf **Neues Element hinzufügen**.  
  
     Das Dialogfeld "Neues Element hinzufügen" wird angezeigt.  
  
2.  Wählen Sie im Feld **Vorlagen** die Option **DataSet** aus.  
  
3.  Klicken Sie auf **Hinzufügen**.  
  
     Visual Studio fügt dem Projekt eine Datei mit dem Namen **DataSet1.xsd** hinzu und öffnet sie im **Dataset\-Designer**.  
  
## Hinzufügen einer neuen DataTable zum Dataset  
  
#### So fügen Sie dem Dataset eine neue Datentabelle hinzu  
  
1.  Ziehen Sie von der Registerkarte **DataSet** der **Toolbox** eine **DataTable** auf den **Dataset\-Designer**.  
  
     Dem Dataset wird eine Tabelle mit dem Namen **DataTable1** hinzugefügt.  
  
    > [!NOTE]
    >  Informationen zum Erstellen einer Datentabelle, die einen TableAdapter enthält, finden Sie unter [Exemplarische Vorgehensweise: Erstellen eines TableAdapter mit mehreren Abfragen](../data-tools/walkthrough-creating-a-tableadapter-with-multiple-queries.md).  
  
2.  Klicken Sie auf die Titelleiste der **DataTable1**, und geben Sie ihr den neuen Namen `Music`.  
  
## Hinzufügen von Spalten zur Datentabelle  
  
#### So fügen Sie der Datentabelle Spalten hinzu  
  
1.  Klicken Sie mit der rechten Maustaste auf die Tabelle **Music**.  Zeigen Sie auf **Hinzufügen**, und klicken Sie dann auf **Spalte**.  
  
2.  Nennen Sie die Spalte `SongID`.  
  
3.  Legen Sie im **Eigenschaftenfenster** die <xref:System.Data.DataColumn.DataType%2A>\-Eigenschaft auf <xref:System.Int16?displayProperty=fullName> fest.  
  
4.  Wiederholen Sie diesen Prozess, und fügen Sie die folgenden Spalten hinzu:  
  
     `SongTitle`: <xref:System.String?displayProperty=fullName>  
  
     `Artist`: <xref:System.String?displayProperty=fullName>  
  
     `Genre`: <xref:System.String?displayProperty=fullName>  
  
## Festlegen des Primärschlüssels für die Tabelle  
 Alle Datentabellen sollten über einen Primärschlüssel verfügen.  Ein Primärschlüssel identifiziert eindeutig einen bestimmten Datensatz in einer Datentabelle.  
  
#### So legen Sie den Primärschlüssel der Datentabelle fest  
  
-   Klicken Sie mit der rechten Maustaste auf die Spalte **SongID**, und klicken Sie dann auf **Primärschlüssel festlegen**.  
  
     Ein Schlüsselsymbol wird neben der Spalte **SongID** angezeigt.  
  
## Speichern des Projekts  
  
#### So speichern Sie das DataTableWalkthrough\-Projekt  
  
-   Klicken Sie im Menü **Datei** auf **Alle speichern**.  
  
## Nächste Schritte  
 Nachdem Sie die Tabelle erstellt haben, können Sie die folgenden Aktionen ausführen:  
  
|To|Siehe|  
|--------|-----------|  
|Erstellen eines Formulars für die Eingabe von Daten|[Exemplarische Vorgehensweise: Anzeigen von Daten in einem Windows Form](../data-tools/walkthrough-displaying-data-on-a-windows-form.md).|  
|Hinzufügen von Daten zur Tabelle|[Hinzufügen von Daten zu einer 'DataTable'](../Topic/Adding%20Data%20to%20a%20DataTable.md).|  
|Anzeigen von Daten in einer Tabelle|[Anzeigen von Daten in einer 'DataTable'](../Topic/Viewing%20Data%20in%20a%20DataTable.md).|  
|Bearbeiten von Daten|['Edit'\-Methoden für eine 'DataTable'](../Topic/DataTable%20Edits.md)|  
|Löschen einer Zeile aus einer Tabelle|[DataRow\-Löschung](../Topic/DataRow%20Deletion.md)|  
  
## Siehe auch  
 [Herstellen von Datenverbindungen in Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Vorbereiten der Anwendung auf den Empfang von Daten](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [Abrufen von Daten für die Anwendung](../data-tools/fetching-data-into-your-application.md)   
 [Binden von Steuerelementen an Daten in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Bearbeiten von Daten in der Anwendung](../data-tools/editing-data-in-your-application.md)   
 [Überprüfen von Daten](../Topic/Validating%20Data.md)   
 [Speichern von Daten](../data-tools/saving-data.md)   
 [Exemplarische Vorgehensweisen zur Arbeit mit Daten](../Topic/Data%20Walkthroughs.md)