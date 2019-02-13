---
title: Entity Framework-Tools
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 1b06b573-84aa-4458-b3f5-e238df47bf45
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: d6f14dbe79e9ba0f2a8642c61a0682b25aa703f0
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2019
ms.locfileid: "55945832"
---
# <a name="entity-framework-tools-in-visual-studio"></a>Entity Framework-Tools in Visual Studio

Entitätsframework ist eine objektrelationale zuordnungstechnologie, die .NET-Entwicklern arbeiten mit relationalen Daten mithilfe von domänenspezifischen Objekten ermöglicht. In EF Core ist der Großteil des Datenzugriffscodes, den Entwickler in der Regel schreiben müssen, nicht mehr erforderlich. Entitätsframework ist die empfohlene objektrelationales Mapping (ORM) Modellieren der Technologie für neue Anwendungen für .NET.

Entity Framework-Tools dienen können Sie die Entity Framework (EF)-Anwendungen zu erstellen. Die vollständige Dokumentation für Entity Framework ist hier: [EF Core und EF 6](/ef/).

Mit Entity Framework-Tools, Sie erstellen eine *Konzeptmodell* aus einer vorhandenen Datenbank und anschließend grafisch visualisieren und bearbeiten Sie das konzeptionelle Modell. Oder Sie können zuerst ein konzeptionelles Modell grafisch erstellen und anschließend eine Datenbank generieren, die das Modell unterstützt. In beiden Fällen können Sie das Modell automatisch aktualisieren, sobald sich die zugrunde liegende Datenbank ändert, und Sie können automatisch Code auf Objektebene für die Anwendung erstellen. Datenbank- und Codegenerierung auf Objektebene sind vom Benutzer anpassbar.

Die Entity Framework-Tools installiert sind, als Teil der **datenspeicherung und-Verarbeitung** Workload im Visual Studio-Installer. Sie können diese auch als einzelne Komponente unter Installieren der **SDKs, Bibliotheken und Frameworks** Kategorie.

Dies sind die spezifischen Tools, die Entity Framework-Tools in Visual Studio bilden:

- Sie können die [!INCLUDE[vstecado](../data-tools/includes/vstecado_md.md)]  **[!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)] Designer** (**Entity Designer**) visuell erstellen und Ändern von Entitäten, Zuordnungen, Zuordnungen und vererbungsbeziehungen. Die **Entity Designer** generiert außerdem die [!INCLUDE[TLA#tla_cshrp](../data-tools/includes/tlasharptla_cshrp_md.md)] oder [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] Objektebenencode.

- Sie können die  **[!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)] Assistenten** zum Generieren eines konzeptionellen Modells aus einer vorhandenen Datenbank und Ihrer Anwendung Datenbankverbindungsinformationen hinzufügen.

- Sie können die **Assistent zur Datenbankgenerierung** zuerst ein konzeptionelles Modell erstellen, und erstellen Sie eine Datenbank, die das Modell unterstützt.

- Sie können die **Modellaktualisierungs-Assistenten** Ihrer konzeptionellen Modell, Speichermodell und Zuordnungen aktualisieren, wenn Änderungen der zugrunde liegenden Datenbank vorgenommen wurden.

  > [!NOTE]
  > Ab Visual Studio 2010, Entity Framework-Tools unterstützen keine [!INCLUDE[ss2k](../data-tools/includes/ss2k_md.md)].

Die Tools generieren oder Ändern einer *EDMX* Datei. Dies *EDMX* -Datei enthält Informationen, die das konzeptionelle Modell, Speichermodell und die Zuordnungen zwischen ihnen zu beschreiben. Weitere Informationen finden Sie unter [EDMX-Datei](https://docs.microsoft.com/ef/ef6/).

[Entity Framework Power Tools](https://marketplace.visualstudio.com/items?itemName=EntityFrameworkTeam.EntityFrameworkPowerToolsBeta4) hilft Ihnen beim Erstellen von Anwendungen, die das Entity Data Model verwenden. Powertools können ein konzeptionelles Modell, ein bestehendes Modell prüfen, Erzeugen von Quellcodedateien, die Objektklassen basierend auf dem konzeptionellen Modell enthalten und Erzeugen von Quellcodedateien, die Ansichten enthalten, die das Modell generiert. Ausführliche Informationen finden Sie unter [Pre-Generated Zuordnen von Ansichten](https://docs.microsoft.com/ef/ef6/fundamentals/performance/pre-generated-views).

## <a name="related-topics"></a>Verwandte Themen

| Titel | Beschreibung |
| - | - |
| [ADO.NET Entity Framework](/dotnet/framework/data/adonet/ef/index) | Beschreibt, wie [!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)] Tools, die [!INCLUDE[adonet_ef](../data-tools/includes/adonet_ef_md.md)] bereitstellt, um Anwendungen zu erstellen. |
| [Entity Data Model](/dotnet/framework/data/adonet/entity-data-model) | Enthält Links und Informationen zum Arbeiten mit Daten, mit dem Anwendungen, die auf [!INCLUDE[adonet_ef](../data-tools/includes/adonet_ef_md.md)]. |
| [Dokumentation zu Entity Framework (EF))](https://docs.microsoft.com/ef/ef6/get-started) | Stellt einen Index von Videos, Lernprogramme und advanced können Sie die optimale Nutzung von Entity Framework-Dokumentation. |
| [ASP.NET 5-Anwendung mit neuen Datenbank](https://docs.efproject.net/en/latest/platforms/aspnetcore/new-db.html) | Beschreibt, wie Sie eine neue ASP.NET 5-Anwendung mithilfe von Entity Framework 7 zu erstellen. |

## <a name="see-also"></a>Siehe auch

- [Visual Studio-Datentools für .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)