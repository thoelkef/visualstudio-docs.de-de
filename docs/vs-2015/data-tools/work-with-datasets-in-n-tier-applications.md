---
title: Arbeiten mit Datasets in n-Tier-Anwendungen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
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
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 61f3686488a460ef4c7091521c2165f575e76fa6
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47520526"
---
# <a name="work-with-datasets-in-n-tier-applications"></a>Arbeiten mit Datasets in N-Tier-Anwendungen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [arbeiten mit Datasets in n-schichtigen Anwendungen](https://docs.microsoft.com/visualstudio/data-tools/work-with-datasets-in-n-tier-applications).  
  
  
Daten für N-schichtige Anwendungen * sind datenorientierte Anwendungen, die in mehrere logische Ebenen voneinander getrennt sind (oder *Ebenen*). Anders ausgedrückt: Eine N-Tier-Datenanwendung ist eine Anwendung, die in mehrere Projekte unterteilt ist mit der Datenzugriffsebene, Geschäftslogikebene und der Präsentationsebene jeweils als eigenes Projekt. Weitere Informationen finden Sie unter [Übersicht über N-Tier-Datenanwendungen](../data-tools/n-tier-data-applications-overview.md).  
  
 Typisierte DataSets wurden weiterentwickelt, damit die TableAdapters-Klasse und die DataSet-Klasse in gesonderten Projekten generiert werden können. Damit ist es möglich, Anwendungsebenen schnell zu trennen und N-Tier-Datenanwendung zu erstellen.  
  
 N-Tier-Unterstützung in typisierten Datasets ermöglicht die iterative Entwicklung der Anwendungsarchitektur zu einem n-Tier-Design. Es entfernt auch die Anforderung, den Code manuell in mehr als ein Projekt zu trennen. Beginnen Sie mit dem Design der Datenschicht unter Verwendung der [erstellen und Bearbeiten typisierter Datasets](../data-tools/creating-and-editing-typed-datasets.md). Wenn Sie die Anwendungsarchitektur zu einem n-Tier-Design zu entwickeln möchten, legen die **DataSet-Projekt** Eigenschaft von einem Dataset, um die Dataset-Klasse in einem separaten Projekt generieren.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Gewusst wie: DataSets und TableAdapters in verschiedene Projekte aufteilen](../data-tools/separate-datasets-and-tableadapters-into-different-projects.md)  
 Beschreibt, wie die erstellte Dataset-Klasse aus dem Projekt, das die generierten TableAdapter-Klassen enthält, in ein neues bewegt wird.  
  
 [Gewusst wie: Hinzufügen von Code zu TableAdapters in N-Tier-Anwendungen](../data-tools/add-code-to-tableadapters-in-n-tier-applications.md)  
 Beschreibt, wie eine partielle Klasse generiert wird, in der Code für einen N-Tier-TableAdapter hinzugefügt werden kann.  
  
 [Gewusst wie: Hinzufügen von Code zu DataSets in N-Tier-Anwendungen](../data-tools/add-code-to-datasets-in-n-tier-applications.md)  
 Beschreibt, wie eine partielle Klasse generiert wird, in der Code für ein N-Tier-Dataset hinzugefügt werden kann.  
  
 [Hinzufügen von Validierungen zu einem N-Tier-Dataset](../data-tools/add-validation-to-an-n-tier-dataset.md)  
 Beschreibt, wo Code für das Durchführen der Validierung bei Datenänderungen hinzugefügt wird.  
  
 [Exemplarische Vorgehensweise: Erstellen einer N-Tier-Datenanwendung](../data-tools/walkthrough-creating-an-n-tier-data-application.md)  
 Liefert eine Schritt-für-Schritt-Anleitung für das Erstellen eines typisierten Datasets und das Aufteilen des Codes für TableAdapter und Dataset in mehrere Projekte.  
  
 [Exemplarische Vorgehensweise: Hinzufügen einer Validierung zu einer N-Tier-Datenanwendung](http://msdn.microsoft.com/library/b35d072c-31f0-49ba-a225-69177592c265)  
 Enthält detaillierte Anweisungen zum Hinzufügen von Validierungen für die Anwendung, die in der exemplarischen Vorgehensweise Daten der n-Tier-Anwendung erstellt wurde.  
  
## <a name="reference"></a>Referenz  
 <xref:System.Data.DataSet>  
  
 <xref:System.Data.TypedTableBase%601>  
  
## <a name="related-sections"></a>Verwandte Abschnitte  
 [Übersicht über N-Tier-Datenanwendungen](../data-tools/n-tier-data-applications-overview.md)  
  
 [Hierarchische Aktualisierung](../data-tools/hierarchical-update.md)  
  
 [Datasettools in Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)  
  
 [Zugreifen auf Daten in Visual Studio](../data-tools/accessing-data-in-visual-studio.md)  
  
 [Übersicht über TableAdapters](../data-tools/tableadapter-overview.md)  
  
 [N-schichtige Anwendungen und Remoteanwendungen mit LINQ to SQL](http://msdn.microsoft.com/library/854a1cdd-53cb-45f5-83ca-63962a9b3598)

