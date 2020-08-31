---
title: 'Docker-Tutorial-Teil 2: Aktualisieren Ihrer APP'
description: Hier wird beschrieben, wie Sie eine docker-APP aktualisieren.
ms.date: 08/04/2020
author: nebuk89
ms.author: ghogen
manager: jillfra
ms.technology: vs-azure
ms.topic: conceptual
ms.workload:
- azure
ms.openlocfilehash: 4a1cba71481608803522336ad5c0f6b6354bca32
ms.sourcegitcommit: c4212f40df1a16baca1247cac2580ae699f97e4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/31/2020
ms.locfileid: "89176750"
---
# <a name="update-the-app"></a>Aktualisieren der App

Als kleine Funktions Anforderung haben Sie vom Produktteam aufgefordert, den "leeren Text" zu ändern, wenn keine TODO-Listenelemente vorhanden sind. Sie möchten Sie in Folgendes übertragen:

> Sie haben noch keine TODO-Elemente. Fügen Sie oben ein hinzu.

Ganz einfach, richtig? Nehmen wir die Änderung vor.

## <a name="update-the-source-code"></a>Aktualisieren des Quellcodes

1. `src/static/js/app.js`Aktualisieren Sie in der Datei Zeile 56, um den neuen leeren Text zu verwenden.

    ```diff
    -                <p className="text-center">No items yet! Add one above!</p>
    +                <p className="text-center">You have no todo items yet! Add one above!</p>
    ```

1. Erstellen Sie die aktualisierte Version des Images mit dem gleichen Befehl, den Sie zuvor verwendet haben.

    ```bash
    docker build -t getting-started .
    ```

1. Starten Sie einen neuen Container mit dem aktualisierten Code.

    ```bash
    docker run -dp 3000:3000 getting-started
    ```

**Seltsam.** Wahrscheinlich haben Sie einen Fehler wie diesen angezeigt (die IDs unterscheiden sich):

```bash
docker: Error response from daemon: driver failed programming external connectivity on endpoint laughing_burnell 
(bb242b2ca4d67eba76e79474fb36bb5125708ebdabd7f45c8eaf16caaabde9dd): Bind for 0.0.0.0:3000 failed: port is already allocated.
```

Was ist passiert? Der neue Container konnte nicht gestartet werden, da der alte Container noch ausgeführt wird. Der Grund hierfür ist ein Problem, weil dieser Container den Host Port 3000 verwendet und nur ein Prozess auf dem Computer (enthaltene Container) an einem bestimmten Port lauschen kann. Um dieses Problem zu beheben, entfernen Sie den alten Container.

## <a name="replace-the-old-container"></a>Ersetzen des alten Containers

Um einen Container zu entfernen, muss er zuerst beendet werden. Nachdem der Vorgang beendet wurde, kann er entfernt werden. Sie haben zwei Möglichkeiten, den alten Container zu entfernen. Sie können den Pfad auswählen, mit dem Sie am meisten vertraut sind.

### <a name="remove-a-container-using-the-cli"></a>Entfernen eines Containers mithilfe der CLI

1. Verwenden Sie den Befehl, um die ID des Containers zu erhalten `docker ps` .

    ```bash
    docker ps
    ```

1. Verwenden `docker stop` Sie den Befehl, um den Container zu unterbinden.

    ```bash
    # Swap out <the-container-id> with the ID from docker ps
    docker stop <the-container-id>
    ```

1. Nachdem der Container beendet wurde, können Sie ihn mithilfe des- `docker rm` Befehls entfernen.

    ```bash
    docker rm <the-container-id>
    ```

> [!TIP]
> Sie können einen Container in einem einzelnen Befehl durch Hinzufügen des Flag "Force" zum Befehl entfernen und entfernen `docker rm` . Beispiel: `docker rm -f <the-container-id>`

### <a name="remove-a-container-using-the-docker-dashboard"></a>Entfernen eines Containers mithilfe des docker-Dashboards

Wenn Sie die vs Code Erweiterung öffnen, können Sie einen Container mit zwei Klicks entfernen. Es ist sicherlich viel einfacher, als Container-ID zu suchen und zu entfernen.

1. Navigieren Sie mit der geöffneten Erweiterung zum Container, und klicken Sie mit der rechten Maustaste.

1. Klicken Sie auf die Option **Entfernen** .

1. Bestätigen Sie das Entfernen, und Sie sind fertig!

![Docker-Dashboard-Entfernen eines Containers](media/vs-removing-container.png)

### <a name="start-the-updated-app-container"></a>Starten Sie den aktualisierten App-Container.

1. Starten Sie jetzt Ihre aktualisierte APP.

    ```bash
    docker run -dp 3000:3000 getting-started
    ```

1. Aktualisieren Sie Ihren Browser auf, [http://localhost:3000](http://localhost:3000) und Sie sollten den aktualisierten Hilfe Text anzeigen.

![Aktualisierte Anwendung mit aktualisiertem leeren Text](media/todo-list-updated-empty-text.png)

## <a name="recap"></a>Zusammenfassung

Obwohl Sie ein Update erstellen konnten, haben Sie möglicherweise zwei Dinge bemerkt:

- Alle vorhandenen Elemente in der TODO-Liste sind nicht mehr vorhanden! Das ist keine sehr gute APP! Dies wird in Kürze erläutert.
- Für eine solche kleine Änderung wurden *viele* Schritte ausgeführt. In einem kommenden Abschnitt erfahren Sie, wie Sie Code Aktualisierungen anzeigen, ohne jedes Mal, wenn Sie eine Änderung vornehmen, einen neuen Container neu erstellen und neu starten zu müssen.

Bevor Sie sich mit der Persistenz vertraut machen, werden Sie schnell feststellen, wie Sie diese Images für andere freigeben.

## <a name="next-steps"></a>Nächste Schritte

Fahren Sie mit dem Tutorial fort.

> [!div class="nextstepaction"]
> [Freigeben der App](share-your-app.md)
