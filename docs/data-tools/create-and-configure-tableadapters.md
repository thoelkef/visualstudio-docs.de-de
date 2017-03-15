---
title: "Gewusst wie: Erstellen von TableAdapters | Microsoft Docs"
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
  - "Erstellen von TableAdapters"
  - "Daten [Visual Studio], Erstellen von Datenkomponenten"
  - "Daten [Visual Studio], Erstellen von TableAdapters"
  - "Daten [Visual Studio], TableAdapters"
  - "TableAdapter, Erstellen"
ms.assetid: 08630d69-0d6c-4e8f-b42d-2922f45f8415
caps.latest.revision: 28
caps.handback.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Gewusst wie: Erstellen von TableAdapters
TableAdapters ermöglichen die Kommunikation zwischen der Anwendung und einer Datenbank.  Dies bedeutet, dass ein TableAdapter eine Verbindung mit einer Datenbank herstellt, Abfragen oder gespeicherte Prozeduren ausführt und eine neue Datentabelle mit den zurückgegebenen Daten zurückgibt oder aber eine vorhandene <xref:System.Data.DataTable> mit den zurückgegebenen Daten füllt.  Mit TableAdapters werden außerdem aktualisierte Daten von der Anwendung an die Datenbank zurückgesendet.  
  
 Sie können TableAdapters erstellen, indem Sie eine der folgenden Aktionen ausführen:  
  
-   Ausführen des [TableAdapter\-Konfigurations\-Assistent](../Topic/TableAdapter%20Configuration%20Wizard.md) im [DataSet\-Designer](../data-tools/creating-and-editing-typed-datasets.md).  
  
-   Ausführen des [Assistent zum Konfigurieren von Datenquellen](../data-tools/media/data-source-configuration-wizard.png), wobei Sie als Datenquellentyp entweder **Datenbank** oder **Webdienst** auswählen.  
  
-   Ziehen von Datenbankobjekten aus dem [Server\-Explorer](../Topic/Server%20Explorer.md) auf den **DataSet\-Designer**.  
  
 Eine Einführung in TableAdapters finden Sie unter [Übersicht über TableAdapters](../data-tools/tableadapter-overview.md).  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
## Erstellen von TableAdapters mit dem TableAdapter\-Konfigurations\-Assistenten  
 Der **TableAdapter\-Konfigurations\-Assistent** erstellt anhand der von Ihnen angegebenen Informationen einen einzelnen TableAdapter.  
  
#### So erstellen Sie einen TableAdapter mit dem TableAdapter\-Konfigurations\-Assistenten  
  
1.  Öffnen Sie ein Dataset im **Dataset\-Designer**.  Weitere Informationen finden Sie unter [Gewusst wie: Öffnen eines Datasets im DataSet\-Designer](../Topic/How%20to:%20Open%20a%20Dataset%20in%20the%20Dataset%20Designer.md).  
  
2.  Ziehen Sie einen **TableAdapter** aus der Registerkarte **DataSet** der **Toolbox** auf die Entwurfsoberfläche.  
  
     Der **TableAdapter\-Konfigurations\-Assistent** wird geöffnet.  
  
3.  Führen Sie den Assistenten aus; dem Dataset werden eine Datentabelle und ein TableAdapter hinzugefügt.  Weitere Informationen finden Sie unter [TableAdapter\-Konfigurations\-Assistent](../Topic/TableAdapter%20Configuration%20Wizard.md).  
  
## Erstellen von TableAdapters mit dem Assistenten zum Konfigurieren von Datenquellen  
 Der **Assistent zum Konfigurieren von Datenquellen** erstellt für jedes Datenbankobjekt, das während der Ausführung des Assistenten ausgewählt wird, einen TableAdapter.  Nachdem der **Assistent zum Konfigurieren von Datenquellen** fertig gestellt wurde, können Sie sich die erstellten TableAdapters ansehen, indem Sie das Dataset im **DataSet\-Designer** öffnen.  Weitere Informationen finden Sie unter [Gewusst wie: Öffnen eines Datasets im DataSet\-Designer](../Topic/How%20to:%20Open%20a%20Dataset%20in%20the%20Dataset%20Designer.md).  
  
#### So erstellen Sie einen TableAdapter mit dem Assistenten zum Konfigurieren von Datenquellen  
  
1.  Wählen Sie im [Datenquellenfenster](../Topic/Data%20Sources%20Window.md) die Option **Neue Datenquelle hinzufügen** aus.  Wählen Sie im Menü **Daten** den Befehl **Datenquellen anzeigen**, um das **Datenquellenfenster** zu öffnen.  
  
     Der **Assistent zum Konfigurieren von Datenquellen** wird geöffnet.  
  
2.  Führen Sie den Assistenten aus, wobei Sie als Datenquellentyp entweder **Datenbank** oder **Webdienst** auswählen.  Weitere Informationen finden Sie unter [Gewusst wie: Herstellen einer Verbindung zu Daten in einer Datenbank](../data-tools/how-to-connect-to-data-in-a-database.md) oder unter [Gewusst wie: Herstellen einer Verbindung mit Daten in einem Dienst](../data-tools/how-to-connect-to-data-in-a-service.md).  
  
## Erstellen von TableAdapters aus Server\-Explorer\-Datenbankobjekten  
 Für jedes Datenbankobjekt, das Sie auf den **DataSet\-Designer** ziehen, wird ein einzelner TableAdapter erstellt.  
  
#### So erstellen Sie einen TableAdapter aus Server\-Explorer\-Datenbankobjekten  
  
1.  Öffnen Sie ein Dataset im **Dataset\-Designer**.  Weitere Informationen finden Sie unter [Gewusst wie: Öffnen eines Datasets im DataSet\-Designer](../Topic/How%20to:%20Open%20a%20Dataset%20in%20the%20Dataset%20Designer.md).  
  
2.  Ziehen Sie ein Datenbankobjekt aus einer Datenverbindung im [Server\-Explorer](../Topic/Server%20Explorer.md) auf die Oberfläche des **DataSet\-Designers**.  
  
     Dem Dataset werden eine Datentabelle und ein TableAdapter hinzugefügt.  
  
## Siehe auch  
 [Gewusst wie: Aktualisieren von Daten mit einem TableAdapter](../data-tools/update-data-by-using-a-tableadapter.md)   
 [Binden von Windows Forms\-Steuerelementen an Daten in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Vorbereiten der Anwendung auf den Empfang von Daten](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [Abrufen von Daten für die Anwendung](../data-tools/fetching-data-into-your-application.md)   
 [Binden von Steuerelementen an Daten in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Bearbeiten von Daten in der Anwendung](../data-tools/editing-data-in-your-application.md)   
 [Überprüfen von Daten](../Topic/Validating%20Data.md)   
 [Speichern von Daten](../data-tools/saving-data.md)   
 [Exemplarische Vorgehensweisen zur Arbeit mit Daten](../Topic/Data%20Walkthroughs.md)