---
title: Datatools für .NET
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: c3175080-1dfb-4ab8-a460-92dadbb844b4
author: gewarren
ms.author: gewarren
manager: jillfra
ms.prod: visual-studio-dev15
ms.workload:
- data-storage
- dotnet
ms.openlocfilehash: a8cca5d3ff93612e17750caa303db386616a6573
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54923479"
---
# <a name="visual-studio-data-tools-for-net"></a>Visual Studio-Datentools für .NET

Visual Studio und .NET Framework bieten zusammen umfangreiche API und toolunterstützung für die Verbindung mit Datenbanken und Modellieren von Daten im Arbeitsspeicher zum Anzeigen der Daten in der Benutzeroberfläche. .NET Framework-Klassen, die Datenzugriff-Funktionalität bereitstellen, werden als bezeichnet [ADO.NET](/dotnet/framework/data/adonet/index). ADO.NET, zusammen mit den Daten, die in Visual Studio-Tools wurde entwickelt, hauptsächlich als Unterstützung für relationale Datenbanken und XML. Heutzutage bieten viele NoSQL-Datenbank-Anbieter oder von Dritten, ADO.NET-Anbieter gewährleistet.

[.NET Core](/dotnet/core/) ADO.NET, mit Ausnahme von Datasets und verknüpfte Typen unterstützt. Wenn Sie .NET Core Anzielen und eine Ebene objektrelationales Mapping (ORM), verwenden Sie [Entity Framework Core](/ef/core/).

Das folgende Diagramm zeigt eine vereinfachte Ansicht der grundlegenden Architektur:

![ADO.NET-Architektur](../data-tools/media/raddata-ado-net-architecture-diagram.png)

## <a name="typical-workflow"></a>Typischer workflow

Der typische Arbeitsablauf umfasst dies:

1. Installieren Sie eine Entwicklungs- oder Testdatenbank auf dem lokalen Computer. Finden Sie unter [Installieren von Datenbanksystemen, Tools und Beispielen](../data-tools/installing-database-systems-tools-and-samples.md). Wenn Sie einen Azure Data Service verwenden, ist dieser Schritt nicht erforderlich.

2. Testen Sie die Verbindung mit der Datenbank (oder Dienst oder lokale Datei) in Visual Studio. Finden Sie unter [neue Verbindungen hinzufügen](../data-tools/add-new-connections.md).

3. (Optional) Verwenden Sie die Tools zum Generieren und konfigurieren ein neues Modell aus. Modelle auf Grundlage von Entity Framework sind die Empfehlung für neue Anwendungen. Das Modell, einem Sie verwenden, ist die Datenquelle, mit der die Anwendung interagiert. Das Modell befindet sich logisch zwischen der Datenbank "oder" Service "und" der Anwendung verwendet wird. Finden Sie unter [neue Datenquellen hinzufügen](../data-tools/add-new-data-sources.md).

4. Ziehen Sie die Datenquelle aus der **Datenquellen** Fenster auf einer Windows Forms, ASP.NET oder Windows Presentation Foundation-Entwurfsoberfläche, um den Code für die Datenbindung zu generieren, die die Daten für den Benutzer auf die Weise angezeigt werden, die Sie angeben. Finden Sie unter [Binden von Steuerelementen an Daten in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md).

5. Hinzufügen von benutzerdefiniertem Code für Aspekte wie Geschäftsregeln, Suche und datenüberprüfung oder benutzerdefinierte Funktionalität nutzen, die die zugrunde liegenden Datenbank verfügbar macht.

Sie können überspringen Sie Schritt 3 und Programmieren eine Anwendung .NET Befehle direkt an eine Datenbank, sondern mithilfe eines Modells. In diesem Fall finden Sie hier auf die entsprechende Dokumentation: [ADO.NET](/dotnet/framework/data/adonet/index). Beachten Sie, mit denen Sie immer noch die **Assistenten zur Datenquellenkonfiguration** und Designern, die Datenbindung-Code generieren, wenn Sie Ihre eigenen Objekte im Arbeitsspeicher, und klicken Sie dann eine Datenbindung von UI-Steuerelemente mit diesen Objekten aufzufüllen.

## <a name="see-also"></a>Siehe auch

- [Zugreifen auf Daten in Visual Studio](../data-tools/accessing-data-in-visual-studio.md)