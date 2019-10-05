---
title: Containerprotokolle, Umgebungsvariablen und Dateisystemzugriff
description: In diesem Artikel wird beschrieben, wie Sie Ihre Fähigkeiten zum Debuggen und Diagnostizieren Ihrer containerbasierten Apps in Visual Studio mithilfe eines Toolfensters verbessern, um zu erfahren, was innerhalb der Container geschieht, die Ihre App hosten.
author: ghogen
ms.author: ghogen
ms.topic: conceptual
ms.date: 05/06/2019
ms.technology: vs-azure
monikerRange: vs-2019
ms.openlocfilehash: 3fb9a52f990a2e492c63a6e71a7cc2063110c816
ms.sourcegitcommit: 44e9b1d9230fcbbd081ee81be9d4be8a485d8502
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/30/2019
ms.locfileid: "71126094"
---
# <a name="how-to-view-and-diagnose-containers-in-visual-studio"></a>Anzeigen und Diagnostizieren von Containern in Visual Studio

Mithilfe des Fensters **Container** können Sie anzeigen, was in den Containern passiert, die Ihre App hosten. Wenn Sie gewohnt sind, die Eingabeaufforderung zum Ausführen von Docker-Befehlen zu verwenden, um die Vorgänge in Ihren Containern anzuzeigen und zu diagnostizieren, wird sich dieses Fenster als praktischere Möglichkeit zum Überwachen Ihrer Container erweisen, ohne dass Sie die Visual Studio-IDE verlassen müssen.

> [!NOTE]
> Das Containerfenster steht derzeit als Vorschauerweiterung zur Verfügung, die Sie Visual Studio 2019 [herunterladen](https://aka.ms/vscontainerspreview) können.

## <a name="prerequisites"></a>Erforderliche Komponenten

- [Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-windows)
- Installation von [Visual Studio 2019](https://visualstudio.microsoft.com/downloads)
- Installation der [Containerfenstererweiterung](https://aka.ms/vscontainerspreview)

## <a name="view-information-about-your-containers"></a>Anzeigen von Informationen zu den Containern

Das Fenster **Container** wird automatisch geöffnet, wenn Sie ein .NET-Containerprojekt starten. Drücken Sie **STRG**+**Q**, um das Visual Studio-Suchfeld zu aktivieren, geben Sie `Containers` ein, und wählen Sie das erste Element aus, um Ihre Container jederzeit in Visual Studio anzuzeigen. Sie können das **Containerfenster** auch über das Hauptmenü öffnen. Verwenden Sie den Menüpfad **Ansicht** > **Weitere Fenster** > **Container**.  

![Screenshot: Registerkarte „Umgebung“ im Containerfenster](media/view-and-diagnose-containers/container-window.png)

Auf der linken Seite wird die Liste der Container auf Ihrem lokalen Computer angezeigt. Die Container, die Ihrer Projektmappe zugeordnet sind, werden unter **Lösungscontainer** angezeigt. Auf der rechten Seite wird ein Bereich mit den Registerkarten **Umgebung**, **Ports**, **Protokolle** und **Dateien** angezeigt.

> [!TIP]
> Sie können mühelos anpassen, wo das Toolfenster **Container** in Visual Studio andocken soll. Informationen dazu finden Sie unter [Anpassen von Fensterlayouts in Visual Studio](/visualstudio/ide/customizing-window-layouts-in-visual-studio). Das Fenster **Container** ist standardmäßig an das **Überwachungsfenster** angedockt, wenn der Debugger ausgeführt wird.

## <a name="view-environment-variables"></a>Anzeigen von Umgebungsvariablen

Auf der Registerkarte **Umgebung** werden die Umgebungsvariablen im Container angezeigt. Sie können diese Variablen auf vielerlei Weisen für den Container Ihrer App festlegen, z. B. in der Dockerfile, in einer ENV-Datei oder mithilfe der Option „-e“, wenn Sie einen Container mithilfe eines Docker-Befehls starten.

![Screenshot: Registerkarte „Umgebung“ im Containerfenster](media/view-and-diagnose-containers/container-environment-vars.png)

> [!NOTE]
> Änderungen an den Umgebungsvariablen werden nicht in Echtzeit wiedergegeben. Außerdem handelt es sich bei den Umgebungsvariablen auf dieser Registerkarte um Systemumgebungsvariablen im Container, die nicht den lokalen Benutzerumgebungsvariablen der App entsprechen.

## <a name="view-port-mappings"></a>Anzeigen von Portzuordnungen

Auf der Registerkarte **Ports** können Sie die Portzuordnungen überprüfen, die für Ihren Container konfiguriert sind.

![Screenshot: Registerkarte „Ports“ im Containerfenster](media/view-and-diagnose-containers/container-ports.png)

Bekannte Ports sind verknüpft. Wenn also Inhalt für einen Port verfügbar ist, können Sie auf den Link klicken, um den Browser zu öffnen.

## <a name="view-logs"></a>Protokoll anzeigen...

Auf der Registerkarte **Protokolle** werden die Ergebnisse des `docker logs`-Befehls angezeigt. Auf der Registerkarte werden standardmäßig die Datenströme „stdout“ und „stderr“ für einen Container angezeigt, aber Sie können die Ausgabe konfigurieren. Weitere Informationen finden Sie unter [Docker-Protokollierung](https://docs.docker.com/config/containers/logging/).  Auf der Registerkarte **Protokolle** werden die Protokolle standardmäßig in Echtzeit angezeigt. Sie können dies jedoch deaktivieren, indem Sie auf der Registerkarte auf **Stoppen** klicken.

![Screenshot: Registerkarte „Protokolle“ im Containerfenster](media/view-and-diagnose-containers/containers-logs.jpg)

Klicken Sie auf der Registerkarte **Protokolle** auf **Löschen**, um die Protokolle zu löschen.  Klicken Sie auf **Aktualisieren**, um alle Protokolle abzurufen.

> [!NOTE]
> Visual Studio leitet „stdout“ und „stderr“ automatisch an das **Ausgabefenster** weiter, also werden für Container, die über Visual Studio gestartet werden (d. h. die Container im Abschnitt **Lösungscontainer**), keine Protokolle auf dieser Registerkarte angezeigt. Verwenden Sie stattdessen das **Ausgabefenster**.

## <a name="view-the-filesystem"></a>Anzeigen des Dateisystems

Auf der Registerkarte **Dateien** können Sie das Dateisystem des Containers sowie den App-Ordner anzeigen, der Ihr Projekt enthält.

![Screenshot: Registerkarte „Dateien“ im Containerfenster](media/view-and-diagnose-containers/container-filesystem.png)

Navigieren Sie zur Datei, und doppelklicken Sie auf diese, oder klicken Sie mit der rechten Maustaste auf die Datei, und wählen Sie **Öffnen** aus, um Dateien in Visual Studio zu öffnen. Visual Studio öffnet Dateien im schreibgeschützten Modus.

![Screenshot: Anzeige der geöffneten Datei in Visual Studio](media/view-and-diagnose-containers/container-file-open.png)

Auf der Registerkarte **Dateien** können Sie Anwendungsprotokolle wie IIS-Protokolle, Konfigurationsdateien und andere Inhaltsdateien im Dateisystem Ihres Containers anzeigen.

## <a name="start-stop-and-remove-containers"></a>Starten, Stoppen und Entfernen von Containern

Im Fenster **Container** werden standardmäßig alle Container auf dem Computer angezeigt, die von Docker verwaltet werden. Sie können die Symbolleistenschaltflächen zum Starten, Stoppen und Entfernen (Löschen) eines Containers verwenden, den Sie nicht mehr benötigen.  Diese Liste wird dynamisch aktualisiert, wenn Container erstellt oder entfernt werden.

## <a name="next-steps"></a>Nächste Schritte

Erfahren Sie mehr über die Containertools in Visual Studio in der [Übersicht über Containertools](overview.md).

## <a name="see-also"></a>Siehe auch

[Containerentwicklung in Visual Studio](/visualstudio/containers)

[Marketplace für Visual Studio-Erweiterungen](https://marketplace.visualstudio.com/)
