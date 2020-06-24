---
title: Daten Tools für .net
ms.date: 11/04/2016
ms.topic: overview
ms.assetid: c3175080-1dfb-4ab8-a460-92dadbb844b4
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
- dotnet
ms.openlocfilehash: 67cf4969a5db8900910b375d4cf560b1e30da4eb
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/23/2020
ms.locfileid: "85281070"
---
# <a name="visual-studio-data-tools-for-net"></a>Visual Studio-Datentools für .NET

Visual Studio und .net bieten eine umfassende Unterstützung für APIs und Tools zum Herstellen einer Verbindung mit Datenbanken, zum Modellieren von Daten im Arbeitsspeicher und zum Anzeigen der Daten auf der Benutzeroberfläche. Die .NET-Klassen, die Datenzugriffs Funktionen bereitstellen, werden als [ADO.net](/dotnet/framework/data/adonet/index)bezeichnet. ADO.net, zusammen mit den Daten Tools in Visual Studio, wurde hauptsächlich zur Unterstützung von relationalen Datenbanken und XML entwickelt. Heutzutage bieten viele nosql-Datenbankanbieter oder Drittanbieter ADO.NET-Anbieter an.

[.Net Core](/dotnet/core/) unterstützt ADO.net, mit Ausnahme von Datasets und den zugehörigen Typen. Wenn Sie .net Core als Ziel verwenden und eine ORM-Ebene (Object-Relational Mapping) benötigen, verwenden Sie [Entity Framework Core](/ef/core/).

Das folgende Diagramm zeigt eine vereinfachte Ansicht der grundlegenden Architektur:

![ADO.NET-Architektur](../data-tools/media/raddata-ado-net-architecture-diagram.png)

## <a name="typical-workflow"></a>Typischer Workflow

Der typische Workflow lautet wie folgt:

1. Installieren Sie eine Entwicklungs-oder Testdatenbank auf dem lokalen Computer. Weitere Informationen finden Sie unter [Installieren von Datenbanksystemen, Tools und Beispielen](../data-tools/installing-database-systems-tools-and-samples.md). Wenn Sie einen Azure-Datendienst verwenden, ist dieser Schritt nicht erforderlich.

2. Testen Sie die Verbindung mit der Datenbank (oder dem Dienst oder der lokalen Datei) in Visual Studio. Siehe [Hinzufügen neuer Verbindungen](../data-tools/add-new-connections.md).

3. Optionale Verwenden Sie die-Tools, um ein neues Modell zu generieren und zu konfigurieren. Modelle, die auf Entity Framework basieren, sind die Standard Empfehlung für neue Anwendungen. Das Modell, das Sie verwenden, ist die Datenquelle, mit der die Anwendung interagiert. Das Modell befindet sich logisch zwischen der Datenbank oder dem Dienst und der Anwendung. Siehe [Hinzufügen neuer Datenquellen](../data-tools/add-new-data-sources.md).

4. Ziehen Sie die Datenquelle aus dem **Datenquellen** Fenster auf eine Windows Forms-, ASP.net-oder Windows Presentation Foundation-Entwurfs Oberfläche, um den Daten Bindungs Code zu generieren, der die Daten für den Benutzer auf die von Ihnen angegebene Weise anzeigt. Siehe [Binden von Steuerelementen an Daten in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md).

5. Fügen Sie benutzerdefinierten Code für Dinge wie Geschäftsregeln, Suche und Datenvalidierung hinzu, oder verwenden Sie benutzerdefinierte Funktionen, die von der zugrunde liegenden Datenbank verfügbar gemacht werden.

Sie können Schritt 3 überspringen und eine .NET-Anwendung programmieren, um Befehle direkt an eine Datenbank auszugeben, anstatt ein Modell zu verwenden. In diesem Fall finden Sie hier auf die entsprechende Dokumentation: [ADO.NET](/dotnet/framework/data/adonet/index). Beachten Sie, dass Sie den **Assistenten zum Konfigurieren von Datenquellen** und Designer weiterhin verwenden können, um Daten Bindungs Code zu generieren, wenn Sie Ihre eigenen Objekte im Arbeitsspeicher auffüllen und anschließend Daten der Benutzeroberflächen-Steuerelemente an diese Objekte binden.

## <a name="see-also"></a>Weitere Informationen

- [Zugreifen auf Daten in Visual Studio](../data-tools/accessing-data-in-visual-studio.md)
