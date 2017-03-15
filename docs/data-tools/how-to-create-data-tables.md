---
title: "Gewusst wie: Erstellen von Datentabellen | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "Microsoft.VSDesigner.DataSource.DesignTable"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
helpviewer_keywords: 
  - "Daten [Visual Studio], Erstellen von Datentabellen"
  - "DataSet-Designer, Erstellen von Datentabellen"
  - "Tabellen [Visual Studio], Erstellen"
ms.assetid: 0e8bf4c4-3d05-4b20-9926-9d29914b26ed
caps.latest.revision: 19
caps.handback.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
robots: noindex,nofollow
---
# Gewusst wie: Erstellen von Datentabellen
Daten können in <xref:System.Data.DataTable>\-Objekten im Arbeitsspeicher gespeichert werden. \(Datasets bestehen aus <xref:System.Data.DataTable>\-Objekten.\) Zum Erstellen neuer Datentabellen mit TableAdapters können Sie den [TableAdapter\-Konfigurations\-Assistent](../Topic/TableAdapter%20Configuration%20Wizard.md) verwenden oder Datenbankobjekte aus dem **Server\-Explorer** auf den **DataSet\-Designer** ziehen.  
  
 Datentabellen werden auch als Nebenprodukt beim Erstellen neuer TableAdapters im [Assistent zum Konfigurieren von Datenquellen](../data-tools/media/data-source-configuration-wizard.png) generiert. Sie können jedoch auch separat erstellt werden.  Sie erstellen eine eigenständige Datentabelle, indem Sie ein <xref:System.Data.DataTable>\-Objekt aus der Registerkarte **DataSet** der **Toolbox** auf den **DataSet\-Designer** ziehen.  
  
> [!NOTE]
>  Weitere Informationen zum programmgesteuerten Erstellen von Datentabellen finden Sie unter [Erstellen einer DataTable](../Topic/Creating%20a%20DataTable.md).  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
## Erstellen einer Datentabelle mit TableAdapter  
 Datentabellen mit TableAdapters enthalten Methoden, die die Tabelle mit Daten füllen und Änderungen in die zugrunde liegende Datenbank eintragen.  Zum Erstellen von TableAdapters führen Sie den **TableAdapter\-Konfigurations\-Assistenten** aus oder ziehen Datenbankobjekte aus dem **Server\-Explorer** auf den **DataSet\-Designer**.  
  
#### So erstellen Sie eine neue Datentabelle mit TableAdapter  
  
1.  Öffnen Sie das Dataset im **DataSet\-Designer**.  Weitere Informationen finden Sie unter [Gewusst wie: Öffnen eines Datasets im DataSet\-Designer](../Topic/How%20to:%20Open%20a%20Dataset%20in%20the%20Dataset%20Designer.md).  
  
2.  Ziehen Sie einen **TableAdapter** aus der Registerkarte **DataSet** der **Toolbox** auf den **DataSet\-Designer**.  
  
     Der **TableAdapter\-Konfigurations\-Assistent** wird geöffnet.  
  
3.  Durchlaufen Sie den Assistenten.  Weitere Informationen finden Sie unter [TableAdapter\-Konfigurations\-Assistent](../Topic/TableAdapter%20Configuration%20Wizard.md)  
  
#### So erstellen Sie eine neue Datentabelle mit einem TableAdapter unter Verwendung des Server\-Explorers  
  
1.  Öffnen Sie das Dataset im **Datenquellen\-Designer**.  
  
2.  Ziehen Sie ein Datenbankobjekt \(z. B. eine Tabelle\) aus dem **Server\-Explorer** auf den **DataSet\-Designer**.  
  
## Erstellen einer eigenständigen Datentabelle  
 Damit eigenständige Tabellen mit Daten gefüllt werden, muss eine `Fill`\-Logik implementiert werden.  Informationen zum Füllen eigenständiger Datentabellen mit Daten finden Sie unter [Auffüllen eines DataSet mit einem DataAdapter](../Topic/Populating%20a%20DataSet%20from%20a%20DataAdapter.md).  
  
#### So erstellen Sie eine neue eigenständige Datentabelle  
  
1.  Öffnen Sie das Dataset im **DataSet\-Designer**.  
  
2.  Ziehen Sie in der **Toolbox** aus der Registerkarte **DataSet** eine <xref:System.Data.DataTable> in den **Dataset\-Designer**.  
  
3.  Fügen Sie Spalten hinzu, um die Datentabelle zu definieren.  Weitere Informationen finden Sie unter [Gewusst wie: Hinzufügen von Spalten zu einer DataTable](../Topic/How%20to:%20Add%20Columns%20to%20a%20DataTable.md).  
  
## Siehe auch  
 <xref:System.Data.DataTable>   
 [Exemplarische Vorgehensweisen zur Arbeit mit Daten](../Topic/Data%20Walkthroughs.md)   
 [Exemplarische Vorgehensweise: Anzeigen von Daten in einem Windows Form](../data-tools/walkthrough-displaying-data-on-a-windows-form.md)   
 [Übersicht über TableAdapters](../data-tools/tableadapter-overview.md)   
 [Erstellen und Bearbeiten von typisierten Datasets](../data-tools/creating-and-editing-typed-datasets.md)   
 [Übersicht über Datenquellen](../data-tools/add-new-data-sources.md)   
 [Datenquellenfenster](../Topic/Data%20Sources%20Window.md)   
 [Gewusst wie: Herstellen einer Verbindung zu Daten in einer Datenbank](../data-tools/how-to-connect-to-data-in-a-database.md)   
 [Überprüfen von Daten](../Topic/Validating%20Data.md)