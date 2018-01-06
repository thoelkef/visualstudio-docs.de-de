---
title: DataSet-Tools in Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.data.DataSet
helpviewer_keywords:
- untyped datasets
- datasets [Visual Basic], extended properties
- typed datasets
- current record in dataset
- XML [Visual Basic], datasets
- DataSet class, about datasets
- unique constraints (datasets)
- data relationships
- parent records in datasets
- extended properties, in typed datasets
- datasets [Visual Basic]
- schemas [Visual Basic], datasets
- datasets [Visual Basic], msprop
- master-detail tables, datasets
- databases [Visual Basic], updating
- msprop
- foreign keys, datasets
- DataSet class
- datasets [Visual Basic], filling
- case sensitivity, datasets
- constraints [Visual Basic], datasets
- child records
- related tables, datasets
- updating datasets, about dataset updates
- data caching, datasets
- DataRelation object, datasets
- untyped datasets, compared to typed datasets
- cache [Visual Studio], datasets
- datasets [Visual Basic], relationships
- related tables
- XML schemas, about XML schemas and datasets
- relationships, datasets
- typed datasets, compared to untyped datasets
- datasets [Visual Basic], populating
- datasets [Visual Basic], namespace
- data adapters, populating datasets
ms.assetid: ee57f4f6-9fe1-4e0a-be9a-955c486ff427
caps.latest.revision: "49"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.workload: data-storage
ms.openlocfilehash: a8c8660fbc489dd8c4926bb09b8b42006da0897a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="dataset-tools-in-visual-studio"></a>DataSet-Tools in Visual Studio
> [!NOTE]
>  Datasets und verwandten Klassen sind ältere .NET Technologien aus den frühen 2000 s, mit denen Anwendungen arbeiten mit Daten im Arbeitsspeicher, während die Anwendungen aus der Datenbank getrennt werden. Sie sind besonders nützlich für Anwendungen, mit denen Benutzer Daten ändern und die Änderungen wieder in der Datenbank persistent gespeichert. Obwohl Datasets eine sehr erfolgreiche Technologie erwiesen haben, wird empfohlen, dass neue .NET-Anwendungen Entity Framework verwenden. Entity Framework bietet eine natürliche Möglichkeit zum Arbeiten mit tabellarischen Daten als Object-Modelle, und es wurde eine einfachere Programmierschnittstelle.  
  
 Ein Datasetobjekt ist ein in-Memory-Objekt, das im Wesentlichen eine Mini-Datenbank ist. Es enthält DataTable, DataColumn und DataRow-Objekte, in denen Sie speichern und Ändern von Daten aus einer oder mehreren Datenbanken ohne eine offene Verbindung verwalten können. Das Dataset enthält Informationen über Änderungen an Daten, damit Updates nachverfolgt werden können, und wieder an die Datenbank gesendet werden, wenn Ihre Anwendung die Verbindung wiederhergestellt wird.  
  
 Datasets und verwandten Klassen werden im Namespace "System.Data" in der .NET Framework-Klassenbibliothek definiert. Sie können erstellen und Ändern von Datasets dynamisch im Code. Weitere Informationen hierzu finden Sie in ADO.NET. Die Dokumentation in diesem Abschnitt wird das Arbeiten mit Datasets mithilfe von Visual Studio-Designer veranschaulicht. Aufpassen kennen: Datasets, die über Designer vorgenommen werden TableAdapter-Objekte für die Interaktion mit der Datenbank verwenden, während Datasets, die programmgesteuert erfolgen DataAdapter-Objekten verwendet werden. Informationen zum programmgesteuerten Erstellen von Datasets finden Sie unter ["DataAdapters" und "DataReaders"](/dotnet/framework/data/adonet/dataadapters-and-datareaders).  
  
 Wenn Ihre Anwendung muss nur Daten aus einer Datenbank lesen und nicht ausgeführt werden, Updates, hinzufügt oder löscht, können Sie in der Regel eine bessere Leistung unter Verwendung eines DataReader-Objekts zum Abrufen von Daten in einer generischen Listenobjekt oder ein anderes Auflistungsobjekt abrufen. Wenn Sie die Daten anzeigen, können Sie Daten-Benutzeroberfläche auf die Auflistung binden.  
  
## <a name="dataset-workflow"></a>DataSet-workflow  
 Visual Studio enthält viele Tools zum Arbeiten mit Datasets zu vereinfachen. Das grundlegende End-to-End-Workflow wird:  
  
-   Verwenden der **Datenquelle** Fenster aus, um ein neues Dataset aus einem oder mehreren Datenquellen zu erstellen. Verwenden der **Dataset-Designer** , konfigurieren das Dataset und seine Eigenschaften festlegen. Beispielsweise müssen Sie angeben, Tabellen, zwischen denen aus der Datenquelle enthalten und welche Spalten aus jeder Tabelle. Wählen Sie sorgfältig, um die Menge an Arbeitsspeicher zu sparen, die das Dataset benötigen. Weitere Informationen finden Sie unter [Erstellen und Konfigurieren von Datasets in Visual Studio](../data-tools/create-and-configure-datasets-in-visual-studio.md).  
  
-   Geben Sie die Beziehungen zwischen den Tabellen, sodass Fremdschlüssel ordnungsgemäß behandelt werden. Weitere Informationen finden Sie unter [Datasets mit TableAdapters füllen](../data-tools/fill-datasets-by-using-tableadapters.md).  
  
-   Verwenden der **TableAdapter-Konfigurations-Assistenten** an der Abfrage oder gespeicherte Prozedur, die das Dataset zu füllen, wird und welche Datenbankvorgänge (Update, Delete usw.) zu implementieren. Weitere Informationen finden Sie in den folgenden Themen:  
  
    -   [Füllen von Datasets mit TableAdapters](../data-tools/fill-datasets-by-using-tableadapters.md)  
  
    -   [Bearbeiten von Daten in Datasets](../data-tools/edit-data-in-datasets.md)  
  
    -   [Überprüfen von Daten in Datasets](../data-tools/validate-data-in-datasets.md)  
  
    -   [Rückspeichern von Daten in der Datenbank](../data-tools/save-data-back-to-the-database.md)  
  
-   Fragen Sie ab, und suchen Sie die Daten im Dataset. Weitere Informationen finden Sie unter [Abfragedatasets](../data-tools/query-datasets.md). [!INCLUDE[linq_dataset](../data-tools/includes/linq_dataset_md.md)]ermöglicht [LINQ (Language-Integrated Query)](/dotnet/csharp/linq/) über Daten in einem <xref:System.Data.DataSet> Objekt. Weitere Informationen finden Sie unter [LINQ to DataSet](/dotnet/framework/data/adonet/linq-to-dataset).  
  
-   Verwenden der **Datenquellen** Fenster Benutzeroberflächen-Steuerelemente an das Dataset oder die einzelnen Spalten gebunden, und um anzugeben, welche Spalten Benutzer bearbeitet werden. Weitere Informationen finden Sie unter [Binden von Steuerelementen an Daten in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md).  
  
## <a name="datasets-and-n-tier-architecture"></a>Datasets und N-Tier-Architektur  
 Informationen über Datasets in N-Tier-Anwendungen finden Sie unter [arbeiten mit Datasets in n-Tier-Anwendungen](../data-tools/work-with-datasets-in-n-tier-applications.md).  
  
## <a name="datasets-and-xml"></a>Datasets und XML  
 Informationen zum Konvertieren von Datasets in und aus XML finden Sie unter [liest XML-Daten in ein Dataset](../data-tools/read-xml-data-into-a-dataset.md) und [ein Dataset als XML speichern](../data-tools/save-a-dataset-as-xml.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Visual Studio-Datentools für .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)