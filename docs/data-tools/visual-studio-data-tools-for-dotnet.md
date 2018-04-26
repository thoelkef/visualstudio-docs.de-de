---
title: Visual Studio-Tools mit Daten für .NET
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: c3175080-1dfb-4ab8-a460-92dadbb844b4
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
- dotnet
ms.openlocfilehash: d2db4210085e3dc16d9c4b9e00653312ae0d5a82
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
---
# <a name="visual-studio-data-tools-for-net"></a>Visual Studio-Tools mit Daten für .NET

Visual Studio und .NET Framework geben zusammen eine umfangreiche API und toolunterstützung ist für das Herstellen einer Verbindung mit Datenbanken und Modellieren von Daten im Arbeitsspeicher zum Anzeigen der Daten in der Benutzeroberfläche. .NET Framework-Klassen, die Datenzugriffs-Funktionalität bereitstellen, werden als bezeichnet [ADO.NET](/dotnet/framework/data/adonet/index). ADO.NET, zusammen mit den Daten in Visual Studio-Tools wurde ursprünglich entworfen, in erster Linie zum Unterstützen von relationalen Datenbanken und XML. Heutzutage bieten viele NoSQL-Datenbankhersteller oder Drittanbieter, ADO.NET-Anbietern.

[.NET Core](/dotnet/core/) ADO.NET, mit Ausnahme von Datasets und verwandte Typen unterstützt. Wenn Sie .NET Core als Ziel dient, erfordern eine ORM (Objektrelationales Mapping)-Ebene verwenden [Entity Framework Core](/ef/core/).

Das folgende Diagramm zeigt eine vereinfachte Ansicht die grundlegende Architektur:

![ADO.NET-Architektur](../data-tools/media/raddata-ado-net-architecture-diagram.png)

Der typische Arbeitsablauf umfasst dies:

1. Installieren der Entwicklungs- oder Testdatenbank auf dem lokalen Computer an. Finden Sie unter [Datenbanksystemen, Tools und Beispiele installieren](../data-tools/installing-database-systems-tools-and-samples.md). Wenn Sie einen Azure-Datendienst verwenden, ist dieser Schritt nicht erforderlich.

2. Testen Sie die Verbindung mit der Datenbank (oder Dienst oder lokale Datei) in Visual Studio. Finden Sie unter [neue Verbindungen hinzufügen](../data-tools/add-new-connections.md).

3. (Optional) Verwenden Sie die Tools zum Generieren und konfigurieren ein neues Modell aus. Modelle auf Grundlage von Entity Framework werden die Standard-Empfehlung für neue Anwendungen. Das Modell, einem Sie verwenden, ist die Datenquelle, der die Anwendung interagiert. Das Modell befindet sich logisch zwischen der Datenbank oder der Dienst und die Anwendung. Finden Sie unter [neue Datenquellen hinzufügen](../data-tools/add-new-data-sources.md).

4. Ziehen Sie die Datenquelle aus der **Datenquellen** auf einem Windows Forms, ASP.NET oder Windows Presentation Foundation-Entwurfsoberfläche, um den Code die Datenbindung zu generieren, die die Daten für den Benutzer auf die Weise angezeigt werden, die Sie angeben. Finden Sie unter [Binden von Steuerelementen an Daten in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md).

5. Hinzufügen von benutzerdefiniertem Code für Elemente, wie Geschäftsregeln, Suche und Überprüfen von Daten oder benutzerdefinierte Funktionen nutzen, die die zugrunde liegenden Datenbank verfügbar macht.

Überspringen Sie Schritt 3 und Programmieren Sie eine Anwendung .NET Befehle direkt an eine Datenbank, sondern mithilfe eines Modells. In diesem Fall finden Sie hier die relevante Dokumentation: [ADO.NET](/dotnet/framework/data/adonet/index). Beachten Sie, dass Sie weiterhin verwenden können die Datenquellen-Konfigurations-Assistenten und Designer Datenbindungsfunktionen Code zu generieren, wenn Sie Ihre eigenen Objekte im Arbeitsspeicher und dann binden Sie-Benutzeroberflächen-Steuerelemente mit diesen Objekten aufzufüllen.

## <a name="see-also"></a>Siehe auch

- [Zugreifen auf Daten in Visual Studio](../data-tools/accessing-data-in-visual-studio.md)