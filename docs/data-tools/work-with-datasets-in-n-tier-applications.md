---
title: Arbeiten mit Datasets in n-Tier-Anwendungen | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "22"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.openlocfilehash: 85062fe6ea82a73fbc2d64e1d1ce9136d16831cf
ms.sourcegitcommit: ee42a8771f0248db93fd2e017a22e2506e0f9404
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/09/2017
---
# <a name="work-with-datasets-in-n-tier-applications"></a>Arbeiten Sie mit Datasets in n-Tier-Anwendungen
*N-Tier-datenanwendungen* sind datenorientierte Anwendungen, die in mehrere logische Ebenen aufgeteilt sind (oder *Ebenen*). Anders ausgedrückt: Eine N-Tier-Datenanwendung ist eine Anwendung, die in mehrere Projekte unterteilt ist mit der Datenzugriffsebene, Geschäftslogikebene und der Präsentationsebene jeweils als eigenes Projekt. Weitere Informationen finden Sie unter [Übersicht über N-Tier Applications](../data-tools/n-tier-data-applications-overview.md).  
  
Typisierte DataSets wurden weiterentwickelt, damit die TableAdapters-Klasse und die DataSet-Klasse in gesonderten Projekten generiert werden können. Damit ist es möglich, Anwendungsebenen schnell zu trennen und N-Tier-Datenanwendung zu erstellen.  
  
N-Tier-Unterstützung in typisierten Datasets ermöglicht die iterative Entwicklung der Anwendungsarchitektur zu einem n-Tier-Design. Es entfernt auch die Anforderung, den Code manuell in mehr als ein Projekt zu trennen. Beginnen Sie mit dem Entwerfen der Datenschicht mithilfe der **Dataset-Designer**. Wenn Sie bereit sind, die Anwendungsarchitektur zu einem n-Tier-Design übernehmen, legen Sie die **DataSet-Projekt** Eigenschaft von einem Dataset, um die Dataset-Klasse in einem separaten Projekt generieren.  
  
## <a name="reference"></a>Verweis  
<xref:System.Data.DataSet>  
<xref:System.Data.TypedTableBase%601>  
  
## <a name="see-also"></a>Siehe auch
[Übersicht über N-Tier-Datenanwendungen](../data-tools/n-tier-data-applications-overview.md)  
[Exemplarische Vorgehensweise: Erstellen einer N-Tier-Datenanwendung](../data-tools/walkthrough-creating-an-n-tier-data-application.md)  
[Gewusst wie: Hinzufügen von Code zu TableAdapters in N-Tier-Anwendungen](../data-tools/add-code-to-tableadapters-in-n-tier-applications.md)  
[Gewusst wie: Hinzufügen von Code zu DataSets in N-Tier-Anwendungen](../data-tools/add-code-to-datasets-in-n-tier-applications.md)  
[Hinzufügen von Validierungen zu einem N-Tier-Dataset](../data-tools/add-validation-to-an-n-tier-dataset.md)  
[Gewusst wie: DataSets und TableAdapters in verschiedene Projekte aufteilen](../data-tools/separate-datasets-and-tableadapters-into-different-projects.md)  
[Hierarchische Aktualisierung](../data-tools/hierarchical-update.md)  
[Datasettools in Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)  
[Zugreifen auf Daten in Visual Studio](../data-tools/accessing-data-in-visual-studio.md)  
[Erstellen und Konfigurieren von TableAdapters](../data-tools/create-and-configure-tableadapters.md)  
[N-schichtige und Remoteanwendungen mit LINQ to SQL](http://msdn.microsoft.com/Library/854a1cdd-53cb-45f5-83ca-63962a9b3598)