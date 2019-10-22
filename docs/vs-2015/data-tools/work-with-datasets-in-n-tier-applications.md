---
title: Arbeiten mit Datasets in n-Tier-Anwendungen | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
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
caps.latest.revision: 25
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 4f7be307ec94b15871da20ace8055fc7121d5d92
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72657817"
---
# <a name="work-with-datasets-in-n-tier-applications"></a>Arbeiten mit Datasets in N-Tier-Anwendungen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

N-Tier-Daten Anwendungen * sind datenzentrierte Anwendungen, die in mehrere logische Ebenen (oder *Ebenen*) aufgeteilt sind. Anders ausgedrückt: Eine N-Tier-Datenanwendung ist eine Anwendung, die in mehrere Projekte unterteilt ist mit der Datenzugriffsebene, Geschäftslogikebene und der Präsentationsebene jeweils als eigenes Projekt. Weitere Informationen finden Sie unter [Übersicht über N-Tier-Daten Anwendungen](../data-tools/n-tier-data-applications-overview.md).

 Typisierte DataSets wurden weiterentwickelt, damit die TableAdapters-Klasse und die DataSet-Klasse in gesonderten Projekten generiert werden können. Damit ist es möglich, Anwendungsebenen schnell zu trennen und N-Tier-Datenanwendung zu erstellen.

 Die n-Tier-Unterstützung in typisierten Datasets ermöglicht die iterative Entwicklung der Anwendungsarchitektur zu einem n-Tier-Design. Außerdem entfällt die Anforderung, den Code manuell in mehr als ein Projekt zu trennen. Beginnen Sie mit dem Entwerfen der Datenschicht, indem Sie die DataSet-Designer verwenden. Wenn Sie soweit sind, dass Sie die Anwendungsarchitektur in ein n-schichtiges Design übernehmen können, legen Sie die Eigenschaft **DataSet-Projekt** eines Datasets so fest, dass die Dataset-Klasse in einem separaten Projekt erstellt wird.

## <a name="in-this-section"></a>In diesem Abschnitt
 [Trennen von Datasets und TableAdapters in verschiedene Projekte](../data-tools/separate-datasets-and-tableadapters-into-different-projects.md) Beschreibt, wie die generierte Dataset-Klasse aus dem Projekt, das die generierten TableAdapter-Klassen enthält, und in ein neues Projekt verschoben werden.

 [Hinzufügen von Code zu TableAdapters in n-Tier-Anwendungen](../data-tools/add-code-to-tableadapters-in-n-tier-applications.md) Beschreibt, wie eine partielle Klasse generiert wird, in der Code für einen n-Tier-TableAdapter hinzugefügt werden kann.

 [Hinzufügen von Code zu Datasets in n-Tier-Anwendungen](../data-tools/add-code-to-datasets-in-n-tier-applications.md) Beschreibt, wie eine partielle Klasse generiert wird, in der Code für ein n-Tier-DataSet hinzugefügt werden kann.

 [Hinzufügen von Validierungen zu einem n-Tier-DataSet](../data-tools/add-validation-to-an-n-tier-dataset.md) Beschreibt das Hinzufügen von Code zum Ausführen von Validierungen für das Ändern von Daten.

 Exemplarische Vorgehensweise [: Erstellen einer N-Tier-Daten Anwendung](../data-tools/walkthrough-creating-an-n-tier-data-application.md) Enthält Schritt-für-Schritt-Anleitungen zum Erstellen eines typisierten Datasets und zum Trennen des TableAdapter-und datasetcodes in mehrere Projekte.

 Exemplarische Vorgehensweise [: Hinzufügen von Validierungen zu einer N-Tier-Daten Anwendung](https://msdn.microsoft.com/library/b35d072c-31f0-49ba-a225-69177592c265) Enthält Schritt-für-Schritt-Anleitungen zum Hinzufügen von Validierungen zu der Anwendung, die in der exemplarischen Vorgehensweise der n-Tier-Daten Anwendung erstellt wurde.

## <a name="reference"></a>Referenz
 <xref:System.Data.DataSet>

 <xref:System.Data.TypedTableBase%601>

## <a name="related-sections"></a>Verwandte Abschnitte

- [Übersicht über N-Tier-Datenanwendungen](../data-tools/n-tier-data-applications-overview.md)
- [Hierarchische Aktualisierung](../data-tools/hierarchical-update.md)
- [Datasettools in Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)
- [Zugreifen auf Daten in Visual Studio](../data-tools/accessing-data-in-visual-studio.md)
- [N-schichtige Anwendungen und Remoteanwendungen mit LINQ to SQL](https://msdn.microsoft.com/library/854a1cdd-53cb-45f5-83ca-63962a9b3598)