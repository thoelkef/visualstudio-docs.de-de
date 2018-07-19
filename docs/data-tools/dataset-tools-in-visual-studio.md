---
title: Datasettools in Visual Studio
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.data.DataSet
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
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 71e660260c6ec6dfd671d4b6b2d036ffd6cffb3a
ms.sourcegitcommit: 30f653d9625ba763f6b58f02fb74a24204d064ea
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/25/2018
ms.locfileid: "36756170"
---
# <a name="dataset-tools-in-visual-studio"></a>Datasettools in Visual Studio
> [!NOTE]
>  Datasets und verknüpften Klassen sind ältere Technologien von .NET aus den frühen 2000 s, mit denen Anwendungen arbeiten mit Daten im Arbeitsspeicher, während die Anwendungen aus der Datenbank getrennt werden. Sie sind besonders nützlich für Anwendungen, die Benutzern das Ändern von Daten und speichert die Änderungen in der Datenbank dauerhaft zu ermöglichen. Obwohl Datasets zu einer sehr erfolgreichen Technologie bewährt haben, empfehlen wir, neue Anwendungen für .NET zu Entity Framework verwenden. Entitätsframework bietet eine natürliche Möglichkeit zum Arbeiten mit tabellarischen Daten als Object-Modelle, und es hat es sich um eine einfachere Programmierschnittstelle.

 Ein `DataSet` Objekt ist ein in-Memory-Objekt, das im Wesentlichen eine Mini-Datenbank ist. Es enthält `DataTable`, `DataColumn`, und `DataRow` Objekte in der Sie speichern und Ändern von Daten aus einer oder mehreren Datenbanken ohne eine geöffnete Verbindung verwalten zu müssen. Das Dataset enthält Informationen zu Änderungen an Daten, damit Updates zurück an die Datenbank gesendet werden, wenn Ihre Anwendung die Verbindung wiederhergestellt wird und nachverfolgt werden können.

 Datasets und verknüpften Klassen sind in definiert die *"System.Data"* Namespace in der .NET Framework-Klassenbibliothek. Sie können erstellen und ändern die Datasets dynamisch im Code. Weitere Informationen zur Vorgehensweise, die ADO.NET finden Sie unter. Die Dokumentation in diesem Abschnitt wird das Arbeiten mit Datasets mithilfe von Visual Studio-Designer veranschaulicht. Dabei ist zu wissen: Datasets, die über Designer vorgenommen werden TableAdapter-Objekte verwenden, um mit der Datenbank zu interagieren. Dagegen verwenden Sie die Datasets, die programmgesteuert erfolgen `DataAdapter` Objekte. Informationen zum programmgesteuerten Erstellen von Datasets finden Sie unter ["DataAdapters" und "DataReaders"](/dotnet/framework/data/adonet/dataadapters-and-datareaders).

 Wenn Ihre Anwendung muss nur das Lesen von Daten aus einer Datenbank und nicht ausgeführt werden, Updates, hinzufügt oder löscht, in der Regel erhalten Sie eine bessere Leistung mit einem `DataReader` Objekt zum Abrufen von Daten in eine generische `List` Objekt oder ein anderes Auflistungsobjekt. Wenn Sie die Daten anzeigen, Sie können die Benutzeroberfläche der Auflistung Datenbindung.

## <a name="dataset-workflow"></a>DataSet-workflow
 Visual Studio bietet Tools zum Arbeiten mit Datasets zu vereinfachen. Der grundlegende Workflow für die End-to-End ist:

-   Verwenden der **Datenquelle** um ein neues Dataset aus einem oder mehreren Datenquellen zu erstellen. Verwenden der **Dataset-Designer** , konfigurieren das Dataset und seine Eigenschaften festlegen. Beispielsweise müssen Sie angeben, Tabellen, zwischen denen aus der Datenquelle eingeschlossen werden und welche Spalten aus jeder Tabelle. Wählen Sie sorgfältig, um die Menge an Arbeitsspeicher zu sparen, die das Dataset erforderlich sind. Weitere Informationen finden Sie unter [Erstellen und Konfigurieren von Datasets in Visual Studio](../data-tools/create-and-configure-datasets-in-visual-studio.md).

-   Geben Sie die Beziehungen zwischen den Tabellen, sodass Fremdschlüssel richtig behandelt werden. Weitere Informationen finden Sie unter [Füllen von Datasets mit TableAdapters](../data-tools/fill-datasets-by-using-tableadapters.md).

-   Verwenden der **TableAdapter-Konfigurations-Assistenten** an die Abfrage oder gespeicherte Prozedur, die das Dataset füllt und welche Datenbankvorgänge (Update, Delete usw.) zu implementieren. Weitere Informationen finden Sie in den folgenden Themen:

    -   [Füllen von Datasets mit TableAdapters](../data-tools/fill-datasets-by-using-tableadapters.md)

    -   [Bearbeiten von Daten in Datasets](../data-tools/edit-data-in-datasets.md)

    -   [Überprüfen von Daten in Datasets](../data-tools/validate-data-in-datasets.md)

    -   [Rückspeichern von Daten in der Datenbank](../data-tools/save-data-back-to-the-database.md)

-   Fragen Sie ab aus, und suchen Sie die Daten im Dataset. Weitere Informationen finden Sie unter [Abfragedatasets](../data-tools/query-datasets.md). [!INCLUDE[linq_dataset](../data-tools/includes/linq_dataset_md.md)] ermöglicht [LINQ (Language-Integrated Query)](/dotnet/csharp/linq/) für Daten in einem <xref:System.Data.DataSet> Objekt. Weitere Informationen finden Sie unter [LINQ to DataSet](/dotnet/framework/data/adonet/linq-to-dataset).

-   Verwenden der **Datenquellen** Fenster, um Benutzeroberflächen-Steuerelemente an das Dataset oder einzelne Spalten binden und angeben, welche Spalten Benutzer bearbeitet werden. Weitere Informationen finden Sie unter [Binden von Steuerelementen an Daten in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md).

## <a name="datasets-and-n-tier-architecture"></a>Datasets und N-schichtige Architektur
 Weitere Informationen zu Datasets in N-Tier-Anwendungen finden Sie unter [arbeiten mit Datasets in n-schichtigen Anwendungen](../data-tools/work-with-datasets-in-n-tier-applications.md).

## <a name="datasets-and-xml"></a>Datasets und XML
 Informationen zum Konvertieren von Datasets in und aus XML finden Sie unter [liest XML-Daten in ein Dataset](../data-tools/read-xml-data-into-a-dataset.md) und [Speichern eines Datasets als XML](../data-tools/save-a-dataset-as-xml.md).

## <a name="see-also"></a>Siehe auch

- [Visual Studio-Datentools für .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)