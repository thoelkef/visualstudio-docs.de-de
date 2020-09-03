---
title: Entity Data Model-Tools
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
ms.assetid: 1b06b573-84aa-4458-b3f5-e238df47bf45
caps.latest.revision: 24
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: d663b86603145f8a665f189e5abfbfa2b0b360ae
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72672383"
---
# <a name="entity-data-model-tools-in-visual-studio"></a>Entity Data Model-Tools in Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Entity Framework ist eine Objekt relationale Mapping-Technologie, die es .NET-Entwicklern ermöglicht, mithilfe von domänenspezifischen Objekten mit relationalen Daten zu arbeiten. Es entfällt die Notwendigkeit für den Großteil des Datenzugriffs-Codes, den Entwickler normalerweise schreiben müssen. Entity Framework ist die empfohlene ORM-Modellierungstechnologie (Object-Relational Mapping) für neue .NET-Anwendungen.

 Ab dem 2016 ist die aktuelle veröffentlichte Version [Entity Framework 6](https://msdn.microsoft.com/data/ef) . [Entity Framework 7](https://docs.efproject.net/en/latest/) befindet sich in der Vorabversion.

 [!INCLUDE[adonet_edm](../includes/adonet-edm-md.md)] Tools dienen als Hilfe beim Erstellen von [!INCLUDE[adonet_ef](../includes/adonet-ef-md.md)] Anwendungen. Die komplette Dokumentation für [!INCLUDE[adonet_edm](../includes/adonet-edm-md.md)] Tools finden Sie hier: [Entity Framework](https://msdn.microsoft.com/data/jj590134).

 Mit [!INCLUDE[adonet_edm](../includes/adonet-edm-md.md)] Tools können Sie ein *konzeptionelles Modell* aus einer vorhandenen Datenbank erstellen und dann das konzeptionelle Modell grafisch visualisieren und bearbeiten. Oder Sie können zuerst ein konzeptionelles Modell grafisch erstellen und anschließend eine Datenbank generieren, die das Modell unterstützt. In beiden Fällen können Sie das Modell automatisch aktualisieren, sobald sich die zugrunde liegende Datenbank ändert, und Sie können automatisch Code auf Objektebene für die Anwendung erstellen. Datenbank- und Codegenerierung auf Objektebene sind vom Benutzer anpassbar.

 Dies sind die spezifischen Tools, die Entity Data Model Tools in Visual Studio 2015 bilden:

- Mit dem [!INCLUDE[vstecado](../includes/vstecado-md.md)] ** [!INCLUDE[adonet_edm](../includes/adonet-edm-md.md)] Designer** (**Entity Designer**) können Sie Entitäten, Zuordnungen, Zuordnungen und Vererbungs Beziehungen visuell erstellen und ändern. Der- **Entity Designer** generiert auch [!INCLUDE[TLA#tla_cshrp](../includes/tlasharptla-cshrp-md.md)] oder [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] objektebenencode.

- Sie können den ** [!INCLUDE[adonet_edm](../includes/adonet-edm-md.md)] Assistenten** verwenden, um ein konzeptionelles Modell aus einer vorhandenen Datenbank zu generieren und der Anwendung Daten bankverbindungs Informationen hinzuzufügen.

- Mit dem Assistenten zum **Erstellen einer Datenbank** können Sie zuerst ein konzeptionelles Modell erstellen und dann eine Datenbank erstellen, die das Modell unterstützt.

- Mit dem **Modellaktualisierungs-Assistenten** können Sie das konzeptionelle Modell, das Speichermodell und die Zuordnungen aktualisieren, wenn Änderungen an der zugrunde liegenden Datenbank vorgenommen wurden.

  > [!NOTE]
  > Ab Visual Studio 2010 [!INCLUDE[adonet_edm](../includes/adonet-edm-md.md)] unterstützen Tools nicht [!INCLUDE[ss2k](../includes/ss2k-md.md)] .

  Die-Tools generieren oder ändern eine EDMX-Datei. Diese Datei enthält Informationen, in denen das konzeptionelle Modell, das Speichermodell und die Zuordnungen zwischen Ihnen beschrieben werden. Weitere Informationen finden Sie unter  [edmx](https://msdn.microsoft.com/data/jj650889.aspx).

  Entity Framework Power Tools helfen Ihnen beim Erstellen von Anwendungen, die die Entity Data Model verwenden. Mit den Tools können Sie ein konzeptionelles Modell generieren, ein vorhandenes Modell überprüfen, Quell Code Dateien erstellen, die auf dem konzeptionellen Modell basierende Objektklassen enthalten, und Quell Code Dateien erstellen, die vom Modell generierte Sichten enthalten. Ausführliche Informationen finden Sie unter [vorab generierte Mapping-Sichten](https://msdn.microsoft.com/data/dn469601.aspx).

## <a name="related-topics"></a>Verwandte Themen

|Titel|BESCHREIBUNG|
|-----------|-----------------|
|[ADO.NET Entity Framework](https://msdn.microsoft.com/library/a437041f-6899-4ae7-96ce-aabf528d7205)|Beschreibt [!INCLUDE[adonet_edm](../includes/adonet-edm-md.md)] die Verwendung von Tools, die [!INCLUDE[adonet_ef](../includes/adonet-ef-md.md)] bereitstellt, um-Anwendungen zu erstellen.|
|[Entity Data Model](https://msdn.microsoft.com/library/2dda3d5b-4582-4ba0-a91d-fcd7a1498137)|Enthält Links und Informationen zum Arbeiten mit Daten, die von Anwendungen verwendet werden, die auf basieren [!INCLUDE[adonet_ef](../includes/adonet-ef-md.md)] .|
|[Getting Started on Full .net (Console, WinForms, WPF usw.)](/ef/ef6/get-started)|Enthält Tutorials zum Erstellen von .net-Desktop Anwendungen, in denen Entity Framework 7 verwendet wird.|
|[ASP.net 5 Anwendung in neue Datenbank](https://docs.efproject.net/en/latest/platforms/aspnetcore/new-db.html)|Hier wird beschrieben, wie Sie eine neue ASP.net 5-Anwendung mit Entity Framework 7 erstellen.|

## <a name="see-also"></a>Weitere Informationen
 [Visual Studio-Datentools für .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)
