---
title: Übersicht über N-Tier-Daten Anwendungen | Microsoft-Dokumentation
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
- presentation tier
- middle tier
- data tier
- n-tier applications, about n-tier applications
ms.assetid: 1020581d-eaaa-41a2-aca4-bf4c212895f6
caps.latest.revision: 29
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 7c8e0b0eb1c1016ac8e5351ff55df23b44d26824
ms.sourcegitcommit: a3edc753c951f317b67ce294cd2fc74f0c45390c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/03/2020
ms.locfileid: "89426706"
---
# <a name="n-tier-data-applications-overview"></a>Übersicht über N-Tier-Datenanwendungen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

*N-Tier-* Daten Anwendungen sind Daten Anwendungen, die in mehrere *Ebenen*aufgeteilt sind. Sie werden auch "verteilte Anwendungen" oder "Anwendungen mit mehreren Ebenen" genannt, da die Verarbeitung auf voneinander unabhängige, auf Client und Server verteilte Ebenen aufgeteilt wird. Beim Entwickeln einer Anwendung, die auf Daten zugreift, sollten die verschiedenen Ebenen, aus denen die Anwendung besteht, klar getrennt sein.

 Eine typische N-Tier-Anwendung besteht aus einer Präsentationsschicht, einer mittleren Ebene und einer Datenschicht. Die einfachste Möglichkeit zum Trennen der verschiedenen Ebenen einer N-Tier-Anwendung besteht im Erstellen separater Projekte für jede Ebene, die in der Anwendung enthalten sein soll. Beispielsweise könnte die Präsentationsebene eine Windows Forms-Anwendung sein, während die Datenzugriffslogik eine in der mittleren Ebene angesiedelte Klassenbibliothek ist. Weiterhin könnte die Präsentationslogik in der mittleren Ebene über einen Dienst mit der Datenzugriffsebene kommunizieren. Die Aufteilung der Anwendungskomponenten in verschiedene Ebenen erhöht die Verwaltbarkeit und die Skalierbarkeit der Anwendung.  Auf diese Weise wird das Einarbeiten neuer, eine einzelne Ebene betreffender Technologien vereinfacht, ein erneutes Entwerfen der Anwendung ist nicht notwendig. Außerdem werden vertrauliche Informationen von N-Tier-Anwendungen in der Regel in der mittleren Ebene gespeichert, die von der Präsentationsebene getrennt ist.

 Visual Studio enthält zahlreiche Features, die Entwicklern das Erstellen von N-Tier-Anwendungen erleichtern.

- Der DataSet-Designer stellt eine **DataSet-Projekt** Eigenschaft bereit, die es Ihnen ermöglicht, das Dataset (Daten Entitäts Schicht) und `TableAdapter` s (Datenzugriffs Ebene) in diskrete Projekte aufzuteilen.

- Die [LINQ to SQL-Tools in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) stellen Einstellungen bereit, mit denen die DataContext-und Daten Klassen in separaten Namespaces generiert werden. Dies ermöglicht eine logische Trennung von Datenzugriffs- und Datenentitätsebenen.

- [LINQ to SQL](https://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655) stellt die- <xref:System.Data.Linq.Table%601.Attach%2A> Methode bereit, mit der Sie den DataContext aus verschiedenen Ebenen in einer Anwendung zusammenführen können. Weitere Informationen finden Sie unter [N-Tier-und Remote Anwendungen mit LINQ to SQL](https://msdn.microsoft.com/library/854a1cdd-53cb-45f5-83ca-63962a9b3598).

## <a name="presentation-tier"></a>Präsentationsebene
 Die *Präsentationsebene* ist die Ebene, auf der Benutzer mit einer Anwendung interagieren. Sie enthält oft auch zusätzliche Anwendungslogik. Zu den typischen Komponenten einer Präsentationsebene gehören:

- Komponenten zur Datenbindung, etwa <xref:System.Windows.Forms.BindingSource> und <xref:System.Windows.Forms.BindingNavigator>.

- Objekt Darstellungen von Daten, z. b. [LINQ to SQL](https://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655) Entitäts Klassen für die Verwendung in der Präsentationsebene.

  Die Präsentationsebene greift in der Regel mithilfe eines Dienst Verweises auf die mittlere Ebene zu (z. b. ein [Windows Communication Foundation Dienste und WCF Data Services in der Visual Studio-](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md) Anwendung). Die Präsentationsschicht greift nicht direkt auf die Datenschicht zu. Sie kommuniziert mit der Datenebene unter Verwendung der Datenzugriffskomponenten der mittleren Ebene.

## <a name="middle-tier"></a>Mittlere Ebene
 Die *mittlere Ebene* ist die Ebene, über die Präsentationsebene und Datenebene miteinander kommunizieren. Zu den typischen Komponenten einer mittleren Ebene gehören:

- Geschäftslogik, z. B. Geschäftsregeln und Datenvalidierung.

- Komponenten und Logik für den Datenzugriff, wie beispielsweise:

  - [TableAdapters](https://msdn.microsoft.com/library/09416de9-134c-4dc7-8262-6c8d81e3f364) und [DataAdapters und DataReaders](https://msdn.microsoft.com/library/cc952ca2-ec19-46ab-9189-15174b52cb74).

  - Objekt Darstellungen von Daten, z. b. [LINQ to SQL](https://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655) Entitäts Klassen.

  - Allgemeine Anwendungsdienste wie Authentifizierung, Autorisierung und Personalisierung.

  In der folgenden Abbildung werden die in Visual Studio zur Verfügung stehenden Features und Technologien und deren mögliche Verwendung in der mittleren Ebene einer N-Tier-Anwendung dargestellt.

  ![Komponenten der mittleren Ebene](../data-tools/media/ntiermid.png "Ntiermid") Mittlere Ebene

  Die mittlere Ebene stellt in der Regel mithilfe einer Datenverbindung eine Verbindung mit der Datenschicht her. Diese Datenverbindung wird üblicherweise in der Datenzugriffskomponente gespeichert.

## <a name="data-tier"></a>Datenschicht
 Die *Datenebene* ist im Grunde der Server, der die Daten einer Anwendung speichert (z. b. ein Server, auf dem ausgeführt wird [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ).

 In der folgenden Abbildung werden die in Visual Studio zur Verfügung stehenden Funktionen und Technologien und deren mögliche Verwendung in der Datenebene einer N-Tier-Anwendung dargestellt.

 ![Datenebenenkomponenten](../data-tools/media/ntierdatatier.png "ntierdatatier") Datenebene

 Vom Client in der Präsentationsebene kann nicht direkt auf die Datenschicht zugegriffen werden. Stattdessen fungiert die mittlere Ebene als Datenzugriffskomponente und dient zur Kommunikation zwischen der Präsentations- und der Datenebene.

## <a name="help-for-n-tier-development"></a>Hilfe zur N-Tier-Entwicklung
 In den folgenden Themen finden Sie Informationen über die Arbeit mit N-Tier-Anwendungen:

 [Gewusst wie: DataSets und TableAdapters in verschiedene Projekte aufteilen](../data-tools/separate-datasets-and-tableadapters-into-different-projects.md)

 [Exemplarische Vorgehensweise: Erstellen einer N-Tier-Daten Anwendung](../data-tools/walkthrough-creating-an-n-tier-data-application.md)

 [Exemplarische Vorgehensweise: Hinzufügen von Validierungen zu einer N-Tier-Datenanwendung](https://msdn.microsoft.com/library/b35d072c-31f0-49ba-a225-69177592c265)

 [N-schichtige Anwendungen und Remoteanwendungen mit LINQ to SQL](https://msdn.microsoft.com/library/854a1cdd-53cb-45f5-83ca-63962a9b3598)

## <a name="see-also"></a>Weitere Informationen
 <xref:System.Data.Linq.ITable.Attach%2A>Exemplarische Vorgehensweise [: Erstellen einer N-Tier-Daten Anwendung](../data-tools/walkthrough-creating-an-n-tier-data-application.md) [hierarchische Update](../data-tools/hierarchical-update.md) [DataSet-Tools in Visual Studio](../data-tools/dataset-tools-in-visual-studio.md) [zugreifen auf Daten in Visual Studio](../data-tools/accessing-data-in-visual-studio.md)
