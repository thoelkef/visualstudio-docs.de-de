---
title: 'Docker-Tutorial-Teil 1: Erstellen und Ausführen der Beispiel-App für TODO-Listen'
description: Übersicht über die ToDo List-Beispiel-APP, die in Node.js ausgeführt wird.
ms.date: 08/04/2020
author: nebuk89
ms.author: ghogen
manager: jillfra
ms.technology: vs-azure
ms.topic: conceptual
ms.workload:
- azure
ms.openlocfilehash: b8470c8d7708bc51916a6f57f5aa135c3267e355
ms.sourcegitcommit: c4212f40df1a16baca1247cac2580ae699f97e4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/31/2020
ms.locfileid: "89176742"
---
# <a name="build-and-run-the-todo-sample-app"></a>Erstellen und Ausführen der TODO-Beispiel-App

Im weiteren Verlauf dieses Tutorials arbeiten Sie mit einem einfachen Todo List Manager, der in Node.js ausgeführt wird. Wenn Sie mit Node.js nicht vertraut sind, machen Sie sich keine Sorgen! Es sind keine echten JavaScript-Kenntnisse erforderlich!

An diesem Punkt ist Ihr Entwicklungsteam sehr klein, und Sie entwickeln einfach eine APP, um Ihren MVP (minimal brauchbares Produkt) zu beweisen. Sie möchten zeigen, wie es funktioniert und was es tun kann, ohne sich Gedanken darüber machen zu müssen, wie es für ein großes Team, mehrere Entwickler usw. funktioniert.

![Bildschirm Abbildung von ToDo List Manager](media/todo-list-sample.png)

## <a name="get-the-app"></a>Abrufen der App

Bevor Sie die Anwendung ausführen können, müssen Sie den Quellcode der Anwendung auf Ihren Computer herunterladen. Bei echten Projekten Klonen Sie das Repository in der Regel. In diesem Tutorial haben Sie jedoch eine ZIP-Datei mit der Anwendung erstellt.

1. [Herunterladen der ZIP](/assets/app.zip)-Datei. Öffnen Sie die ZIP-Datei, und stellen Sie sicher, dass Sie den Inhalt extrahieren.

1. Verwenden Sie nach dem Extrahieren Ihren bevorzugten Code-Editor, um das Projekt zu öffnen. Wenn Sie einen Editor benötigen, können Sie [Visual Studio Code](https://code.visualstudio.com/)verwenden. Das `package.json` und die beiden Unterverzeichnisse ( `src` und) sollten angezeigt werden `spec` .

    ![Screenshot der Visual Studio Code mit geladener app geöffnet](media/ide-screenshot.png)

## <a name="building-the-apps-container-image"></a>Das Container Image der APP wird aufgebaut.

Um die Anwendung zu erstellen, müssen Sie eine verwenden `Dockerfile` . Eine dockerfile-Datei ist einfach ein textbasiertes Skript mit Anweisungen, die zum Erstellen eines Container Images verwendet werden. Wenn Sie zuvor dockerfiles erstellt haben, werden möglicherweise einige Fehler in der dockerfile-Datei unten angezeigt. Aber keine Sorge! Wir werden Sie übernehmen.

1. Erstellen Sie eine Datei `Dockerfile` mit dem Namen im selben Ordner wie die Datei `package.json` mit dem folgenden Inhalt.

    ```dockerfile
    FROM node:12-alpine
    WORKDIR /app
    COPY . .
    RUN yarn install --production
    CMD ["node", "/app/src/index.js"]
    ```

    Überprüfen Sie, ob die Datei `Dockerfile` keine Dateierweiterung wie hat `.txt` . Einige Editoren können diese Dateierweiterung automatisch anfügen, was zu einem Fehler im nächsten Schritt führen würde.

1. Wenn Sie dies nicht bereits getan haben, öffnen Sie ein Terminal, und wechseln Sie zum `app` Verzeichnis mit dem `Dockerfile` . Erstellen Sie nun das Container Image mit dem `docker build` Befehl.

    ```bash
    docker build -t getting-started .
    ```

    Dieser Befehl verwendet die dockerfile-Datei, um ein neues Container Image zu erstellen. Vielleicht haben Sie bemerkt, dass viele "Ebenen" heruntergeladen wurden. Dies liegt daran, dass Sie den Generator angewiesen haben, dass Sie aus dem Image starten möchten `node:12-alpine` . Da Sie das jedoch nicht auf Ihrem Computer haben, musste dieses Image heruntergeladen werden.

    Nachdem das Abbild heruntergeladen wurde, haben Sie in Ihre Anwendung kopiert und `yarn` zum Installieren der Abhängigkeiten Ihrer Anwendung verwendet. Die- `CMD` Direktive gibt den Standardbefehl an, der ausgeführt wird, wenn ein Container aus diesem Bild gestartet wird.

    Schließlich markiert das `-t` Flag das Image. Stellen Sie sich dies einfach als lesbarer Name für das endgültige Bild vor. Da Sie das Bild benannt `getting-started` haben, können Sie auf dieses Bild verweisen, wenn Sie einen Container ausführen.

    Der `.` am Ende des `docker build` Befehls weist darauf hin, dass docker im aktuellen Verzeichnis nach dem suchen soll `Dockerfile` .

## <a name="starting-an-app-container"></a>Starten eines App-Containers

Nachdem Sie nun über ein Image verfügen, führen Sie die Anwendung aus. Verwenden Sie hierzu den `docker run` Befehl (denken Sie daran, dass von oben?).

1. Starten Sie den Container mithilfe des `docker run` Befehls, und geben Sie den Namen des soeben erstellten Images an:

    ```bash
    docker run -dp 3000:3000 getting-started
    ```

    Erinnern Sie sich an die `-d` `-p` Flags und? Sie führen den neuen Container im abgetrennten Modus (im Hintergrund) aus und erstellen eine Zuordnung zwischen dem Port 3000 des Hosts und dem Port 3000 des Containers. Ohne die Port Zuordnung sind Sie nicht in der Lage, auf die Anwendung zuzugreifen.

1. Öffnen Sie nach einigen Sekunden den Webbrowser in [http://localhost:3000](http://localhost:3000) .
    Die APP sollte angezeigt werden.

    ![Leere TODO-Liste](media/todo-list-empty.png)

1. Fügen Sie ein Element oder zwei Elemente hinzu, und sehen Sie, dass es erwartungsgemäß funktioniert. Sie können Elemente als Complete markieren und Elemente entfernen. Das Front-End speichert Elemente erfolgreich im Back-End. Ziemlich schnell und einfach?

An diesem Punkt sollten Sie über einen aktuell erstellten Todo List Manager mit einigen Elementen verfügen, die alle von Ihnen erstellt wurden. Nehmen wir nun einige Änderungen vor, und erfahren Sie mehr über die Verwaltung von Containern.

Wenn Sie die vs Code Erweiterung kurz betrachten, sollten Sie sehen, dass ihre zwei Container jetzt ausgeführt werden (dieses Tutorial und der neu gestartete App-Container).

![Docker-Erweiterung mit Tutorial und App-Containern, die ausgeführt werden](media/vs-two-containers.png)

## <a name="recap"></a>Zusammenfassung

In diesem kurzen Abschnitt haben Sie die Grundlagen zum Erstellen eines Container Images kennengelernt und eine dockerfile-Datei erstellt. Nachdem Sie ein Image erstellt haben, haben Sie den Container gestartet und die laufende APP gesehen.

Als nächstes nehmen Sie eine Änderung an der APP vor und erfahren, wie Sie die laufende Anwendung mit einem neuen Image aktualisieren. Dabei lernen Sie einige andere nützliche Befehle kennen.

## <a name="next-steps"></a>Nächste Schritte

Fahren Sie mit dem Tutorial fort.

> [!div class="nextstepaction"]
> [Aktualisieren der APP](update-your-app.md)