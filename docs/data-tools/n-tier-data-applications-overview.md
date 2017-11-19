---
title: "Daten von N-Tier-Anwendungen (Übersicht) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- presentation tier
- middle tier
- data tier
- n-tier applications, about n-tier applications
ms.assetid: 1020581d-eaaa-41a2-aca4-bf4c212895f6
caps.latest.revision: "26"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.openlocfilehash: 3949d49f763c2513e86c2cd3f1b20c20fb858ecc
ms.sourcegitcommit: ee42a8771f0248db93fd2e017a22e2506e0f9404
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/09/2017
---
# <a name="n-tier-data-applications-overview"></a>Übersicht über N-Tier-Datenanwendungen
*N-Tier-* -datenanwendungen sind datenanwendungen, die in mehrere voneinander *Ebenen*. Sie werden auch "verteilte Anwendungen" oder "Anwendungen mit mehreren Ebenen" genannt, da die Verarbeitung auf voneinander unabhängige, auf Client und Server verteilte Ebenen aufgeteilt wird. Beim Entwickeln einer Anwendung, die auf Daten zugreift, sollten die verschiedenen Ebenen, aus denen die Anwendung besteht, klar getrennt sein.  
  
Eine typische N-Tier-Anwendung besteht aus einer Präsentationsebene, einer mittleren Ebene und einer Datenebene. Die einfachste Möglichkeit zum Trennen der verschiedenen Ebenen einer N-Tier-Anwendung besteht im Erstellen separater Projekte für jede Ebene, die in der Anwendung enthalten sein soll. Beispielsweise könnte die Präsentationsebene eine Windows Forms-Anwendung sein, während die Datenzugriffslogik eine in der mittleren Ebene angesiedelte Klassenbibliothek ist. Weiterhin könnte die Präsentationslogik in der mittleren Ebene über einen Dienst mit der Datenzugriffsebene kommunizieren. Die Aufteilung der Anwendungskomponenten in verschiedene Ebenen erhöht die Verwaltbarkeit und die Skalierbarkeit der Anwendung.  Auf diese Weise wird das Einarbeiten neuer, eine einzelne Ebene betreffender Technologien vereinfacht, ein erneutes Entwerfen der Anwendung ist nicht notwendig. Außerdem werden vertrauliche Informationen von N-Tier-Anwendungen in der Regel in der mittleren Ebene gespeichert, die von der Präsentationsebene getrennt ist.  
  
Visual Studio enthält zahlreiche Funktionen, die Entwicklern das Erstellen von N-Tier-Anwendungen erleichtern.  
  
-   Das Dataset bietet eine **DataSet-Projekt** -Eigenschaft, die Ihnen ermöglicht, das Dataset (Datenentitätsschicht) und TableAdaptern (Data Access Layer) in gesonderten Projekten.  
  
-   Die [LINQ to SQL-Tools in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) enthält Einstellungen, um die Klassen DataContext und Daten in separaten Namespaces zu generieren. Dies ermöglicht eine logische Trennung von Datenzugriffs- und Datenentitätsebenen.  
  
-   [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index) bietet die <xref:System.Data.Linq.Table%601.Attach%2A> Methode, die Sie für das Zusammenführen der DataContext aus unterschiedlichen Ebenen in einer Anwendung ermöglicht. Weitere Informationen finden Sie unter [N-schichtige und Remoteanwendungen mit LINQ to SQL](http://msdn.microsoft.com/Library/854a1cdd-53cb-45f5-83ca-63962a9b3598).  
  
## <a name="presentation-tier"></a>Präsentationsebene  
Die *Präsentationsebene* ist die Ebene, in dem Benutzer, die mit einer Anwendung interagieren. Sie enthält oft auch zusätzliche Anwendungslogik. Zu den typischen Komponenten einer Präsentationsebene gehören:  
  
-   Komponenten zur Datenbindung, etwa <xref:System.Windows.Forms.BindingSource> und <xref:System.Windows.Forms.BindingNavigator>.  
  
-   Objekt-Darstellung der Daten, z. B. [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index) Entitätsklassen zur Verwendung in der Präsentationsebene.  
  
Die Präsentationsebene greift der mittleren Ebene in der Regel mithilfe eines Dienstverweises auf (z. B. eine [Windows Communication Foundation-Dienste und WCF Data Services in Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md) Anwendung). Die Präsentationsschicht greift nicht direkt auf die Datenschicht zu. Sie kommuniziert mit der Datenebene unter Verwendung der Datenzugriffskomponenten der mittleren Ebene.  
  
## <a name="middle-tier"></a>Mittlere Ebene  
Die *mittleren Ebene* ist die Ebene, die die Präsentationsebene und Datenebene miteinander kommunizieren verwenden. Zu den typischen Komponenten einer mittleren Ebene gehören:  
  
-   Geschäftslogik, z. B. Geschäftsregeln und Datenvalidierung.  
  
-   Komponenten und Logik für den Datenzugriff, wie beispielsweise:  
  
    -   [TableAdapters](create-and-configure-tableadapters.md) und ["DataAdapters" und "DataReaders"](/dotnet/framework/data/adonet/dataadapters-and-datareaders).  
  
    -   Objekt-Darstellung der Daten, z. B. [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index) Entitätsklassen.  
  
    -   Allgemeine Anwendungsdienste wie Authentifizierung, Autorisierung und Personalisierung.  
  
In der folgenden Abbildung werden die in Visual Studio zur Verfügung stehenden Funktionen und Technologien und deren mögliche Verwendung in der mittleren Ebene einer N-Tier-Anwendung dargestellt.  
  
![Mittlere Ebene Komponenten](../data-tools/media/ntiermid.png "NtierMid")  
Mittlere Ebene  
  
Die mittlere Ebene stellt in der Regel mithilfe einer Datenverbindung eine Verbindung mit der Datenschicht her. Diese Datenverbindung wird üblicherweise in der Datenzugriffskomponente gespeichert.  
  
## <a name="data-tier"></a>Datenschicht  
Die *Datenebene* entspricht im Grunde der Server, die eine Anwendung Daten speichert (z. B. einem Server mit [!INCLUDE[ssNoVersion](../data-tools/includes/ssnoversion_md.md)]).  
  
In der folgenden Abbildung werden die in Visual Studio zur Verfügung stehenden Funktionen und Technologien und deren mögliche Verwendung in der Datenebene einer N-Tier-Anwendung dargestellt.  
  
![Komponenten der Datenebene](../data-tools/media/ntierdatatier.png "Ntierdatatier")  
Datenschicht  
  
Vom Client in der Präsentationsebene kann nicht direkt auf die Datenschicht zugegriffen werden. Stattdessen fungiert die mittlere Ebene als Datenzugriffskomponente und dient zur Kommunikation zwischen der Präsentations- und der Datenebene.  
  
## <a name="help-for-n-tier-development"></a>Hilfe zur N-Tier-Entwicklung  
In den folgenden Themen finden Sie Informationen über die Arbeit mit N-Tier-Anwendungen:  
  
[Gewusst wie: DataSets und TableAdapters in verschiedene Projekte aufteilen](../data-tools/separate-datasets-and-tableadapters-into-different-projects.md)  
  
[Exemplarische Vorgehensweise: Erstellen einer N-Tier-Datenanwendung](../data-tools/walkthrough-creating-an-n-tier-data-application.md)  

[N-schichtige und Remoteanwendungen mit LINQ to SQL](http://msdn.microsoft.com/Library/854a1cdd-53cb-45f5-83ca-63962a9b3598)  
  
## <a name="see-also"></a>Siehe auch
[Exemplarische Vorgehensweise: Erstellen einer N-Tier-Datenanwendung](../data-tools/walkthrough-creating-an-n-tier-data-application.md)   
[Hierarchische Aktualisierung](../data-tools/hierarchical-update.md)   
[Datasettools in Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)   
[Zugreifen auf Daten in Visual Studio](../data-tools/accessing-data-in-visual-studio.md)