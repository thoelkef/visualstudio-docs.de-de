---
title: Datasettools
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
f1_keywords:
- vs.data.DataSet
dev_langs:
- VB
- CSharp
- C++
- aspx
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
caps.latest.revision: 53
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: df415b9ad56e8e9b740da57709d039737f1bd24a
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/15/2019
ms.locfileid: "65697906"
---
# <a name="dataset-tools-in-visual-studio"></a>Datasettools in Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

HINWEIS]
> Datasets und verknüpften Klassen sind ältere Technologien von .NET aus den frühen 2000 s, mit denen Anwendungen arbeiten mit Daten im Arbeitsspeicher, während die Anwendungen aus der Datenbank getrennt werden. Sie sind besonders nützlich für Anwendungen, die Benutzern das Ändern von Daten und speichert die Änderungen in der Datenbank dauerhaft zu ermöglichen. Obwohl Datasets zu einer sehr erfolgreichen Technologie bewährt haben, empfehlen wir, neue Anwendungen für .NET zu Entity Framework verwenden. Entitätsframework bietet eine natürliche Möglichkeit zum Arbeiten mit tabellarischen Daten als Object-Modelle, und es hat es sich um eine einfachere Programmierschnittstelle.

 Ein DataSet-Objekt ist ein in-Memory-Objekt, das im Wesentlichen eine Mini-Datenbank ist. Sie enthält DataTable DataColumn und DataRow-Objekte, in denen Sie speichern und Ändern von Daten aus einer oder mehreren Datenbanken ohne eine geöffnete Verbindung verwalten zu müssen. Das Dataset enthält Informationen zu Änderungen an Daten, damit Updates zurück an die Datenbank gesendet werden, wenn Ihre Anwendung die Verbindung wiederhergestellt wird und nachverfolgt werden können.

 Datasets und verknüpften Klassen werden in der System.Data-Namespace in der .NET Framework-Klassenbibliothek definiert. Sie können erstellen und ändern die Datasets dynamisch im Code. Weitere Informationen zur Vorgehensweise, die ADO.NET finden Sie unter. Die Dokumentation in diesem Abschnitt wird das Arbeiten mit Datasets mithilfe von Visual Studio-Designer veranschaulicht. Dabei ist zu wissen: Datasets, die über Designer vorgenommen werden TableAdapter-Objekte für die Interaktion mit der Datenbank verwenden, während der Datasets, die programmgesteuert erfolgen DataAdapter-Objekte verwenden. Informationen zum programmgesteuerten Erstellen von Datasets finden Sie unter ["DataAdapters" und "DataReaders"](https://msdn.microsoft.com/library/cc952ca2-ec19-46ab-9189-15174b52cb74).

 Wenn Ihre Anwendung muss nur das Lesen von Daten aus einer Datenbank und nicht ausgeführt werden, Updates, hinzufügt oder löscht, können Sie in der Regel eine bessere Leistung mit einem DataReader-Objekt zum Abrufen von Daten in einer generischen List-Objekt oder ein anderes Auflistungsobjekt abrufen. Wenn Sie die Daten anzeigen, Sie können die Benutzeroberfläche der Auflistung Datenbindung.

## <a name="dataset-workflow"></a>DataSet-workflow
 Visual Studio bietet zahlreiche Tools zum Arbeiten mit Datasets zu vereinfachen. Der grundlegende Workflow für die End-to-End ist:

- Verwenden der **Datenquelle** um ein neues Dataset aus einem oder mehreren Datenquellen zu erstellen. Verwenden der **Dataset-Designer** , konfigurieren das Dataset und seine Eigenschaften festlegen. Beispielsweise müssen Sie angeben, Tabellen, zwischen denen aus der Datenquelle eingeschlossen werden und welche Spalten aus jeder Tabelle. Wählen Sie sorgfältig, um die Menge an Arbeitsspeicher zu sparen, die das Dataset benötigen. Weitere Informationen finden Sie unter [Erstellen und Konfigurieren von Datasets in Visual Studio](../data-tools/create-and-configure-datasets-in-visual-studio.md).

- Geben Sie die Beziehungen zwischen den Tabellen, sodass Fremdschlüssel richtig behandelt werden. Weitere Informationen finden Sie unter [Füllen von Datasets mit TableAdapters](../data-tools/fill-datasets-by-using-tableadapters.md).

- Verwenden der **TableAdapter-Konfigurations-Assistenten** an die Abfrage oder gespeicherte Prozedur, mit denen das Dataset aufgefüllt wird und welche Datenbankvorgänge (Update, Delete usw.) zu implementieren. Weitere Informationen finden Sie in den folgenden Themen:

    - [Füllen von Datasets mit TableAdapters](../data-tools/fill-datasets-by-using-tableadapters.md)

    - [Bearbeiten von Daten in Datasets](../data-tools/edit-data-in-datasets.md)

    - [Überprüfen von Daten in Datasets](../data-tools/validate-data-in-datasets.md)

    - [Rückspeichern von Daten in der Datenbank](../data-tools/save-data-back-to-the-database.md)

- Fragen Sie ab aus, und suchen Sie die Daten im Dataset. Weitere Informationen finden Sie unter [Abfragedatasets](../data-tools/query-datasets.md). [!INCLUDE[linq_dataset](../includes/linq-dataset-md.md)] ermöglicht [LINQ (Language-Integrated Query)](https://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d) für Daten in einem <xref:System.Data.DataSet> Objekt. Weitere Informationen finden Sie unter [LINQ to DataSet](https://msdn.microsoft.com/library/743e3755-3ecb-45a2-8d9b-9ed41f0dcf17).

- Verwenden der **Datenquellen** Fenster, um Benutzeroberflächen-Steuerelemente an das Dataset oder einzelne Spalten binden und angeben, welche Spalten Benutzer bearbeitet werden. Weitere Informationen finden Sie unter [Binden von Steuerelementen an Daten in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md).

## <a name="datasets-and-n-tier-architecture"></a>Datasets und N-schichtige Architektur
 Weitere Informationen zu Datasets in N-Tier-Anwendungen finden Sie unter [arbeiten mit Datasets in n-schichtigen Anwendungen](../data-tools/work-with-datasets-in-n-tier-applications.md).

## <a name="datasets-and-xml"></a>Datasets und XML
 Informationen zum Konvertieren von Datasets in und aus XML finden Sie unter [liest XML-Daten in ein Dataset](../data-tools/read-xml-data-into-a-dataset.md) und [Speichern eines Datasets als XML](../data-tools/save-a-dataset-as-xml.md).

## <a name="see-also"></a>Siehe auch
 [Visual Studio-Datentools für .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)
