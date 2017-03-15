---
title: "Gewusst wie: DataSets und TableAdapters in verschiedene Projekte aufteilen | Microsoft Docs"
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
  - "N-Tier-Anwendungen, Trennen von Datasets und TableAdapters"
  - "TableAdapters, N-Tier-Anwendungen"
ms.assetid: f66a3940-6227-46af-a930-9177f425f4fd
caps.latest.revision: 18
caps.handback.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Gewusst wie: DataSets und TableAdapters in verschiedene Projekte aufteilen
Typisierte DataSets wurden weiterentwickelt, damit die [TableAdapters](../Topic/TableAdapters.md)\-Klasse und die DataSet\-Klasse in separaten Projekten generiert werden können.  Dies ermöglicht eine bequeme Trennung der Anwendungsebenen und die Erzeugung von N\-Tier\-Datenanwendungen.  
  
 Die folgende Vorgehensweise beschreibt die Verwendung von [Erstellen und Bearbeiten von typisierten Datasets](../data-tools/creating-and-editing-typed-datasets.md) zum Generieren von DataSet\-Code in einem zu dem Projekt, das den generierten `TableAdapter`\-Code enthält, getrennten Projekt.  
  
## Trennen von DataSets und TableAdapters  
 Wenn Sie DataSet\-Code von `TableAdapter`\-Code trennen, muss sich das Projekt, das den DataSet\-Code enthält, in der aktuellen Projektmappe befinden.  Wenn sich dieses Projekt nicht in der aktuellen Projektmappe befindet, ist es in der **DataSet\-Projekt**–Liste im Fenster **Eigenschaften** nicht verfügbar.  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
#### So separieren Sie das DataSet in ein anderes Projekt  
  
1.  Öffnen Sie eine Projektmappe, die ein DataSet \(XSD\-Datei\) enthält.  
  
    > [!NOTE]
    >  Wenn die Projektmappe das Projekt, in das Sie den DataSet\-Code separieren möchten, nicht enthält, erzeugen Sie es, oder fügen Sie der Projektmappe ein bestehendes Projekt hinzu.  
  
2.  Doppelklicken Sie auf eine typisierte DataSet\-Datei \(XSD\-Datei\) im **Projektmappen\-Explorer**, um das DataSet mit dem **DataSet\-Designer** zu öffnen.  
  
3.  Klicken Sie auf einen leeren Bereich im **DataSet\-Designer**.  
  
4.  Suchen Sie den Knoten **DataSet\-Projekt** im Fenster **Eigenschaften**.  
  
5.  Klicken Sie in der **DataSet\-Projekt**\-Liste auf den Namen des Projekts, in dem Sie den DataSet\-Code generieren möchten.  
  
     Nachdem Sie auf das Projekt geklickt haben, in dem Sie den DataSet\-Code generieren möchten, wird in der **DataSet\-Datei**\-Eigenschaft ein Standarddateiname angezeigt.  Sie können diesen Namen bei Bedarf ändern.  Wenn Sie den DataSet\-Code in einem bestimmten Verzeichnis generieren möchten, können Sie in der **Projektordner**–Eigenschaft den Namen des Ordners angeben.  
  
    > [!NOTE]
    >  Bei einer Aufteilung von DataSets und TableAdaptern durch Festlegen der **DataSet\-Projekt**\-Eigenschaft werden vorhandene partielle DataSet\-Klassen in dem Projekt nicht automatisch verschoben.  Vorhandene partielle DataSet\-Klassen müssen manuell in das DataSet\-Projekt verschoben werden.  
  
6.  Speichern Sie das DataSet.  
  
     Der DataSet\-Code wird im Projekt generiert, das in der **DataSet\-Projekt**\-Eigenschaft ausgewählt wurde. Der **TableAdapter**\-Code wird im aktuellen Projekt generiert.  
  
 Standardmäßig wird bei einer Trennung von DataSet\-Code und `TableAdapter`\-Code eine separate Klassendatei in jedem Projekt angelegt.  Das ursprüngliche Projekt enthält eine Datei mit dem Namen  DatasetName.Designer.vb oder DatasetName.Designer.cs, die den `TableAdapter`\-Code enthält.  Das Projekt, das in der **DataSet\-Projekt**\-Eigenschaft ausgewählt wurde, enthält eine Datei mit dem Namen DatasetName.DataSet.Designer.vb oder DatasetName.DataSet.Designer.cs, die den DataSet\-Code enthält.  
  
> [!NOTE]
>  Wenn das DataSet\-Projekt oder das `TableAdapter`\-Projekt markiert ist, klicken Sie im **Projektmappen\-Explorer** auf **Alle Dateien anzeigen**, um die generierte Klassendatei anzuzeigen.  
  
## Siehe auch  
 [Übersicht über N\-Tier\-Datenanwendungen](../data-tools/n-tier-data-applications-overview.md)   
 [Exemplarische Vorgehensweise: Erstellen einer N\-Tier\-Datenanwendung](../data-tools/walkthrough-creating-an-n-tier-data-application.md)   
 [Hierarchische Aktualisierung](../data-tools/hierarchical-update.md)   
 [Zugreifen auf Daten in Visual Studio](../data-tools/accessing-data-in-visual-studio.md)   
 [ADO.NET](../Topic/ADO.NET.md)