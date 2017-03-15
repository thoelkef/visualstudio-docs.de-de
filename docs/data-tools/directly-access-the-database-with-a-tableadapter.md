---
title: "Gewusst wie: Direktes Zugreifen auf die Datenbank mit einem TableAdapter | Microsoft Docs"
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
  - "Daten [Visual Studio], Speichern"
  - "Datenbanken [Visual Basic], Zugreifen auf Datenbanken mit einem TableAdapter"
  - "Datasets [Visual Basic], Hinzufügen zu Projekten"
  - "DBDirect-Methoden"
  - "GenerateDbDirectMethods-Eigenschaft"
  - "Speichern von Daten"
  - "TableAdapter.Delete-Methode"
  - "TableAdapter.GenerateDBDirectMethods-Eigenschaft"
  - "TableAdapter.Insert-Methode"
  - "TableAdapter.Update-Methode"
  - "TableAdapters"
ms.assetid: 012c5924-91f7-4790-b2a6-f51402b7014b
caps.latest.revision: 12
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Gewusst wie: Direktes Zugreifen auf die Datenbank mit einem TableAdapter
Zusätzlich zu den Befehlen `InsertCommand`, `UpdateCommand` und `DeleteCommand` werden für die TableAdapter\-Erstellung Methoden verwendet, die direkt gegen die Datenbank ausgeführt werden können.  Diese Methoden \(`TableAdapter.Insert`, `TableAdapter.Update` und `TableAdapter.Delete`\) können direkt aufgerufen werden, um Daten in der Datenbank zu bearbeiten.  
  
 Wenn Sie diese direkten Methoden nicht erstellen möchten, legen Sie die `GenerateDbDirectMethods`\-Eigenschaft des TableAdapter im **Eigenschaftenfenster** auf `false` fest.  Sämtliche einem TableAdapter zusätzlich zur Hauptabfrage des TableAdapter hinzugefügten Abfragen sind eigenständige Abfragen und generieren daher keine DbDirect\-Methoden.  
  
## Direktes Senden von Befehlen an eine Datenbank  
 Rufen Sie DbDirect\-Methode des TableAdapter auf, die die von Ihnen vorgesehene Aufgabe ausführt.  
  
#### So fügen Sie neue Datensätze direkt in eine Datenbank ein  
  
-   Rufen Sie die `Insert`\-Methode des TableAdapter auf, und übergeben Sie die Werte für jede Spalte als Parameter.  In der folgenden Prozedur wird als Beispiel die Tabelle `Region` der Datenbank Northwind verwendet.  
  
    > [!NOTE]
    >  Wenn Ihnen keine Instanz zur Verfügung steht, instanziieren Sie den TableAdapter, den Sie verwenden möchten.  
  
     [!code-vb[VbRaddataSaving#15](../data-tools/codesnippet/VisualBasic/directly-access-the-database-with-a-tableadapter_1.vb)]
     [!code-cs[VbRaddataSaving#15](../data-tools/codesnippet/CSharp/directly-access-the-database-with-a-tableadapter_1.cs)]  
  
#### So aktualisieren Sie Datensätze direkt in einer Datenbank  
  
-   Rufen Sie die `Update`\-Methode des TableAdapter auf, um die neuen und ursprünglichen Werte für jede Spalte als Parameter zu übergeben.  
  
    > [!NOTE]
    >  Wenn Ihnen keine Instanz zur Verfügung steht, instanziieren Sie den TableAdapter, den Sie verwenden möchten.  
  
     [!code-vb[VbRaddataSaving#18](../data-tools/codesnippet/VisualBasic/directly-access-the-database-with-a-tableadapter_2.vb)]
     [!code-cs[VbRaddataSaving#18](../data-tools/codesnippet/CSharp/directly-access-the-database-with-a-tableadapter_2.cs)]  
  
#### So löschen Sie Datensätze direkt in einer Datenbank  
  
-   Rufen Sie die `Delete`\-Methode des TableAdapter auf, und übergeben Sie der `Delete`\-Methode die Werte für alle Spalten als Parameter.  \(In diesem Beispiel wird die Tabelle `Region` der Datenbank Northwind verwendet.\)  
  
    > [!NOTE]
    >  Wenn Ihnen keine Instanz zur Verfügung steht, instanziieren Sie den TableAdapter, den Sie verwenden möchten.  
  
     [!code-vb[VbRaddataSaving#21](../data-tools/codesnippet/VisualBasic/directly-access-the-database-with-a-tableadapter_3.vb)]
     [!code-cs[VbRaddataSaving#21](../data-tools/codesnippet/CSharp/directly-access-the-database-with-a-tableadapter_3.cs)]  
  
## Siehe auch  
 [Übersicht über Datenanwendungen in Visual Studio](../data-tools/overview-of-data-applications-in-visual-studio.md)   
 [Herstellen von Datenverbindungen in Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Vorbereiten der Anwendung auf den Empfang von Daten](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [Abrufen von Daten für die Anwendung](../data-tools/fetching-data-into-your-application.md)   
 [Binden von Steuerelementen an Daten in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Bearbeiten von Daten in der Anwendung](../data-tools/editing-data-in-your-application.md)   
 [Überprüfen von Daten](../Topic/Validating%20Data.md)   
 [Speichern von Daten](../data-tools/saving-data.md)   
 [Übersicht über TableAdapters](../data-tools/tableadapter-overview.md)   
 [Befehle und Parameter](../Topic/Commands%20and%20Parameters.md)