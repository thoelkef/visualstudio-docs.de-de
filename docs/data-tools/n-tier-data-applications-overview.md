---
title: Übersicht über N-Tier-Datenanwendungen
ms.date: 11/04/2016
ms.topic: overview
helpviewer_keywords:
- presentation tier
- middle tier
- data tier
- n-tier applications, about n-tier applications
ms.assetid: 1020581d-eaaa-41a2-aca4-bf4c212895f6
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 14527e84d5bbd2d06b2d091ba7a9d4daa9763462
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/23/2020
ms.locfileid: "85281954"
---
# <a name="n-tier-data-applications-overview"></a>Übersicht über n-schichtige Datenanwendungen
*N-Tier-* Daten Anwendungen sind Daten Anwendungen, die in mehrere *Ebenen*aufgeteilt sind. Sie werden auch "verteilte Anwendungen" oder "Anwendungen mit mehreren Ebenen" genannt, da die Verarbeitung auf voneinander unabhängige, auf Client und Server verteilte Ebenen aufgeteilt wird. Beim Entwickeln einer Anwendung, die auf Daten zugreift, sollten die verschiedenen Ebenen, aus denen die Anwendung besteht, klar getrennt sein.

Eine typische N-Tier-Anwendung besteht aus einer Präsentationsschicht, einer mittleren Ebene und einer Datenschicht. Die einfachste Möglichkeit zum Trennen der verschiedenen Ebenen einer N-Tier-Anwendung besteht im Erstellen separater Projekte für jede Ebene, die in der Anwendung enthalten sein soll. Beispielsweise könnte die Präsentationsebene eine Windows Forms-Anwendung sein, während die Datenzugriffslogik eine in der mittleren Ebene angesiedelte Klassenbibliothek ist. Darüber hinaus kann die Präsentationsschicht über einen Dienst, z. b. einen Webdienst, mit der Datenzugriffs Logik in der mittleren Ebene kommunizieren. Die Aufteilung der Anwendungskomponenten in verschiedene Ebenen erhöht die Verwaltbarkeit und die Skalierbarkeit der Anwendung.  Auf diese Weise wird das Einarbeiten neuer, eine einzelne Ebene betreffender Technologien vereinfacht, ein erneutes Entwerfen der Anwendung ist nicht notwendig. Außerdem werden vertrauliche Informationen von N-Tier-Anwendungen in der Regel in der mittleren Ebene gespeichert, die von der Präsentationsebene getrennt ist.

Visual Studio enthält zahlreiche Features, die Entwicklern das Erstellen von N-Tier-Anwendungen erleichtern.

- Das DataSet stellt eine **DataSet-Projekt** Eigenschaft bereit, die es Ihnen ermöglicht, das Dataset (Daten Entitäts Ebene) und TableAdapters (Datenzugriffs Ebene) in diskrete Projekte zu trennen.

- Die [LINQ to SQL-Tools in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) stellen Einstellungen bereit, mit denen die DataContext-und Daten Klassen in separaten Namespaces generiert werden. Dies ermöglicht eine logische Trennung von Datenzugriffs- und Datenentitätsebenen.

- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index) stellt die- <xref:System.Data.Linq.Table%601.Attach%2A> Methode bereit, mit der Sie den DataContext aus verschiedenen Ebenen in einer Anwendung zusammenführen können. Weitere Informationen finden Sie unter [N-Tier-und Remote Anwendungen mit LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/n-tier-and-remote-applications-with-linq-to-sql).

## <a name="presentation-tier"></a>Darstellungsschicht
Die *Präsentationsebene* ist die Ebene, auf der Benutzer mit einer Anwendung interagieren. Sie enthält oft auch zusätzliche Anwendungslogik. Zu den typischen Komponenten einer Präsentationsebene gehören:

- Komponenten zur Datenbindung, etwa <xref:System.Windows.Forms.BindingSource> und <xref:System.Windows.Forms.BindingNavigator>.

- Objekt Darstellungen von Daten, z. b. [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index) Entitäts Klassen für die Verwendung in der Präsentationsebene.

Die Präsentationsebene greift in der Regel mithilfe eines Dienst Verweises auf die mittlere Ebene zu (z. b. ein [Windows Communication Foundation Dienste und WCF Data Services in der Visual Studio-](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md) Anwendung). Die Präsentationsschicht greift nicht direkt auf die Datenschicht zu. Sie kommuniziert mit der Datenebene unter Verwendung der Datenzugriffskomponenten der mittleren Ebene.

## <a name="middle-tier"></a>Mittlere Ebene
Die *mittlere Ebene* ist die Ebene, über die Präsentationsebene und Datenebene miteinander kommunizieren. Zu den typischen Komponenten einer mittleren Ebene gehören:

- Geschäftslogik, z. B. Geschäftsregeln und Datenvalidierung.

- Komponenten und Logik für den Datenzugriff, wie beispielsweise:

  - [TableAdapters](create-and-configure-tableadapters.md) und [DataAdapters und DataReaders](/dotnet/framework/data/adonet/dataadapters-and-datareaders).

  - Objekt Darstellungen von Daten, z. b. [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index) Entitäts Klassen.

  - Allgemeine Anwendungsdienste wie Authentifizierung, Autorisierung und Personalisierung.

In der folgenden Abbildung werden die in Visual Studio zur Verfügung stehenden Features und Technologien und deren mögliche Verwendung in der mittleren Ebene einer N-Tier-Anwendung dargestellt.

![](../data-tools/media/ntiermid.png)Mittlere Ebene Komponenten der mittleren Ebene

Die mittlere Ebene stellt in der Regel mithilfe einer Datenverbindung eine Verbindung mit der Datenschicht her. Diese Datenverbindung wird üblicherweise in der Datenzugriffskomponente gespeichert.

## <a name="data-tier"></a>Datenschicht
Die *Datenebene* ist im Grunde der Server, auf dem Daten einer Anwendung (z.B. ein Server mit SQL Server) gespeichert werden.

In der folgenden Abbildung werden die in Visual Studio zur Verfügung stehenden Funktionen und Technologien und deren mögliche Verwendung in der Datenebene einer N-Tier-Anwendung dargestellt.

![Datenebene der Datenebenenkomponenten ](../data-tools/media/ntierdatatier.png)

Vom Client in der Präsentationsebene kann nicht direkt auf die Datenschicht zugegriffen werden. Stattdessen fungiert die mittlere Ebene als Datenzugriffskomponente und dient zur Kommunikation zwischen der Präsentations- und der Datenebene.

## <a name="help-for-n-tier-development"></a>Hilfe zur n-schichtigen Entwicklung
In den folgenden Themen finden Sie Informationen über die Arbeit mit N-Tier-Anwendungen:

[Gewusst wie: DataSets und TableAdapters in verschiedene Projekte aufteilen](../data-tools/separate-datasets-and-tableadapters-into-different-projects.md)

[Exemplarische Vorgehensweise: Erstellen einer n-Tier-Daten Anwendung](../data-tools/walkthrough-creating-an-n-tier-data-application.md)

[N-Tier-und Remote Anwendungen mit LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/n-tier-and-remote-applications-with-linq-to-sql)

## <a name="see-also"></a>Weitere Informationen

- [Exemplarische Vorgehensweise: Erstellen einer n-Tier-Daten Anwendung](../data-tools/walkthrough-creating-an-n-tier-data-application.md)
- [Hierarchische Aktualisierung](../data-tools/hierarchical-update.md)
- [Datasettools in Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)
- [Zugreifen auf Daten in Visual Studio](../data-tools/accessing-data-in-visual-studio.md)
