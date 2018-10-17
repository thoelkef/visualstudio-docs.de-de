---
title: Entity Data Model-Tools in Visual Studio | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
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
ms.assetid: 1b06b573-84aa-4458-b3f5-e238df47bf45
caps.latest.revision: 24
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 3a3d64aed3834d517cb916bfbbed47a263eb8619
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49290471"
---
# <a name="entity-data-model-tools-in-visual-studio"></a>Entity Data Model-Tools in Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Entitätsframework ist eine objektrelationale zuordnungstechnologie, die .NET-Entwicklern arbeiten mit relationalen Daten mithilfe von domänenspezifischen Objekten ermöglicht. In EF Core ist der Großteil des Datenzugriffscodes, den Entwickler in der Regel schreiben müssen, nicht mehr erforderlich. Entitätsframework ist die empfohlene objektrelationales Mapping (ORM) Modellieren der Technologie für neue Anwendungen für .NET.  
  
 Im März 2016 ist die aktuelle veröffentlichte Version [Entity Framework 6](https://msdn.microsoft.com/data/ef) . [Entitätsframework 7](https://docs.efproject.net/en/latest/) ist in der Vorabversion.  
  
 [!INCLUDE[adonet_edm](../includes/adonet-edm-md.md)] Tools dienen zum Erstellen [!INCLUDE[adonet_ef](../includes/adonet-ef-md.md)] Anwendungen. Die vollständige Dokumentation für [!INCLUDE[adonet_edm](../includes/adonet-edm-md.md)] -Tools finden Sie hier: [Entity Framework](https://msdn.microsoft.com/data/jj590134).  
  
 Mit [!INCLUDE[adonet_edm](../includes/adonet-edm-md.md)] Tools, die Sie erstellen eine *Konzeptmodell* aus einer vorhandenen Datenbank und anschließend grafisch visualisieren und bearbeiten Sie das konzeptionelle Modell. Oder Sie können zuerst ein konzeptionelles Modell grafisch erstellen und anschließend eine Datenbank generieren, die das Modell unterstützt. In beiden Fällen können Sie das Modell automatisch aktualisieren, sobald sich die zugrunde liegende Datenbank ändert, und Sie können automatisch Code auf Objektebene für die Anwendung erstellen. Datenbank- und Codegenerierung auf Objektebene sind vom Benutzer anpassbar.  
  
 Dies sind die spezifischen Tools, die Entity Data Model-Tools in Visual Studio 2015 bilden:  
  
-   Sie können die [!INCLUDE[vstecado](../includes/vstecado-md.md)]  **[!INCLUDE[adonet_edm](../includes/adonet-edm-md.md)] Designer** (**Entity Designer**) visuell erstellen und Ändern von Entitäten, Zuordnungen, Zuordnungen und vererbungsbeziehungen. Die **Entity Designer** generiert außerdem die [!INCLUDE[TLA#tla_cshrp](../includes/tlasharptla-cshrp-md.md)] oder [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] Objektebenencode.  
  
-   Sie können die  **[!INCLUDE[adonet_edm](../includes/adonet-edm-md.md)] Assistenten** zum Generieren eines konzeptionellen Modells aus einer vorhandenen Datenbank und Ihrer Anwendung Datenbankverbindungsinformationen hinzufügen.  
  
-   Sie können die **Assistent zur Datenbankgenerierung** zuerst ein konzeptionelles Modell erstellen, und erstellen Sie eine Datenbank, die das Modell unterstützt.  
  
-   Sie können die **Modellaktualisierungs-Assistenten** Ihrer konzeptionellen Modell, Speichermodell und Zuordnungen aktualisieren, wenn Änderungen der zugrunde liegenden Datenbank vorgenommen wurden.  
  
    > [!NOTE]
    >  Beginnend mit Visual Studio 2010 [!INCLUDE[adonet_edm](../includes/adonet-edm-md.md)] Tools unterstützen keine [!INCLUDE[ss2k](../includes/ss2k-md.md)].  
  
 Die Tools generieren oder ändern eine EDMX-Datei. Diese Datei enthält Informationen, die das konzeptionelle Modell, Speichermodell und die Zuordnungen zwischen ihnen zu beschreiben. Weitere Informationen finden Sie unter [EDMX-Datei](https://msdn.microsoft.com/data/jj650889.aspx).  
  
 Entity Framework Powertools können Sie die Anwendungen erstellen, die verwenden das Entity Data Model. Die Tools können ein konzeptionelles Modell, ein bestehendes Modell prüfen, Erzeugen von Quellcodedateien, die Objektklassen basierend auf dem konzeptionellen Modell enthalten und Erzeugen von Quellcodedateien, die Ansichten enthalten, die das Modell generiert. Ausführliche Informationen finden Sie unter [Pre-Generated Zuordnen von Ansichten](https://msdn.microsoft.com/data/dn469601.aspx).  
  
## <a name="related-topics"></a>Verwandte Themen  
  
|Titel|Beschreibung|  
|-----------|-----------------|  
|[ADO.NET Entity Framework](http://msdn.microsoft.com/library/a437041f-6899-4ae7-96ce-aabf528d7205)|Beschreibt, wie [!INCLUDE[adonet_edm](../includes/adonet-edm-md.md)] Tools, die [!INCLUDE[adonet_ef](../includes/adonet-ef-md.md)] bereitstellt, um Anwendungen zu erstellen.|  
|[Entity Data Model](http://msdn.microsoft.com/library/2dda3d5b-4582-4ba0-a91d-fcd7a1498137)|Enthält Links und Informationen zum Arbeiten mit Daten, mit dem Anwendungen, die auf [!INCLUDE[adonet_ef](../includes/adonet-ef-md.md)].|  
|[Erste Schritte in der vollständigen .NET (Konsole, WinForms, WPF, usw.).](https://docs.efproject.net/en/latest/platforms/full-dotnet/getting-started.html)|Stellt Tutorials zum Erstellen von .NET desktop-Anwendungen, die Entity Framework 7 verwenden.|  
|[ASP.NET 5-Anwendung mit neuen Datenbank](https://docs.efproject.net/en/latest/platforms/aspnetcore/new-db.html)|Beschreibt, wie Sie eine neue ASP.NET 5-Anwendung mithilfe von Entity Framework 7 zu erstellen.|  
  
## <a name="see-also"></a>Siehe auch  
 [Visual Studio-Datentools für .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)

