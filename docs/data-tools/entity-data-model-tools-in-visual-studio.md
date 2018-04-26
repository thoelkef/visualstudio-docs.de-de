---
title: Entity Framework-Tools in Visual Studio
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 1b06b573-84aa-4458-b3f5-e238df47bf45
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 0b1d98422d9527220b54232d1180ae4b91a28e6b
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
---
# <a name="entity-framework-tools-in-visual-studio"></a>Entity Framework-Tools in Visual Studio
Entity Framework ist eine objektrelationales Mapping-Technologie, mit der .NET Entwicklern das Arbeiten mit relationalen Daten mithilfe von domänenspezifischen Objekten. In EF Core ist der Großteil des Datenzugriffscodes, den Entwickler in der Regel schreiben müssen, nicht mehr erforderlich. Entity Framework ist die empfohlene objektrelationales Mapping (ORM) Technologie für neue .NET-Anwendungen zu modellieren.

Entity Framework-Tools dienen können Sie die Entity Framework (EF)-Anwendungen zu erstellen. Eine vollständige Dokumentation zu Entity Framework ist hier: [EF Core und EF 6](/ef/).

Sie können mit Entity Framework-Tools erstellen eine *Konzeptmodell* aus einer vorhandenen Datenbank grafisch visualisieren und bearbeiten Sie das konzeptionelle Modell. Oder Sie können zuerst ein konzeptionelles Modell grafisch erstellen und anschließend eine Datenbank generieren, die das Modell unterstützt. In beiden Fällen können Sie das Modell automatisch aktualisieren, sobald sich die zugrunde liegende Datenbank ändert, und Sie können automatisch Code auf Objektebene für die Anwendung erstellen. Datenbank- und Codegenerierung auf Objektebene sind vom Benutzer anpassbar.

Die Entity Framework-Tools installiert sind, als Teil der **datenspeicherung und Verarbeitung** arbeitsauslastung in der Visual Studio-Installer. Sie können diese auch als Komponente Indvidual unter Installieren der **SDKs, Bibliotheken und Frameworks** Kategorie.

Dies sind die einzelnen Tools, die Entity Framework-Tools in Visual Studio bilden:

-   Sie können die [!INCLUDE[vstecado](../data-tools/includes/vstecado_md.md)]  **[!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)] Designer** (**Entity Designer**) visuell erstellen und Ändern von Entitäten, Zuordnungen, Zuordnungen und vererbungsbeziehungen. Die **Entity Designer** generiert auch [!INCLUDE[TLA#tla_cshrp](../data-tools/includes/tlasharptla_cshrp_md.md)] oder [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] Objektebenencode.

-   Sie können die  **[!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)] Assistenten** zum Generieren eines konzeptionellen Modells aus einer vorhandenen Datenbank und Datenbank-Verbindungsinformationen zur Anwendung hinzufügen.

-   Sie können die **Assistenten zum Erstellen von Datenbanken** erstellen zuerst ein konzeptionelles Modell und erstellen Sie eine Datenbank, die das Modell unterstützt.

-   Sie können die **Modellaktualisierungs-Assistenten** Ihrem konzeptionellen Modell, die Speichermodell und die Zuordnungen aktualisieren, wenn Änderungen der zugrunde liegenden Datenbank vorgenommen wurden.

    > [!NOTE]
    >  Beginnend mit Visual Studio 2010, Entity Framework-Tools unterstützen keine [!INCLUDE[ss2k](../data-tools/includes/ss2k_md.md)].

Die Tools generieren oder ändern eine EDMX-Datei. Diese EDMX-Datei enthält Informationen, die das konzeptionelle Modell, das Speichermodell und die Zuordnungen zwischen beiden beschreiben. Weitere Informationen finden Sie unter [EDMX](https://msdn.microsoft.com/data/jj650889.aspx).

[Entity Framework-Powertools](https://marketplace.visualstudio.com/items?itemName=EntityFrameworkTeam.EntityFrameworkPowerToolsBeta4) können Sie Anwendungen erstellen, die das Entity Data Model zu verwenden. Die Powertools können ein konzeptionelles Modell, ein vorhandenes Modell prüfen, Erstellen von Quellcodedateien, die basierend auf dem konzeptionellen Modell Objektklassen enthalten und erzeugen Quellcodedateien, die Ansichten enthalten, die das Modell generiert. Ausführliche Informationen finden Sie unter [Pre-Generated Zuordnung Ansichten](https://msdn.microsoft.com/data/dn469601.aspx).

## <a name="related-topics"></a>Verwandte Themen

|Titel|Beschreibung|
|-----------|-----------------|
|[ADO.NET Entity Framework](/dotnet/framework/data/adonet/ef/index)|Beschreibt, wie [!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)] Tools, die [!INCLUDE[adonet_ef](../data-tools/includes/adonet_ef_md.md)] bereitstellt, um Anwendungen zu erstellen.|
|[Entity Data Model](/dotnet/framework/data/adonet/entity-data-model)|Enthält Links und Informationen zum Arbeiten mit Daten, die von Anwendungen, die auf verwendet [!INCLUDE[adonet_ef](../data-tools/includes/adonet_ef_md.md)].|
|[Dokumentation zu Entity Framework (EF))](https://msdn.microsoft.com/library/ee712907(v=vs.113).aspx)|Stellt einen Index von Videos, Lernprogramme und erweiterte Dokumentation zum Optimieren der Ergebnisse der Entity Framework treffen zu können.|
|[ASP.NET 5 Anwendung zur neuen Datenbank](https://docs.efproject.net/en/latest/platforms/aspnetcore/new-db.html)|Beschreibt die Erstellung eine neue ASP.NET 5-Anwendung mithilfe von Entity Framework-7.|

## <a name="see-also"></a>Siehe auch

- [Visual Studio-Datentools für .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)