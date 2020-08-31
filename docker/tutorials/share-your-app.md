---
title: 'Docker-Tutorial-Teil 3: Freigeben Ihrer APP'
description: Hier wird beschrieben, wie Sie docker-Images mithilfe der Docker-Hub-Registrierung freigeben.
ms.date: 08/04/2020
author: nebuk89
ms.author: ghogen
manager: jillfra
ms.technology: vs-azure
ms.topic: conceptual
ms.workload:
- azure
ms.openlocfilehash: d5bd7a2d79bf6da710fd0f5803c2415781160143
ms.sourcegitcommit: c4212f40df1a16baca1247cac2580ae699f97e4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/31/2020
ms.locfileid: "89176746"
---
# <a name="share-your-app"></a>Freigeben der APP

Nun, da wir ein Image erstellt haben, können Sie es freigeben. Zum Freigeben von Docker-Images müssen Sie eine docker-Registrierung verwenden. Die Standard Registrierung ist docker Hub und ist der Ort, an dem alle Images, die wir verwendet haben, stammen.

## <a name="create-a-repo"></a>Erstellen eines Repository

Um ein Image per Push zu überführen, müssen Sie zunächst ein Repository auf dem docker-Hub erstellen.

1. Wechseln Sie zu [docker Hub](https://hub.docker.com) , und melden Sie sich bei Bedarf an.

1. Klicken Sie auf die Schaltfläche **Create Repository** .

1. Verwenden Sie für den Namen des Repository `getting-started` . Stellen Sie sicher, dass die Sichtbarkeit ist `Public` .

1. Klicken Sie auf die Schaltfläche **Erstellen** .

Wenn Sie sich auf der rechten Seite der Seite ansehen, wird ein Abschnitt mit dem Namen **docker-Befehle**angezeigt. Dies ist ein Beispiel Befehl, den Sie ausführen müssen, um ein Push in dieses Repository auszuführen.

![Docker-Befehl mit Push-Beispiel](media/push-command.png)

## <a name="push-the-image"></a>Verschieben des Images

1. Führen Sie in der Befehlszeile den Push-Befehl aus, den Sie auf dem docker-Hub sehen. Beachten Sie, dass der Befehl Ihren Namespace verwendet, nicht "docker".

    ```plaintext
    $ docker push docker/getting-started
    The push refers to repository [docker.io/docker/getting-started]
    An image does not exist locally with the tag: docker/getting-started
    ```

    Warum tritt ein Fehler auf? Der Push-Befehl suchte nach einem Image mit dem Namen "docker/Getting-Started", aber es wurde nicht gefunden. Wenn Sie Ausführen `docker image ls` , wird keine der beiden angezeigt.

    Um dieses Problem zu beheben, müssen Sie Ihr vorhandenes Image, das wir erstellt haben, "markieren", um einen anderen Namen zu erhalten.

1. Melden Sie sich mit dem Befehl beim docker-Hub an `docker login -u <username>` .

1. Verwenden `docker tag` Sie den Befehl, um dem `getting-started` Image einen neuen Namen zuzuweisen. Stellen Sie sicher, dass Sie sich `<username>` mit ihrer docker-ID austauschen.

    ```bash
    docker tag getting-started <username>/getting-started
    ```

1. Versuchen Sie nun erneut, den Push-Befehl auszuführen. Wenn Sie den Wert aus dem docker-Hub kopieren, können Sie den `tagname` Teil löschen, da Sie dem Bildnamen kein Tag hinzugefügt haben. Wenn Sie kein Tag angeben, wird von Docker ein Tag mit dem Namen verwendet `latest` .

    ```bash
    docker push <username>/getting-started
    ```

## <a name="run-the-image-on-a-new-instance"></a>Ausführen des Abbilds auf einer neuen Instanz

Nachdem Ihr Image erstellt und in eine Registrierung gepusht wurde, führen Sie die APP auf einer neuen Instanz aus, die dieses Container Image noch nicht gesehen hat! Zu diesem Zweck verwenden Sie Play mit Docker.

1. Öffnen Sie Ihren Browser, um [Docker zu spielen](http://play-with-docker.com).

1. Melden Sie sich mit Ihrem docker Hub-Konto an.

1. Wenn Sie angemeldet sind, klicken Sie auf den Link "+ neue Instanz hinzufügen" auf der linken Seite. (Wenn Sie es nicht sehen, machen Sie Ihren Browser etwas breiter.) Nach wenigen Sekunden wird in Ihrem Browser ein Terminalfenster geöffnet.

    ![Mit docker neue Instanz hinzufügen](media/pwd-add-new-instance.png)

1. Starten Sie im Terminal ihre neu übersetzte app.

    ```bash
    docker run -dp 3000:3000 <username>/getting-started
    ```

    Es sollte angezeigt werden, dass das Bild heruntergezogen und schließlich gestartet wird.

1. Klicken Sie auf das 3000-Badge, wenn es angezeigt wird, und Sie sollten die APP mit Ihren Änderungen anzeigen. Hurra! Wenn das 3000-Badge nicht angezeigt wird, können Sie auf die Schaltfläche **Port öffnen** klicken und 3000 eingeben.

## <a name="recap"></a>Zusammenfassung

In diesem Abschnitt haben Sie erfahren, wie Sie Images freigeben können, indem Sie Sie per Push in eine Registrierung übertragen. Dann haben Sie zu einer neuen Instanz gewechselt und konnten das frisch übersetzte Abbild ausführen. Dies wird in CI-Pipelines häufig vorkommen, bei denen die Pipeline das Image erstellt und per Push in eine Registrierung überträgt. Anschließend kann die Produktionsumgebung die neueste Version des Abbilds verwenden.

Nun, da Sie dies herausgefunden haben, erinnern Sie sich, dass Sie am Ende des letzten Abschnitts, als Sie die APP neu gestartet haben, alle Ihre TODO-Listenelemente verloren haben. Das ist natürlich keine gute Benutzerfunktion, daher erfahren Sie im nächsten Schritt, wie Sie die Daten bei Neustarts dauerhaft speichern können.

## <a name="next-steps"></a>Nächste Schritte

Fahren Sie mit dem Tutorial fort.

> [!div class="nextstepaction"]
> [Beibehalten der Datenbank](persist-your-data.md)