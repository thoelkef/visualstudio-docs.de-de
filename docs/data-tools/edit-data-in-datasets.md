---
title: "Bearbeiten von Daten in Datasets | Microsoft Docs"
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
  - "Daten [Visual Studio], Bearbeiten in Datasets"
  - "Datasets [Visual Basic], Bearbeiten von Daten"
ms.assetid: 50d5c580-fbf7-408f-be70-e63ac4f4d0eb
caps.latest.revision: 15
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Bearbeiten von Daten in Datasets
Die Daten in einem <xref:System.Data.DataSet> werden bearbeitet, indem die Daten in den einzelnen <xref:System.Data.DataTable>\-Objekten bearbeitet werden, die das Dataset bilden.  Das Bearbeiten der Daten in Datentabellen entspricht weitgehend dem Bearbeiten von Daten in einer Datenbanktabelle und kann das Einfügen, Aktualisieren und Löschen von Datensätzen in der Tabelle umfassen.  
  
 Neben dem Ändern der Daten haben Sie auch die Möglichkeit, eine <xref:System.Data.DataTable> so abzufragen, dass bestimmte Datenzeilen zurückgegeben werden, z. B. einzelne Zeilen, bestimmte Versionen von Zeilen \(ursprüngliche und vorgesehene\), nur geänderte Zeilen oder Zeilen mit Fehlern.  
  
## Häufige Aufgaben beim Arbeiten mit Datentabellen  
 Die folgende Tabelle enthält Links zu Aufgaben, die beim Bearbeiten und Abfragen von Daten in einem Dataset häufig vorkommen:  
  
|Aufgabe|Beschreibung|  
|-------------|------------------|  
|Einfügen von neuen Datensätzen in eine Datentabelle.|Erstellen Sie eine neue <xref:System.Data.DataRow>, und fügen Sie sie der Zeilenauflistung der Tabelle hinzu.  Weitere Informationen finden Sie unter [Gewusst wie: Hinzufügen von Zeilen zu einer DataTable](../Topic/How%20to:%20Add%20Rows%20to%20a%20DataTable.md).|  
|Aktualisieren von vorhandenen Datensätzen in einer Datentabelle.|Weisen Sie einer bestimmten Spalte einer Datenzeile direkt einen Wert zu.  Weitere Informationen finden Sie unter [Gewusst wie: Bearbeiten von Zeilen in einer DataTable](../Topic/How%20to:%20Edit%20Rows%20in%20a%20DataTable.md).|  
|Löschen von Datensätzen aus einer Datentabelle.|Rufen Sie die <xref:System.Data.DataRow.Delete%2A>\-Methode der Datenzeile auf, die Sie aus der Tabelle entfernen möchten.  Weitere Informationen finden Sie unter [Gewusst wie: Löschen von Zeilen in einer DataTable](../Topic/How%20to:%20Delete%20Rows%20in%20a%20DataTable.md).|  
|Suchen von geänderten Datensätzen in einer Datentabelle.|Rufen Sie die <xref:System.Data.DataTable.GetChanges%2A>\-Methode einer Datentabelle auf.  Weitere Informationen finden Sie unter [Gewusst wie: Abrufen von geänderten Zeilen](../Topic/How%20to:%20Retrieve%20Changed%20Rows.md).|  
|Zugreifen auf verschiedene Versionen einer Zeile in einer Datentabelle.|Greifen Sie auf die einzelnen Spalten einer Datenzeile zu, indem Sie die <xref:System.Data.DataRowVersion> übergeben, die Sie anzeigen möchten.  Weitere Informationen finden Sie unter [Gewusst wie: Abrufen spezifischer Versionen einer DataRow](../data-tools/how-to-get-specific-versions-of-a-datarow.md).|  
|Suchen von Zeilen mit Fehlern in einer Datentabelle.|Überprüfen Sie die <xref:System.Data.DataTable.HasErrors%2A>\-Eigenschaft einer Datentabelle.  Weitere Informationen finden Sie unter [Gewusst wie: Suchen nach Zeilen mit Fehlern](../Topic/How%20to:%20Locate%20Rows%20that%20Have%20Errors.md).|  
  
## Siehe auch  
 [DataTables](../Topic/DataTables.md)   
 [Vorbereiten der Anwendung auf den Empfang von Daten](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [Abrufen von Daten für die Anwendung](../data-tools/fetching-data-into-your-application.md)   
 [Bearbeiten von Daten in der Anwendung](../data-tools/editing-data-in-your-application.md)   
 [DataTables](../Topic/DataTables.md)   
 [Exemplarische Vorgehensweisen zur Arbeit mit Daten](../Topic/Data%20Walkthroughs.md)   
 [Binden von Windows Forms\-Steuerelementen an Daten in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Übersicht über Datenanwendungen in Visual Studio](../data-tools/overview-of-data-applications-in-visual-studio.md)   
 [Herstellen von Datenverbindungen in Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Binden von Steuerelementen an Daten in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Überprüfen von Daten](../Topic/Validating%20Data.md)   
 [Speichern von Daten](../data-tools/saving-data.md)