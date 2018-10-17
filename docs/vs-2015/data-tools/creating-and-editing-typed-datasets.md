---
title: Erstellen und Bearbeiten typisierter Datasets | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- Designer_Microsoft.VSDesigner.DataSource.Designer.DataSourceRootDesigner
- vs.data.adddataset
dev_langs:
- VB
- CSharp
- C++
- aspx
- aspx
helpviewer_keywords:
- datasets [Visual Basic], visual designer
- data [Visual Studio], Dataset Designer
- Dataset Designer
ms.assetid: cd0dbe93-be9b-41e4-bc39-e9300678c1f2
caps.latest.revision: 26
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 8c18717cd2a5c7e05b79dbe575d919ef0c8670dd
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49225838"
---
# <a name="creating-and-editing-typed-datasets"></a>Erstellen und Bearbeiten von typisierten Datasets
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die**Dataset-Designer** ist ein Satz von visual Tools, die Sie verwenden können, erstellen und Bearbeiten typisierter Datasets und die einzelnen Elemente, die sie enthalten.  
  
 Die **Dataset-Designer** stellt visuelle Darstellungen der Objekte enthalten, die in typisierten Datasets bereit. Sie erstellen und Ändern von [TableAdapters](../data-tools/tableadapter-overview.md), [TableAdapter-Abfragen](../data-tools/how-to-create-tableadapter-queries.md), <xref:System.Data.DataTable>s, <xref:System.Data.DataColumn>s, und <xref:System.Data.DataRelation>mit der **Dataset-Designer**.  
  
 Zum Öffnen der **Dataset-Designer**, doppelklicken Sie auf ein Dataset in **Projektmappen-Explorer**, oder mit der rechten Maustaste in ein Dataset in der **Datenquellen** Fenster, und klicken Sie auf **bearbeiten DataSet mit Designer**. Weitere Informationen finden Sie unter [Vorgehensweise: Öffnen Sie ein Dataset im Dataset-Designer](http://msdn.microsoft.com/library/36fc266f-365b-42cb-aebb-c993dc2c47c3). Hinzufügen eines neuen <xref:System.Data.DataSet> das Element mit dem die **neues Element hinzufügen** Dialogfeld wird geöffnet. die **Dataset-Designer** mit einem leeren Dataset für die Bearbeitung bereit.  
  
> [!NOTE]
>  Die **Dataset-Designer** kann zum Erweitern der Funktionalität eines Datasets verwendet werden. Doppelklicken Sie auf der Entwurfsoberfläche oder mit der rechten Maustaste, und wählen Sie **Ansichtscode** Datei eine partielle Klasse erstellen, können Sie Code hinzufügen, auf das Dataset, die nicht geändert oder vom Designer gelöscht werden. Weitere Informationen zum Erweitern der Funktionalität eines TableAdapter, finden Sie unter [erweitern die Funktionalität eines TableAdapter](../data-tools/extend-the-functionality-of-a-tableadapter.md).  
  
 Die folgende Tabelle enthält die allgemeinen Aufgaben, erreichen Sie mit, der **Dataset-Designer**.  
  
|Beschreibung|Siehe|  
|--------|---------|  
|Erstellen eines TableAdapter|[Erstellen und Konfigurieren eines TableAdapters](../data-tools/create-and-configure-tableadapters.md)|  
|Bearbeiten eines TableAdapters|[Vorgehensweise: Bearbeiten von TableAdapters](http://msdn.microsoft.com/library/ca178745-e35a-45f1-a395-23cddfd8f855)|  
|Erstellen einer TableAdapter-Abfrage|[Gewusst wie: Erstellen von TableAdapter-Abfragen](../data-tools/how-to-create-tableadapter-queries.md)|  
|Bearbeiten einer TableAdapter-Abfrage|[Gewusst wie: Bearbeiten von TableAdapter-Abfragen](../data-tools/how-to-edit-tableadapter-queries.md)|  
|Erstellen einer <xref:System.Data.DataTable>|[Gewusst wie: Erstellen von Datentabellen](../data-tools/how-to-create-data-tables.md)|  
|Bearbeiten einer <xref:System.Data.DataTable>|[Entwerfen von DataTables](../data-tools/designing-datatables.md)|  
|Erstellen einer <xref:System.Data.DataColumn>|[Vorgehensweise: Hinzufügen von Spalten zu einer "DataTable"](http://msdn.microsoft.com/library/8ca21f77-b99a-47a7-a656-7cfd7a1bd9df)|  
|Erstellen einer Beziehung zwischen zwei <xref:System.Data.DataTable>s|[Vorgehensweise: Erstellen von DataRelations mit Dataset-Designer](http://msdn.microsoft.com/library/a3ab4803-0b50-4b74-9920-ab20bfbf1aa2)|  
|Erweitern der Datasetfunktionen|[Vorgehensweise: Erweitern der Funktionalität eines Datasets](http://msdn.microsoft.com/library/dfbc21eb-7ea2-4942-addd-49677f5493be)|  
|Hinzufügen einer Validierung zum <xref:System.Data.DataTable.ColumnChanging>-Ereignis einer Datentabelle|[Vorgehensweise: Validieren von Daten während Spaltenänderungen](http://msdn.microsoft.com/library/a2680600-67b6-4a40-a77e-b5bc638281c5)|  
|Hinzufügen einer Validierung zum <xref:System.Data.DataTable.RowChanging>-Ereignis einer Datentabelle|[Vorgehensweise: Validieren von Daten während Zeilenänderungen](http://msdn.microsoft.com/library/afc03c77-dfed-4302-9376-929400468ecc)|  
  
## <a name="creating-objects-on-the-design-surface"></a>Erstellen von Objekten auf der Entwurfsoberfläche  
 Sie können Datasets erstellen, indem Sie die einzelnen Objekte hinzufügen und bearbeiten, die ein Dataset bilden. Die folgende Tabelle enthält eine Erläuterung der verschiedenen Objekte in der **DataSet** Registerkarte die **Toolbox** , die auf die Entwurfsoberfläche gezogen werden können:  
  
|Object|Beschreibung|  
|------------|-----------------|  
|TableAdapter|Enthält eine Auflistung von Datenbefehlen und eine Datenverbindung für die Kommunikation mit der zugrunde liegenden Datenbank und zum Auffüllen einer Datentabelle. Weitere Informationen finden Sie unter [Übersicht über TableAdapters](../data-tools/tableadapter-overview.md) und [erstellen und Konfigurieren eines TableAdapters](../data-tools/create-and-configure-tableadapters.md).|  
|Abfrage|TableAdapter-Abfragen sind Methoden mit starker Typisierung, die SQL-Anweisungen und gespeicherte Prozeduren ausführen. Durch die Ausführung einer TableAdapter-Abfrage werden Datentabellen mit Daten aufgefüllt oder andere Datenbankaufgaben ausgeführt. Weitere Informationen finden Sie unter [Vorgehensweise: Erstellen von TableAdapter-Abfragen](../data-tools/how-to-create-tableadapter-queries.md). Ziehen einer Abfrage auf eine Tabelle wird die Abfrage hinzugefügt, die Tabelle, während eine Abfrage auf einen leeren Bereich der ziehen die **Dataset-Designer** Erstellen einer globalen Abfrage. Weitere Informationen finden Sie unter [Vorgehensweise: Hinzufügen von globalen Abfragen zu einem TableAdapter](../data-tools/how-to-add-global-queries-to-a-tableadapter.md).|  
|<xref:System.Data.DataTable>|Stellt eine Auflistung der Zeilen im Arbeitspeicher dar, die von einer Datenbank zurückgegeben wird.|  
|Beziehung (<xref:System.Data.DataRelation>)|Stellt die hierarchische Beziehung zwischen zwei <xref:System.Data.DataTable>s dar. Weitere Informationen finden Sie unter [Einführung in DataRelation-Objekte](http://msdn.microsoft.com/library/89d8a881-8265-41f2-a88b-61311ab06192) und [Exemplarische Vorgehensweise: Erstellen einer Beziehung zwischen Datentabellen](http://msdn.microsoft.com/library/9b3f1c87-7098-4ed4-a710-cde8f8059f82).|  
  
> [!NOTE]
>  Die **Dataset-Designer** eine Verbindung mit einer zugrunde liegenden Datenbank nur dann, wenn ein Dataset erstellt wird, erkennt des Designers nicht automatisch spätere Änderungen an der Datenbank. Um eine vorhandene XSD-Datei zu aktualisieren, führen Sie erneut die **Konfigurations-Assistenten**. Wenn sich die Tabellenbeziehungen geändert haben, entfernen Sie die relevanten Tabellen in der XSD-Datei und fügen sie wieder hinzu.  
  
## <a name="linq-to-dataset"></a>LINQ to DataSet  
 [!INCLUDE[linq_dataset](../includes/linq-dataset-md.md)] ermöglicht [LINQ (Language-Integrated Query)](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d) für Daten in einem <xref:System.Data.DataSet> Objekt. Weitere Informationen finden Sie unter [LINQ to DataSet](http://msdn.microsoft.com/library/743e3755-3ecb-45a2-8d9b-9ed41f0dcf17).  
  
## <a name="see-also"></a>Siehe auch  
 [Exemplarische Vorgehensweise: Erstellen eines Datasets mit Dataset-Designer](../data-tools/walkthrough-creating-a-dataset-with-the-dataset-designer.md)   
 [Exemplarische Vorgehensweise: Erstellen eines TableAdapter mit mehreren Abfragen](../data-tools/walkthrough-creating-a-tableadapter-with-multiple-queries.md)   
 [Exemplarische Vorgehensweise: Erstellen einer DataTable im Dataset-Designer](../data-tools/walkthrough-creating-a-datatable-in-the-dataset-designer.md)   
 [Exemplarische Vorgehensweise: Erstellen einer Beziehung zwischen Datentabellen](http://msdn.microsoft.com/library/9b3f1c87-7098-4ed4-a710-cde8f8059f82)   
 [Exemplarische Vorgehensweise: Anzeigen von Daten in einem Windows Form](../data-tools/walkthrough-displaying-data-on-a-windows-form.md)   
 [Datenquellenfenster](http://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992)   
 [Datasettools in Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)   
 [Vorbereiten der Anwendung zum Empfangen von Daten](http://msdn.microsoft.com/library/c17bdb7e-c234-4f2f-9582-5e55c27356ad)   
 [Abrufen von Daten für Ihre Anwendung](../data-tools/fetching-data-into-your-application.md)   
 [Bearbeiten von Daten in Ihrer Anwendung](../data-tools/editing-data-in-your-application.md)   
 [Überprüfen von Daten](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)   
 [Speichern von Daten](../data-tools/saving-data.md)