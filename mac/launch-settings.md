---
title: Unterstützung für „launchSettings.json“
description: In diesem Artikel wird die Unterstützung der Datei „launchSettings.json“ in Visual Studio für Mac behandelt.
author: sayedihashimi
ms.author: sayedha
ms.date: 09/18/2019
ms.assetid: a556f9d7-86a8-408e-aa54-392584845889
ms.openlocfilehash: e7de368dd26bf2724a7bc060dade46422817da1e
ms.sourcegitcommit: ea182703e922c74725045afc251bcebac305068a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/24/2019
ms.locfileid: "71213816"
---
# <a name="launchsettingsjson"></a>launchSettings.json

Beim Entwickeln von ASP.NET Core-Projekten können Sie konfigurieren, wie Ihr Projekt in Entwicklungsszenarios gestartet werden soll, indem Sie den Inhalt der `launchSettings.json`-Datei anpassen. Sie können diese Datei in Visual Studio für Mac anpassen, indem Sie die Benutzeroberfläche für Projektoptionen verwenden oder die `launchSettings.json`-Datei direkt bearbeiten. Bei dieser Datei handelt es sich um dieselbe Konfigurationsdatei, die auch für Visual Studio unter Windows oder mithilfe von `dotnet` über die Befehlszeile verwendet werden kann. Diese Datei wird in Ihrem Projekt im Ordner `Properties` gespeichert.

Ausführlichere Informationen finden Sie unter [Verwenden von mehreren Umgebungen in ASP.NET Core](https://docs.microsoft.com/aspnet/core/fundamentals/environments). In dieser Dokumentation wird erläutert, wie Sie diese Datei in Visual Studio für Mac aktualisieren.

## <a name="updating-start-configuration-using-visual-studio-for-mac"></a>Aktualisieren der Startkonfiguration mithilfe von Visual Studio für Mac

Sie können die Datei `launchSettings.json` direkt in Visual Studio für Mac oder über die Projektoptionen bearbeiten. Klicken Sie mit der rechten Maustaste auf Ihr Projekt, und wählen Sie „Optionen“ aus, um zu den Projektoptionen zu gelangen. Siehe Abbildung unten.

![Optionen im Kontextmenü des Projekts ausgewählt](media/vsmac-ctx-proj-options.png)

Klicken Sie in diesem Dialogfeld auf „Ausführen > Konfigurationen > Standard“.

![Ausführen der Standardkonfigurationen](media/vsmac-run-config-default.png)

Hier konfigurieren Sie hauptsächlich zwei Dinge:

 - Beim Start festgelegte Umgebungsvariablen
 - Die Start-URL für das Projekt

## <a name="configure-environment-variables"></a>Konfigurieren von Umgebungsvariablen

Sie können das Raster verwenden, um Werte für Umgebungsvariablen festzulegen. Diese Umgebungsvariablen werden festgelegt, wenn Sie die Anwendung in Visual Studio für Mac starten. Beim Entwickeln von ASP.NET Core-Anwendungen sollten Sie die spezielle Umgebungsvariable `ASPNETCORE_ENVIRONMENT` beachten. Weitere Informationen finden Sie unter [Verwenden von mehreren Umgebungen in ASP.NET Core](https://docs.microsoft.com/aspnet/core/fundamentals/environments).


## <a name="configure-start-url"></a>Konfigurieren der Start-URL

Öffnen Sie die ASP.NET Core-Registerkarte, um die URL zu konfigurieren, mit der die Anwendung gestartet wird.

![Start-URL in den Projektoptionen](media/vsmac-run-config-default-aspnetcore.png)

Hier können Sie die URL(s) festlegen, auf die die Anwendung lauscht, wenn sie gestartet wird.