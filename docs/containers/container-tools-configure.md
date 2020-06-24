---
title: Konfigurieren von Visual Studio-Containertools
description: Erfahren Sie, wie Sie die in Visual Studio verfügbaren Tools zum Arbeiten mit Docker-Container konfigurieren.
author: ghogen
ms.author: ghogen
ms.topic: how-to
ms.date: 03/20/2019
ms.technology: vs-azure
ms.openlocfilehash: d2b3e2821e7697ad53b10a7148c22140aa1a07af
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/23/2020
ms.locfileid: "85283215"
---
# <a name="how-to-configure-visual-studio-container-tools"></a>Konfigurieren von Visual Studio-Containertools

Mithilfe der Visual Studio-Einstellungen können Sie bestimmte Eigenschaften festlegen, die darüber entscheiden, wie Visual Studio mit Docker-Containern zusammenarbeitet. Beispielsweise können Sie die Einstellungen für die Leistung und den Ressourcenverbrauch anpassen.

## <a name="container-tools-settings"></a>Einstellungen für Containertools

Wählen Sie im Hauptmenü **Extras > Optionen** aus, und klappen Sie **Containertools > Einstellungen** auf. Die Einstellungen der Containertools werden angezeigt.

::: moniker range="vs-2017"

![Optionen für Visual Studio Containertools: „Erforderliche Docker-Images beim Laden des Projekts automatisch abrufen“, „Container im Hintergrund automatisch starten“, „Beim Schließen der Lösung Container automatisch beenden“ und „Nicht nach Vertrauenswürdigkeit von SSL-Zertifikaten fragen“.](./media/overview/visual-studio-docker-tools-options.png)
::: moniker-end

::: moniker range=">=vs-2019"

Einstellungen unter **Allgemein** für Containertools:

![Optionen für Visual Studio-Containertools: „Installieren Sie bei Bedarf Docker für Windows“ und „ASP.NET Core-SSL-Zertifikat als vertrauenswürdig einstufen“.](./media/configure-container-tools/tools-options-1.png)

Einstellungen unter **Einzelnes Projekt** und **Docker Compose** für Containertools:

![Optionen für Visual Studio-Containertools: „Container beim Schließen des Projekts beenden“, „Erforderliche Docker-Images beim Öffnen des Projekts mithilfe von Pull übertragen“ und „Container beim Öffnen des Projekts ausführen“.](./media/configure-container-tools/tools-options-2.png)
::: moniker-end

Die folgende Tabelle hilft Ihnen möglicherweise beim Festlegen dieser Optionen.

::: moniker range="vs-2017"
| name | Standardeinstellung | Gilt für | Beschreibung |
| -----|:---------------:|:----------:| ----------- |
| Erforderliche Docker-Images beim Laden des Projekts automatisch abrufen | Ein | Docker Compose | Zum Steigern der Leistung beim Laden von Projekten beginnt Visual Studio einen Docker-Pull-Vorgang im Hintergrund, sodass das Image bereits heruntergeladen ist oder heruntergeladen wird, wenn Sie zur Ausführung Ihres Codes bereit sind. Wenn Sie lediglich Projekte laden und Code durchsuchen, können Sie dies ausschalten, um das Herunterladen von Containerimages zu vermeiden, die Sie nicht benötigen. |
| Container im Hintergrund automatisch starten | Ein | Docker Compose | Ebenfalls zum Steigern der Leistung erstellt Visual Studio einen Container mit Volumeeinbindungen, die bereit stehen, wenn Sie Ihren Container erstellen und ausführen. Wenn Sie steuern möchten, wann Ihr Container erstellt wird, deaktivieren Sie diese Option. |
| Beim Schließen der Lösung Container automatisch beenden | Ein | Docker Compose | Deaktivieren Sie diese Option, wenn Container für Ihre Projektmappe nach dem Schließen von Projektmappe oder Visual Studio weiter ausgeführt werden sollen. |
| Nicht nach Vertrauenswürdigkeit des localhost-SSL-Zertifikats fragen | Aus | ASP.NET Core 2.1-Projekte | Wenn das localhost-SSL-Zertifikat nicht vertrauenswürdig ist, benachrichtigt Visual Studio Sie bei jeder Ausführung Ihres Projekts, sofern dieses Kontrollkästchen nicht aktiviert ist. |
::: moniker-end

::: moniker range=">=vs-2019"

Die Einstellungen unter **Allgemein** sind in der folgenden Tabelle beschrieben:

| name | Standardeinstellung | Gilt für | Beschreibung |
| -----|:---------------:|:----------:| ----------- |
| Installieren Sie bei Bedarf Docker für Windows | Aufforderung | Einzelnes Projekt, Docker Compose | Wählen Sie aus, ob eine Benachrichtigung angezeigt werden soll, wenn Docker Desktop nicht installiert ist. |
| ASP.NET Core-SSL-Zertifikat als vertrauenswürdig einstufen | Aufforderung | ASP.NET Core 2.x-Projekte | Wenn **Aufforderung** aktiviert und das Localhost-SSL-Zertifikat nicht vertrauenswürdig ist, benachrichtigt Visual Studio Sie bei jeder Ausführung Ihres Projekts. |

In der folgenden Tabelle werden die Einstellungen unter **Einzelnes Projekt** und **Docker Compose** beschrieben:

| name | Standardeinstellung | Gilt für | Beschreibung |
| -----|:---------------:|:----------:| ----------- |
| Erforderliche Docker-Images beim Öffnen des Projekts mithilfe von Pull übertragen | True | Einzelnes Projekt, Docker Compose | Zum Steigern der Leistung beim Laden von Projekten beginnt Visual Studio einen Docker-Pull-Vorgang im Hintergrund, sodass das Image bereits heruntergeladen ist oder heruntergeladen wird, wenn Sie zur Ausführung Ihres Codes bereit sind. Wenn Sie lediglich Projekte laden und Code durchsuchen, können Sie **False** festlegen, um das Herunterladen von Containerimages zu vermeiden, die Sie nicht benötigen. |
| Container beim Öffnen des Projekts ausführen | True | Einzelnes Projekt, Docker Compose | Visual Studio nutzt einen Ahead-of-time-Prozess zur Erstellung eines Containers, der bereitsteht, wenn Sie Ihren Container erstellen und ausführen. Auch diese Maßnahme dient der Leistungsoptimierung. Wenn Sie steuern möchten, wann Ihr Container erstellt wird, legen Sie **False** fest. |
| „Stop containers on project close“ (Container beim Schließen des Projekts beenden) | True | Einzelnes Projekt und Docker Compose | Legen Sie **False** fest, wenn Container für Ihre Projektmappe weiter ausgeführt werden sollen, nachdem die Projektmappe oder Visual Studio geschlossen wurde. |

::: moniker-end
> [!WARNING]
> Wenn das Localhost-SSL-Zertifikat nicht vertrauenswürdig ist und Sie das Kontrollkästchen aktivieren, um die Benachrichtigung zu unterdrücken, treten in Ihrer App oder Ihrem Dienst bei HTTPS-Webanforderungen zur Laufzeit möglicherweise Fehler auf. Deaktivieren Sie in diesem Fall das **Nicht fragen**-Kontrollkästchen, führen Sie Ihr Projekt aus, und drücken Sie bei der Aufforderung Ihr Vertrauen aus.

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zum Arbeiten mit Containern in Visual Studio finden Sie in der [Übersicht](overview.md).