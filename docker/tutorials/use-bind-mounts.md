---
title: 'Docker-Tutorial-Teil 5: Verwenden von BIND-bereit Stellungen'
description: Beschreibt die Verwendung von Bindungs Aufstellungen zum Steuern des Einbindungs Punkts auf dem Host.
ms.date: 08/04/2020
author: nebuk89
ms.author: ghogen
manager: jillfra
ms.technology: vs-azure
ms.topic: conceptual
ms.workload:
- azure
ms.openlocfilehash: 6474179a0714f2407ac37e724b997139206a91fb
ms.sourcegitcommit: c4212f40df1a16baca1247cac2580ae699f97e4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/31/2020
ms.locfileid: "89176741"
---
# <a name="use-bind-mounts"></a>Verwenden von Bindungs Zustellungen

Im vorherigen Kapitel haben Sie erfahren, wie Sie ein **benanntes Volume** verwendet haben, um die Daten in der Datenbank beizubehalten. Benannte Volumes sind hervorragend, wenn Sie einfach Daten speichern möchten, da Sie sich nicht darum kümmern müssen, *wo* die Daten gespeichert werden.

Mit **Bindungs**Bereitstellungen steuern Sie den genauen Bereitstellungspunkt auf dem Host. So können Sie Daten persistent speichern, werden jedoch häufig verwendet, um zusätzliche Daten in Containern bereitzustellen. Wenn Sie an einer Anwendung arbeiten, können Sie mit einer Bindungs Bindung Quellcode in den Container einbinden, um Codeänderungen anzuzeigen, zu reagieren und die Änderungen sofort anzuzeigen.

Bei Knoten basierten Anwendungen ist [nodemon](https://npmjs.com/package/nodemon) ein großartiges Tool zum Überwachen von Dateiänderungen und anschließendes Neustarten der Anwendung. In den meisten anderen Sprachen und Frameworks sind äquivalente Tools vorhanden.

## <a name="quick-volume-type-comparisons"></a>Kurze Volumentyp Vergleiche

Bindungs Zustellungen und benannte Volumes sind die zwei Haupttypen von Volumes, die in der Docker-Engine enthalten sind. Es sind jedoch zusätzliche Volumetreiber verfügbar, um andere Verwendungs Fälle ([SFTP](https://github.com/vieux/docker-volume-sshfs), [CEPH](https://ceph.com/geen-categorie/getting-started-with-the-docker-rbd-volume-plugin/), [nettapp](https://netappdvp.readthedocs.io/en/stable/), [S3](https://github.com/elementar/docker-s3-volume)usw.) zu unterstützen.

| Eigenschaft | Benannte Volumes | Binden von Bereitstellungen |
| -------- | ------------- | ----------- |
| Host Speicherort | Docker wählt | Steuerelement |
| Einstellungsbeispiel (mit `-v` ) | mein Volume:/usr/local/data | /path/to/data:/usr/local/data |
| Füllt neue Volumes mit Container Inhalten auf | Ja | Nein |
| Unterstützt Volumetreiber | Ja | Nein |

## <a name="start-a-dev-mode-container"></a>Starten eines Containers im dev-Modus

Führen Sie die folgenden Schritte aus, um den Container zur Unterstützung eines Entwicklungs Workflows auszuführen:

- Einbinden des Quellcodes in den Container
- Alle Abhängigkeiten installieren, einschließlich der "dev"-Abhängigkeiten
- Nodemon zum Überwachen von Dateisystem Änderungen starten

1. Stellen Sie sicher, dass keine vorherigen `getting-started` Container ausgeführt werden.

1. Führen Sie den folgenden Befehl aus (ersetzen Sie die ` \ ` Zeichen durch `` ` `` in Windows PowerShell). Anschließend erfahren Sie, was im folgenden geschieht:

    ```bash
    docker run -dp 3000:3000 \
        -w /app -v ${PWD}:/app \
        node:12-alpine \
        sh -c "yarn install && yarn run dev"
    ```

    - `-dp 3000:3000` -wie zuvor. Ausführen im getrennten Modus (Hintergrund) und Erstellen einer Port Zuordnung
    - `-w /app` : legt das Arbeitsverzeichnis oder das aktuelle Verzeichnis fest, aus dem der Befehl ausgeführt wird.
    - `-v ${PWD}:/app` -binden das aktuelle Verzeichnis vom Host im Container in das `/app` Verzeichnis einbinden
    - `node:12-alpine` : das zu verwendende Bild. Beachten Sie, dass dies das Basis Image für Ihre APP aus der dockerfile-Datei ist.
    - `sh -c "yarn install && yarn run dev"` -der Befehl. Wir starten eine Shell mit `sh` (Alpine ist nicht vorhanden `bash` ) und werden ausgeführt `yarn install` , um *alle* Abhängigkeiten zu installieren und dann ausgeführt zu werden `yarn run dev` . Wenn Sie in der sehen `package.json` , sehen Sie, dass das `dev` Skript gestartet wird `nodemon` .

1. Sie können die Protokolle mit überwachen `docker logs -f <container-id>` . Sie werden feststellen, dass Sie bereit sind, wenn Sie Folgendes sehen:

    ```bash
    docker logs -f <container-id>
    $ nodemon src/index.js
    [nodemon] 1.19.2
    [nodemon] to restart at any time, enter `rs`
    [nodemon] watching dir(s): *.*
    [nodemon] starting `node src/index.js`
    Using sqlite database at /etc/todos/todo.db
    Listening on port 3000
    ```

    Wenn Sie mit dem Überwachen der Protokolle fertig sind, beenden Sie den Vorgang `Ctrl` + `C` .

1. Nehmen Sie nun eine Änderung an der APP vor. Ändern Sie in der `src/static/js/app.js` Datei die Schaltfläche **Element hinzufügen** , um einfach die Schaltfläche **hinzu**fügen. Diese Änderung erfolgt in Zeile 109.

    ```diff
    -                         {submitting ? 'Adding...' : 'Add Item'}
    +                         {submitting ? 'Adding...' : 'Add'}
    ```

1. Aktualisieren Sie einfach die Seite (oder öffnen Sie Sie), und die Änderung sollte sich fast sofort im Browser widerspiegeln. Es kann einige Sekunden dauern, bis der Knoten Server neu gestartet wird. Wenn Sie also eine Fehlermeldung erhalten, versuchen Sie es nach einigen Sekunden erneut.

    ![Screenshot der aktualisierten Bezeichnung für die Schaltfläche "hinzufügen"](media/updated-add-button.png)

1. Sie können andere Änderungen vornehmen, die Sie vornehmen möchten. Wenn Sie fertig sind, beenden Sie den Container, und erstellen Sie das neue Image mithilfe von `docker build -t getting-started .` .

Die Verwendung von Bindungs Bereitstellungen ist für lokale Entwicklungseinrichtungen *sehr* üblich. Der Vorteil besteht darin, dass auf dem Entwicklungs Computer nicht alle Buildtools und-Umgebungen installiert sein müssen. Mit einem einzigen `docker run` Befehl wird die Entwicklungsumgebung abgerufen und ist einsatzbereit. In einem späteren Schritt erfahren Sie mehr über die Docker Compose, da dies zur Vereinfachung ihrer Befehle beiträgt (Sie erhalten bereits viele Flags).

## <a name="recap"></a>Zusammenfassung

An diesem Punkt können Sie Ihre Datenbank dauerhaft speichern und schnell auf die Anforderungen und Anforderungen Ihrer Investoren und Gründer reagieren. Hurra! Aber raten Sie? Sie haben großartige Neuigkeiten erhalten!

**Ihr Projekt wurde für die zukünftige Entwicklung ausgewählt!**

Um sich auf die Produktion vorzubereiten, müssen Sie die Datenbank von der Arbeit in SQLite zu einem anderen migrieren, der etwas besser skaliert werden kann. Der Einfachheit halber behalten Sie eine relationale Datenbank bei und wechseln Ihre Anwendung zur Verwendung von MySQL. Aber wie sollten Sie MySQL ausführen? Wie lassen sich die Container miteinander kommunizieren? Weitere Informationen finden Sie hier.

## <a name="next-steps"></a>Nächste Schritte

Fahren Sie mit dem Tutorial fort.

> [!div class="nextstepaction"]
> [Apps mit mehreren Containern](multi-container-apps.md)