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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 38239bd431f3e66e1a694361f3727c843fbf29d3
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62558462"
---
# <a name="work-with-datasets-in-n-tier-applications"></a>Arbeiten mit Datasets in N-Tier-Anwendungen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Daten für N-schichtige Anwendungen * sind datenorientierte Anwendungen, die in mehrere logische Ebenen voneinander getrennt sind (oder *Ebenen*). Anders ausgedrückt: Eine N-Tier-Datenanwendung ist eine Anwendung, die in mehrere Projekte unterteilt ist mit der Datenzugriffsebene, Geschäftslogikebene und der Präsentationsebene jeweils als eigenes Projekt. Weitere Informationen finden Sie unter [Übersicht über N-Tier-Datenanwendungen](../data-tools/n-tier-data-applications-overview.md).  
  
 Typisierte DataSets wurden weiterentwickelt, damit die TableAdapters-Klasse und die DataSet-Klasse in gesonderten Projekten generiert werden können. Damit ist es möglich, Anwendungsebenen schnell zu trennen und N-Tier-Datenanwendung zu erstellen.  
  
 N-Tier-Unterstützung in typisierten Datasets ermöglicht die iterative Entwicklung der Anwendungsarchitektur zu einem n-Tier-Design. Es entfernt auch die Anforderung, den Code manuell in mehr als ein Projekt zu trennen. Beginnen Sie mit dem Design der Datenschicht unter Verwendung der Dataset-Designer. Wenn Sie soweit sind, dass Sie die Anwendungsarchitektur in ein n-schichtiges Design übernehmen können, legen Sie die Eigenschaft **DataSet-Projekt** eines Datasets so fest, dass die Dataset-Klasse in einem separaten Projekt erstellt wird.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Gewusst wie: DataSets und TableAdapters in verschiedene Projekte aufteilen](../data-tools/separate-datasets-and-tableadapters-into-different-projects.md)  
 Beschreibt, wie die erstellte Dataset-Klasse aus dem Projekt, das die generierten TableAdapter-Klassen enthält, in ein neues bewegt wird.  
  
 [Gewusst wie: Hinzufügen von Code zu TableAdapters in N-Tier-Anwendungen](../data-tools/add-code-to-tableadapters-in-n-tier-applications.md)  
 Beschreibt, wie eine partielle Klasse generiert wird, in der Code für einen N-Tier-TableAdapter hinzugefügt werden kann.  
  
 [Gewusst wie: Hinzufügen von Code zu DataSets in N-Tier-Anwendungen](../data-tools/add-code-to-datasets-in-n-tier-applications.md)  
 Beschreibt, wie eine partielle Klasse generiert wird, in der Code für ein N-Tier-Dataset hinzugefügt werden kann.  
  
 [Hinzufügen von Validierungen zu einem N-Tier-Dataset](../data-tools/add-validation-to-an-n-tier-dataset.md)  
 Beschreibt, wo Code für das Durchführen der Validierung bei Datenänderungen hinzugefügt wird.  
  
 [Exemplarische Vorgehensweise: Erstellen einer n-schichtigen Datenanwendung](../data-tools/walkthrough-creating-an-n-tier-data-application.md)  
 Liefert eine Schritt-für-Schritt-Anleitung für das Erstellen eines typisierten Datasets und das Aufteilen des Codes für TableAdapter und Dataset in mehrere Projekte.  
  
 [Exemplarische Vorgehensweise: Hinzufügen einer Validierung zu einer N-Tier-Datenanwendung](http://msdn.microsoft.com/library/b35d072c-31f0-49ba-a225-69177592c265)  
 Enthält detaillierte Anweisungen zum Hinzufügen von Validierungen für die Anwendung, die in der exemplarischen Vorgehensweise Daten der n-Tier-Anwendung erstellt wurde.  
  
## <a name="reference"></a>Referenz  
 <xref:System.Data.DataSet>  
  
 <xref:System.Data.TypedTableBase%601>  
  
## <a name="related-sections"></a>Verwandte Abschnitte

- [Übersicht über N-Tier-Datenanwendungen](../data-tools/n-tier-data-applications-overview.md)   
- [Hierarchische Aktualisierung](../data-tools/hierarchical-update.md)   
- [Datasettools in Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)   
- [Zugreifen auf Daten in Visual Studio](../data-tools/accessing-data-in-visual-studio.md)   
- [N-schichtige Anwendungen und Remoteanwendungen mit LINQ to SQL](http://msdn.microsoft.com/library/854a1cdd-53cb-45f5-83ca-63962a9b3598)