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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 23e4deba53288383a569f6da6e14d27f723825ee
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72657382"
---
# <a name="dataset-tools-in-visual-studio"></a>Datasettools in Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

HINWEIS]
> Bei Datasets und verknüpften Klassen handelt es sich um Legacy-.NET-Technologien aus den frühen 2000er-Jahren, mit denen Anwendungen mit Daten im Arbeitsspeicher arbeiten können, während die Anwendungen von der Datenbank getrennt werden Sie sind besonders nützlich für Anwendungen, die es Benutzern ermöglichen, Daten zu ändern und die Änderungen wieder in der Datenbank zu speichern. Obwohl es sich bei Datasets um eine sehr erfolgreiche Technologie handelt, empfiehlt es sich, dass neue .NET-Anwendungen Entity Framework verwenden. Entity Framework bietet eine natürlichere Möglichkeit zum Arbeiten mit tabellarischen Daten als Objekt Modelle und verfügt über eine einfachere Programmierschnittstelle.

 Ein DataSet-Objekt ist ein in-Memory-Objekt, das im Wesentlichen eine Mini Datenbank ist. Sie enthält Datentabelle, datacolenn und DataRow-Objekte, in denen Sie Daten aus einer oder mehreren Datenbanken speichern und ändern können, ohne dass eine offene Verbindung aufrechterhalten werden muss. Das Dataset verwaltet Informationen zu Änderungen an den Daten, sodass Updates nachverfolgt und zurück an die Datenbank gesendet werden können, wenn die Anwendung wieder verbunden wird.

 Datasets und zugehörige Klassen werden im System. Data-Namespace in der .NET Framework-Klassenbibliothek definiert. Sie können Datasets dynamisch im Code erstellen und ändern. Weitere Informationen hierzu finden Sie unter ADO.net. In der Dokumentation in diesem Abschnitt wird gezeigt, wie mit Datasets mithilfe von Visual Studio-Designern gearbeitet wird. Ein wichtiger Punkt: Datasets, die über Designer erstellt werden, verwenden TableAdapter-Objekte, um mit der Datenbank zu interagieren, während Datasets, die Programm gesteuert DataAdapter-Objekte verwenden, verwendet werden. Informationen zum programmgesteuerten Erstellen von Datasets finden Sie unter [DataAdapters und DataReaders](https://msdn.microsoft.com/library/cc952ca2-ec19-46ab-9189-15174b52cb74).

 Wenn Ihre Anwendung nur Daten aus einer Datenbank lesen und keine Updates, Hinzufügungen oder Löschungen ausführen muss, können Sie in der Regel eine bessere Leistung erzielen, indem Sie ein DataReader-Objekt verwenden, um Daten in einem generischen Listen Objekt oder einem anderen Sammlungsobjekt abzurufen. Wenn Sie die Daten anzeigen, können Sie die Benutzeroberfläche an die Sammlung binden.

## <a name="dataset-workflow"></a>DataSet-Workflow
 Visual Studio bietet eine Vielzahl von Tools, um die Arbeit mit Datasets zu vereinfachen. Der grundlegende End-to-End-Workflow lautet wie folgt:

- Verwenden Sie das Fenster **Datenquelle** , um ein neues Dataset aus einer oder mehreren Datenquellen zu erstellen. Verwenden Sie die **DataSet-Designer** , um das DataSet zu konfigurieren und seine Eigenschaften festzulegen. Beispielsweise müssen Sie angeben, welche Tabellen aus der Datenquelle eingeschlossen werden sollen und welche Spalten aus jeder Tabelle enthalten sein sollen. Wählen Sie sorgfältig aus, um die Menge an Arbeitsspeicher zu sparen, die für das DataSet erforderlich ist. Weitere Informationen finden Sie unter [Erstellen und Konfigurieren von Datasets in Visual Studio](../data-tools/create-and-configure-datasets-in-visual-studio.md).

- Geben Sie die Beziehungen zwischen den Tabellen an, sodass Fremdschlüssel ordnungsgemäß verarbeitet werden. Weitere Informationen finden Sie unter [Füllen von Datasets mit TableAdapters](../data-tools/fill-datasets-by-using-tableadapters.md).

- Verwenden Sie den **TableAdapter-Konfigurations-Assistenten** , um die Abfrage oder die gespeicherte Prozedur anzugeben, die das DataSet auffüllen und welche Daten Bank Vorgänge (aktualisieren, löschen usw.) implementiert werden. Weitere Informationen finden Sie in den folgenden Themen:

  - [Füllen von Datasets mit TableAdapters](../data-tools/fill-datasets-by-using-tableadapters.md)

  - [Bearbeiten von Daten in Datasets](../data-tools/edit-data-in-datasets.md)

  - [Überprüfen von Daten in Datasets](../data-tools/validate-data-in-datasets.md)

  - [Rückspeichern von Daten in der Datenbank](../data-tools/save-data-back-to-the-database.md)

- Abfragen und Durchsuchen der Daten im DataSet. Weitere Informationen finden Sie unter [Abfragen von Datasets](../data-tools/query-datasets.md). [!INCLUDE[linq_dataset](../includes/linq-dataset-md.md)] aktiviert [LINQ (Language-Integrated Query)](https://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d) über Daten in einem <xref:System.Data.DataSet>-Objekt. Weitere Informationen finden Sie unter [LINQ to DataSet](https://msdn.microsoft.com/library/743e3755-3ecb-45a2-8d9b-9ed41f0dcf17).

- Verwenden Sie das Fenster **Datenquellen** , um Steuerelemente der Benutzeroberfläche an das DataSet oder die einzelnen Spalten zu binden und um anzugeben, welche Spalten vom Benutzer bearbeitet werden können. Weitere Informationen finden Sie unter [Binden von Steuerelementen an Daten in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md).

## <a name="datasets-and-n-tier-architecture"></a>Datasets und N-Tier-Architektur
 Informationen zu Datasets in n-Tier-Anwendungen finden Sie unter [Arbeiten mit Datasets in n-Tier-Anwendungen](../data-tools/work-with-datasets-in-n-tier-applications.md).

## <a name="datasets-and-xml"></a>Datasets und XML
 Informationen zum Umstellen von Datasets in und aus XML finden [Sie unter Lesen von XML-Daten in ein DataSet](../data-tools/read-xml-data-into-a-dataset.md) und [Speichern eines Datasets als XML](../data-tools/save-a-dataset-as-xml.md).

## <a name="see-also"></a>Siehe auch
 [Visual Studio-Datentools für .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)
