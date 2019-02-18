---
title: Arbeiten mit Datasets in N-Tier-Anwendungen
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- datasets [Visual Basic], n-tier applications
- multi-tier database applications
- DataSet project [VS n-tier applications]
- distributed applications [VS n-tier applications]
- data [Visual Basic], n-tier applications
- TableAdapters, n-tier applications
- n-tier applications
- tiers, n-tier applications
- typed datasets, n-tier applications
- multiple tier applications
ms.assetid: f6ae2ee0-ea5f-4a79-8f4b-e21c115afb20
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: c6da3f51a249aaf52cf3f20b90f3add6ceeb7aa1
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2019
ms.locfileid: "55936550"
---
# <a name="work-with-datasets-in-n-tier-applications"></a>Arbeiten mit Datasets in N-Tier-Anwendungen

*N-schichtige Datenanwendungen* sind datenorientierte Anwendungen, die in mehrere logische *Schichten* unterteilt sind. Anders ausgedrückt: Eine N-Tier-Datenanwendung ist eine Anwendung, die in mehrere Projekte unterteilt ist mit der Datenzugriffsebene, Geschäftslogikebene und der Präsentationsebene jeweils als eigenes Projekt. Weitere Informationen finden Sie unter [Übersicht über N-Tier-datenanwendungen](../data-tools/n-tier-data-applications-overview.md).

Typisierte DataSets wurden weiterentwickelt, damit die TableAdapters-Klasse und die DataSet-Klasse in gesonderten Projekten generiert werden können. Damit ist es möglich, Anwendungsebenen schnell zu trennen und N-Tier-Datenanwendung zu erstellen.

N-Tier-Unterstützung in typisierten Datasets ermöglicht die iterative Entwicklung der Anwendungsarchitektur zu einem n-Tier-Design. Es entfernt auch die Anforderung, den Code manuell in mehr als ein Projekt zu trennen. Beginnen Sie mit dem Design der Datenschicht unter Verwendung der **Dataset-Designer**. Wenn Sie soweit sind, dass Sie die Anwendungsarchitektur in ein n-schichtiges Design übernehmen können, legen Sie die Eigenschaft **DataSet-Projekt** eines Datasets so fest, dass die Dataset-Klasse in einem separaten Projekt erstellt wird.

## <a name="reference"></a>Referenz

- <xref:System.Data.DataSet>
- <xref:System.Data.TypedTableBase%601>

## <a name="see-also"></a>Siehe auch

- [Übersicht über n-schichtige Datenanwendungen](../data-tools/n-tier-data-applications-overview.md)
- [Exemplarische Vorgehensweise: Erstellen einer n-schichtigen Datenanwendung](../data-tools/walkthrough-creating-an-n-tier-data-application.md)
- [Gewusst wie: Hinzufügen von Code zu TableAdapters in N-Tier-Anwendungen](../data-tools/add-code-to-tableadapters-in-n-tier-applications.md)
- [Gewusst wie: Hinzufügen von Code zu DataSets in N-Tier-Anwendungen](../data-tools/add-code-to-datasets-in-n-tier-applications.md)
- [Hinzufügen von Validierungen zu einem N-Tier-Dataset](../data-tools/add-validation-to-an-n-tier-dataset.md)
- [Gewusst wie: DataSets und TableAdapters in verschiedene Projekte aufteilen](../data-tools/separate-datasets-and-tableadapters-into-different-projects.md)
- [Hierarchische Aktualisierung](../data-tools/hierarchical-update.md)
- [Datasettools in Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)
- [Zugreifen auf Daten in Visual Studio](../data-tools/accessing-data-in-visual-studio.md)
- [Erstellen und Konfigurieren eines TableAdapters](../data-tools/create-and-configure-tableadapters.md)
- [N-schichtige Anwendungen und Remoteanwendungen mit LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/n-tier-and-remote-applications-with-linq-to-sql)