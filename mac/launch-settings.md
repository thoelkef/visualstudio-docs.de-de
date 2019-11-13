---
title: Unterstützung für „launchSettings.json“
description: In diesem Artikel wird die Unterstützung der Datei „launchSettings.json“ in Visual Studio für Mac behandelt.
author: sayedihashimi
ms.author: sayedha
ms.date: 09/18/2019
ms.assetid: a556f9d7-86a8-408e-aa54-392584845889
ms.openlocfilehash: d35bfed901dca960ae21b4e2cf2fa75067c1b3ee
ms.sourcegitcommit: ba0fef4f5dca576104db9a5b702670a54a0fcced
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/07/2019
ms.locfileid: "73715937"
---
# <a name="launchsettingsjson"></a>launchSettings.json

Beim Entwickeln von ASP.NET Core-Projekten können Sie konfigurieren, wie Ihr Projekt in Entwicklungsszenarios gestartet werden soll, indem Sie den Inhalt der launchSettings.json-Datei anpassen. Sie können diese Datei in Visual Studio für Mac anpassen, indem Sie die Benutzeroberfläche für Projektoptionen verwenden oder sie direkt bearbeiten. Bei dieser Datei handelt es sich um dieselbe Konfigurationsdatei, die Sie auch für Visual Studio unter Windows oder mithilfe von `dotnet` über die Befehlszeile verwenden können. Diese Datei wird in Ihrem Projekt im Ordner „Eigenschaften“ gespeichert.

Ausführlichere Informationen finden Sie unter [Verwenden von mehreren Umgebungen in ASP.NET Core](/aspnet/core/fundamentals/environments). In diesem Artikel wird erläutert, wie Sie diese Datei in Visual Studio für Mac aktualisieren.

## <a name="update-the-start-configuration-by-using-visual-studio-for-mac"></a>Aktualisieren der Startkonfiguration mithilfe von Visual Studio für Mac

Sie können die Datei „launchSettings.json“ direkt in Visual Studio für Mac oder über die Projektoptionen bearbeiten. Klicken Sie mit der rechten Maustaste auf Ihr Projekt, und wählen Sie **Optionen** aus, um zu den Projektoptionen zu gelangen.

![Kontextmenü für das Projekt mit „Optionen“ ausgewählt](media/vsmac-ctx-proj-options.png)

Klicken Sie auf **Ausführen** > **Konfigurationen** > **Standard**.

![„Ausführen“, „Konfigurationen“ und „Standard“ in den Projektoptionen](media/vsmac-run-config-default.png)

In erster Linie konfigurieren Sie zwei Dinge:

 - Umgebungsvariablen
 - Die App-URL für das Projekt

## <a name="configure-environment-variables"></a>Konfigurieren von Umgebungsvariablen

Sie können das Raster verwenden, um Werte für Umgebungsvariablen festzulegen. Diese Umgebungsvariablen werden festgelegt, wenn Sie die Anwendung in Visual Studio für Mac starten. Beim Entwickeln von ASP.NET Core-Anwendungen sollten Sie die spezielle Umgebungsvariable `ASPNETCORE_ENVIRONMENT` beachten. Weitere Informationen finden Sie unter [Verwenden von mehreren Umgebungen in ASP.NET Core](/aspnet/core/fundamentals/environments).


## <a name="configure-the-start-url"></a>Konfigurieren der Start-URL

Öffnen Sie die **ASP.NET Core**-Registerkarte, um die URL zu konfigurieren, mit der die Anwendung gestartet wird.

![Anwendungs-URL in den Projektoptionen](media/vsmac-run-config-default-aspnetcore.png)

Hier können Sie die URL festlegen, auf die die Anwendung lauscht, wenn sie gestartet wird.