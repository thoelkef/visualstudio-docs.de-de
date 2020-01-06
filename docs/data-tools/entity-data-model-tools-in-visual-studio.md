---
title: Entity Framework-Tools
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 1b06b573-84aa-4458-b3f5-e238df47bf45
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 4af96ad0f76414468fd194b7079b3c4dbdaf2a4c
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/01/2020
ms.locfileid: "75586665"
---
# <a name="entity-framework-tools-in-visual-studio"></a>Entity Framework Tools in Visual Studio

Entity Framework ist eine Objekt relationale Mapping-Technologie, die es .NET-Entwicklern ermöglicht, mithilfe von domänenspezifischen Objekten mit relationalen Daten zu arbeiten. In EF Core ist der Großteil des Datenzugriffscodes, den Entwickler in der Regel schreiben müssen, nicht mehr erforderlich. Entity Framework ist die empfohlene ORM-Modellierungstechnologie (Object-Relational Mapping) für neue .NET-Anwendungen.

Entity Framework Tools wurden entwickelt, um Sie beim Erstellen von Entity Framework (EF)-Anwendungen zu unterstützen. Die komplette Dokumentation für Entity Framework finden Sie hier: [Übersicht-EF 6](/ef/ef6/).

  > [!NOTE]
  > Die auf dieser Seite beschriebenen Entity Framework Tools werden zum Generieren von *edmx* -Dateien verwendet, die in EF Core nicht unterstützt werden. Informationen zum Generieren eines EF Core Modells aus einer vorhandenen Datenbank finden Sie unter [Reverse Engineering-EF Core](/ef/core/managing-schemas/scaffolding). Weitere Informationen zu den Unterschieden zwischen EF 6 und EF Core finden Sie unter [Vergleichen von EF 6 und EF Core](/ef/efcore-and-ef6/).

Mit Entity Framework Tools können Sie ein *konzeptionelles Modell* aus einer vorhandenen Datenbank erstellen und dann das konzeptionelle Modell grafisch visualisieren und bearbeiten. Oder Sie können zuerst ein konzeptionelles Modell grafisch erstellen und anschließend eine Datenbank generieren, die das Modell unterstützt. In beiden Fällen können Sie das Modell automatisch aktualisieren, sobald sich die zugrunde liegende Datenbank ändert, und Sie können automatisch Code auf Objektebene für die Anwendung erstellen. Datenbank- und Codegenerierung auf Objektebene sind vom Benutzer anpassbar.

Die Entity Framework Tools werden im Rahmen der Arbeitsauslastung für die **Datenspeicherung und-Verarbeitung** im Visual Studio-Installer installiert. Sie können Sie auch als einzelne Komponente unter der Kategorie **SDK, Bibliotheken und Frameworks** installieren.

Dabei handelt es sich um die spezifischen Tools, die Entity Framework Tools in Visual Studio bilden:

- Mit dem [!INCLUDE[vstecado](../data-tools/includes/vstecado_md.md)][!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)]- **Designer** (**Entity Designer**) können Sie Entitäten, Zuordnungen, Zuordnungen und Vererbungs Beziehungen visuell erstellen und ändern. Der **Entity Designer** generiert auch [!INCLUDE[TLA#tla_cshrp](../data-tools/includes/tlasharptla_cshrp_md.md)] oder [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] objektebenencode.

- Mit dem[!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)]- **Assistenten** können Sie ein konzeptionelles Modell aus einer vorhandenen Datenbank generieren und der Anwendung Daten bankverbindungs Informationen hinzufügen.

- Mit dem Assistenten zum **Erstellen einer Datenbank** können Sie zuerst ein konzeptionelles Modell erstellen und dann eine Datenbank erstellen, die das Modell unterstützt.

- Mit dem **Modellaktualisierungs-Assistenten** können Sie das konzeptionelle Modell, das Speichermodell und die Zuordnungen aktualisieren, wenn Änderungen an der zugrunde liegenden Datenbank vorgenommen wurden.

  > [!NOTE]
  > Ab Visual Studio 2010 unterstützen Entity Framework Tools [!INCLUDE[ss2k](../data-tools/includes/ss2k_md.md)]nicht.

Die-Tools generieren oder ändern eine *edmx* -Datei. Diese *edmx* -Datei enthält Informationen, in denen das konzeptionelle Modell, das Speichermodell und die Zuordnungen zwischen Ihnen beschrieben werden. Weitere Informationen finden Sie unter [edmx](/ef/ef6/).

[Entity Framework Power Tools](https://marketplace.visualstudio.com/items?itemName=EntityFrameworkTeam.EntityFrameworkPowerToolsBeta4) helfen Ihnen beim Erstellen von Anwendungen, die die Entity Data Model verwenden. Mit den Power Tools können Sie ein konzeptionelles Modell generieren, ein vorhandenes Modell überprüfen, Quell Code Dateien erstellen, die auf dem konzeptionellen Modell basierende Objektklassen enthalten, und Quell Code Dateien erstellen, die vom Modell generierte Sichten enthalten. Ausführliche Informationen finden Sie unter [vorab generierte Mapping-Sichten](https://docs.microsoft.com/ef/ef6/fundamentals/performance/pre-generated-views).

## <a name="related-topics"></a>Verwandte Themen

| Title | Beschreibung |
| - | - |
| [ADO.NET Entity Framework](/dotnet/framework/data/adonet/ef/index) | Beschreibt die Verwendung von [!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)] Tools, die [!INCLUDE[adonet_ef](../data-tools/includes/adonet_ef_md.md)] bereitstellt, um-Anwendungen zu erstellen. |
| [Entity Data Model](/dotnet/framework/data/adonet/entity-data-model) | Enthält Links und Informationen zum Arbeiten mit Daten, die von Anwendungen verwendet werden, die auf [!INCLUDE[adonet_ef](../data-tools/includes/adonet_ef_md.md)]basieren. |
| [Entity Framework (EF)-Dokumentation)](/ef/ef6/get-started) | Bietet einen Index mit Videos, Tutorials und erweiterter Dokumentation, mit deren Hilfe Sie Entity Framework optimal nutzen können. |
| [ASP.net 5 Anwendung in neue Datenbank](https://docs.efproject.net/en/latest/platforms/aspnetcore/new-db.html) | Hier wird beschrieben, wie Sie eine neue ASP.net 5-Anwendung mit Entity Framework 7 erstellen. |

## <a name="see-also"></a>Siehe auch

- [Visual Studio-Datentools für .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)
