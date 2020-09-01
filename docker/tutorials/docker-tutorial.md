---
title: 'Docker-Tutorial: Einstieg in docker'
description: Ein mehrstufiges Tutorial, in dem die Grundlagen der Arbeit mit docker mit Visual Studio Code behandelt werden.
ms.date: 08/04/2020
author: nebuk89
ms.author: ghogen
manager: jillfra
ms.technology: vs-azure
ms.topic: conceptual
ms.workload:
- azure
next_page: app.md
ms.openlocfilehash: 9961810ad408a384db46439235b0b7acab325062
ms.sourcegitcommit: c4212f40df1a16baca1247cac2580ae699f97e4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/31/2020
ms.locfileid: "89176749"
---
# <a name="tutorial-get-started-with-docker"></a>Tutorial: Einstieg in docker

In diesem Tutorial erfahren Sie mehr über das Erstellen und Bereitstellen von Docker-apps, einschließlich der Verwendung mehrerer Container mit einer Datenbank und der Verwendung von Docker Compose. Außerdem stellen Sie Ihre containerisierte app in Azure bereit.

## <a name="start-the-tutorial"></a>Starten des Tutorials

Wenn Sie den Befehl bereits zum Einstieg in das Tutorial ausgeführt haben, herzlichen Glückwunsch!  Wenn nicht, öffnen Sie eine Eingabeaufforderung oder ein Bash-Fenster, und führen Sie den folgenden Befehl aus:

```cli
docker run -d -p 80:80 docker/getting-started
```

Sie werden feststellen, dass einige Flags verwendet werden. Hier finden Sie weitere Informationen dazu:

- `-d` -Ausführen des Containers im getrennten Modus (im Hintergrund)
- `-p 80:80` -Zuordnen von Port 80 des Hosts zu Port 80 im Container
- `docker/getting-started` -das zu verwendende Bild

> [!TIP]
> Sie können einzelne zeichenflags kombinieren, um den vollständigen Befehl zu verkürzen.
> Der obige Befehl könnte z. b. wie folgt geschrieben werden:
>
> ```cli
> docker run -dp 80:80 docker/getting-started
> ```

## <a name="the-vs-code-extension"></a>Die vs Code-Erweiterung

Bevor wir zu weit gehen, möchten wir die Docker-Erweiterung "vs Code" hervorheben, die Ihnen einen schnellen Überblick über die Container bietet, die auf Ihrem Computer ausgeführt werden. Sie ermöglicht Ihnen den schnellen Zugriff auf Container Protokolle, ermöglicht Ihnen das Abrufen einer Shell innerhalb des Containers und ermöglicht die einfache Verwaltung des Lebenszyklus von Containern ("Abbrechen", "entfernen" usw.).

Befolgen Sie die Anweisungen [hier](https://code.visualstudio.com/docs/containers/overview), um auf die Erweiterung zuzugreifen. Verwenden Sie das docker-Symbol auf der linken Seite, um die Docker-Ansicht zu öffnen. Wenn Sie die Erweiterung jetzt öffnen, wird dieses Tutorial ausgeführt! Der Container Name ( `angry_taussig` unten) ist ein zufällig erstellter Name. Daher haben Sie wahrscheinlich einen anderen Namen.

![Tutorial-Container in der Docker-Erweiterung](media/vs-tutorial-in-extension.png)

## <a name="what-is-a-container"></a>Was ist ein Container?

Nun, da Sie einen Container ausgeführt haben, was *ist* ein Container? Einfach ausgedrückt, handelt es sich bei einem Container einfach um einen anderen Prozess auf dem Computer, der von allen anderen Prozessen auf dem Host Computer isoliert ist. Diese Isolation nutzt [Kernel-Namespaces und cgroups](https://medium.com/@saschagrunert/demystifying-containers-part-i-kernel-space-2c53d6979504), Features, die seit längerer Zeit in Linux vorhanden sind. Docker hat damit gearbeitet, diese Funktionen zugänglich und benutzerfreundlich zu gestalten.

> [!NOTE]
> **Erstellen von Containern von Grund** auf Wenn Sie sehen möchten, wie Container von Grund auf neu erstellt werden, verfügt Liz Rice von Aqua Security über ein Video, in dem Sie einen Container von Grund auf neu erstellt:
>
> [!VIDEO https://www.youtube-nocookie.com/embed/8fi7uSYlOdc]

## <a name="what-is-a-container-image"></a>Was ist ein Container Image?

Beim Ausführen eines Containers wird ein isoliertes Dateisystem verwendet. Dieses benutzerdefinierte Dateisystem wird von einem **Container Image**bereitgestellt. Da das Image das Dateisystem des Containers enthält, muss es alles enthalten, was zum Ausführen einer Anwendung erforderlich ist. alle Abhängigkeiten, Konfigurationen, Skripts, Binärdateien usw. Das Image enthält auch weitere Konfigurationen für den Container, z. b. Umgebungsvariablen, einen Standardbefehl zum Ausführen und andere Metadaten.

Wir werden uns später ausführlicher mit den Bildern befassen, die Themen wie z. b. Schichten, bewährte Methoden und vieles mehr abdecken.

> [!NOTE]
> Wenn Sie mit vertraut sind `chroot` , betrachten Sie einen Container als erweiterte Version von `chroot` . Das Dateisystem stammt einfach aus dem Image. Ein Container bietet jedoch zusätzliche Isolation, die bei der einfachen Verwendung von chroot nicht verfügbar ist.

## <a name="next-steps"></a>Nächste Schritte

Fahren Sie mit dem Tutorial fort.

> [!div class="nextstepaction"]
> [Die Anwendung](your-application.md)
