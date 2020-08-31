---
title: 'Docker-Tutorial-Teil 4: Persistenz Ihrer Daten'
description: Erfahren Sie, wie Sie Daten in einer Datenbank beibehalten und Verzeichnisse in einem Container freigeben, indem Sie ein Volume bereitstellen.
ms.date: 08/04/2020
author: nebuk89
ms.author: ghogen
manager: jillfra
ms.technology: vs-azure
ms.topic: conceptual
ms.workload:
- azure
ms.openlocfilehash: 34b3cb9465c1efb946260917d755729e25c4e259
ms.sourcegitcommit: c4212f40df1a16baca1247cac2580ae699f97e4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/31/2020
ms.locfileid: "89176692"
---
# <a name="persist-your-data"></a> Beibehalten von Daten

Falls Sie nicht bemerkt haben, wird die TODO-Liste jedes Mal bereinigt, wenn Sie den Container starten. Warum? Sehen wir uns nun an, wie der Container funktioniert.

## <a name="the-containers-filesystem"></a>Das Dateisystem des Containers

Wenn ein Container ausgeführt wird, werden die verschiedenen Ebenen von einem Bild für das zugehörige Dateisystem verwendet. Jeder Container erhält auch seinen eigenen "temporären Speicherplatz", um Dateien zu erstellen, zu aktualisieren oder zu entfernen. Änderungen werden in keinem anderen Container angezeigt, *auch wenn* Sie das gleiche Image verwenden.

### <a name="see-this-in-practice"></a>Siehe dies in der Praxis.

Um dies in Aktion zu sehen, starten Sie zwei Container und erstellen jeweils eine Datei. Sie werden sehen, dass die in einem Container erstellten Dateien nicht in einem anderen Container verfügbar sind.

1. Starten Sie einen `ubuntu` Container, mit dem eine Datei `/data.txt` mit dem Namen und einer Zufallszahl zwischen 1 und 10000 erstellt wird.

    ```bash
    docker run -d ubuntu bash -c "shuf -i 1-10000 -n 1 -o /data.txt && tail -f /dev/null"
    ```

    Wenn Sie sich an den Befehl interessiert sind, starten Sie eine bash-Shell und rufen zwei Befehle auf (warum dies der Fall ist `&&` ). Der erste Teil wählt eine einzelne Zufallszahl aus und schreibt Sie in `/data.txt` . Der zweite Befehl dient zum Überwachen einer Datei, um die Ausführung des Containers beizubehalten.

1. Überprüfen Sie die Ausgabe, indem Sie verwenden `exec` , um in den Container zu gelangen. Öffnen Sie hierzu die vs Code-Erweiterung, und klicken Sie auf die Option " **Shell anfügen** ". Dadurch wird `exec` eine Shell im Container innerhalb des vs Code Terminal geöffnet.

    ![Öffnen der CLI in Ubuntu-Container vs Code](media/attach_shell.png)

    Sie sehen ein Terminal, das eine Shell im Ubuntu-Container ausgeführt wird. Führen Sie den folgenden Befehl aus, um den Inhalt der `/data.txt` Datei anzuzeigen. Schließen Sie dieses Terminal anschließend erneut.

    ```bash
    cat /data.txt
    ```

    Wenn Sie die Befehlszeile bevorzugen, können Sie den Befehl verwenden, `docker exec` um das gleiche zu tun. Sie müssen die Container-ID (verwenden Sie `docker ps` , um Sie zu erhalten) und den Inhalt mit dem folgenden Befehl erhalten.

    ```bash
    docker exec <container-id> cat /data.txt
    ```

    Eine Zufallszahl sollte angezeigt werden.

1. Starten Sie nun einen anderen `ubuntu` Container (das gleiche Image), und Sie sehen, dass Sie nicht über die gleiche Datei verfügen.

    ```bash
    docker run -it ubuntu ls /
    ```

    Und sehen Sie! Es ist keine `data.txt` Datei vorhanden. Das liegt daran, dass es nur für den ersten Container in den temporären Bereich geschrieben wurde.

1. Entfernen Sie den ersten Container mithilfe des `docker rm -f` Befehls.

## <a name="container-volumes"></a>Containervolumes

Beim vorherigen Experiment haben Sie gesehen, dass jeder Container bei jedem Start von der Image Definition ausgeht. Während Container Dateien erstellen, aktualisieren und löschen können, gehen diese Änderungen verloren, wenn der Container entfernt wird und alle Änderungen in diesem Container isoliert sind. Mit Volumes können Sie all dies ändern.

[Volumes](https://docs.docker.com/storage/volumes/) bieten die Möglichkeit, bestimmte Dateisystem Pfade des Containers wieder mit dem Host Computer zu verbinden. Wenn ein Verzeichnis im Container bereitgestellt wird, werden Änderungen in diesem Verzeichnis auch auf dem Host Computer angezeigt. Wenn Sie dasselbe Verzeichnis über Container Neustarts einbinden, werden Ihnen dieselben Dateien angezeigt.

Es gibt zwei Haupttypen von Volumes. Sie werden letztendlich beide verwenden, aber Sie beginnen mit **benannten Volumes**.

## <a name="persist-your-todo-data"></a>Beibehalten von TODO-Daten

Standardmäßig speichert die ToDo-APP die Daten in einer [SQLite-Datenbank](https://www.sqlite.org/index.html) unter `/etc/todos/todo.db` . Wenn Sie nicht mit SQLite vertraut sind, machen Sie sich keine Sorgen! Es handelt sich einfach um eine relationale Datenbank, in der alle Daten in einer einzigen Datei gespeichert werden. Dies ist zwar nicht das beste für umfangreiche Anwendungen, aber es funktioniert bei kleinen Demos. Wir werden später über das Wechseln zu einer tatsächlichen Datenbank-Engine sprechen.

Wenn die Datenbank eine einzelne Datei ist und Sie diese Datei auf dem Host beibehalten und für den nächsten Container verfügbar machen können, sollte Sie in der Lage sein, den Speicherort des letzten Containers aufzunehmen. Durch Erstellen eines Volumes und Anfügen (häufig als "einbinden" bezeichnet) an das Verzeichnis, in dem die Daten gespeichert werden, können Sie die Daten persistent speichern. Wenn der Container in die `todo.db` Datei schreibt, wird er auf dem Host auf dem Volume persistent gespeichert.

Wie bereits erwähnt, verwenden Sie ein **benanntes Volume**. Stellen Sie sich ein benanntes Volume einfach als einen Bucket von Daten vor. Docker verwaltet den physischen Speicherort auf dem Datenträger, und Sie müssen sich nur den Namen des Volumes merken. Jedes Mal, wenn Sie das Volume verwenden, stellt docker sicher, dass die richtigen Daten bereitgestellt werden.

1. Erstellen Sie mit dem Befehl ein Volume `docker volume create` .

    ```bash
    docker volume create todo-db
    ```

1. Beendet den ToDo-APP-Container erneut im Dashboard (oder mit `docker rm -f <id>` ), da er noch ausgeführt wird, ohne das persistente Volume zu verwenden.

1. Starten Sie den ToDo-APP-Container, und fügen Sie das-Flag hinzu, `-v` um eine Volumegruppe anzugeben Sie verwenden das benannte Volume, das Sie in einbinden `/etc/todos` , sodass alle im Pfad erstellten Dateien erfasst werden.

    ```bash
    docker run -dp 3000:3000 -v todo-db:/etc/todos getting-started
    ```

1. Nachdem der Container gestartet wurde, öffnen Sie die APP, und fügen Sie Ihrer TODO-Liste einige Elemente hinzu.

    ![Der TODO-Liste hinzugefügte Elemente](media/items-added.png)

1. Entfernen Sie den Container für die ToDo-APP. Verwenden Sie das Dashboard oder `docker ps` , um die ID zu erhalten und dann `docker rm -f <id>` zu entfernen.

1. Starten Sie einen neuen Container, indem Sie den oben aufgeführten Befehl verwenden.

1. Öffnen Sie die app. Ihre Elemente sollten noch in der Liste angezeigt werden.

1. Entfernen Sie den Container, wenn Sie das Auschecken Ihrer Liste abgeschlossen haben.

Hurra! Sie haben nun erfahren, wie Daten persistent gespeichert werden.

> [!TIP]
> Obwohl benannte Volumes und Bindungs Zustellungen (die wir in einer Minute sprechen werden) die beiden Haupttypen von Volumes sind, die von einer Standardinstallation der Docker-Engine unterstützt werden, stehen viele Volumetreiber-Plug-Ins zur Unterstützung von NFS, SFTP, nettapp und mehr zur Verfügung. Dies ist besonders wichtig, wenn Sie Container auf mehreren Hosts in einer Cluster Umgebung mit Swarm, Kubernetes usw. ausführen.

## <a name="dive-into-your-volume"></a>Einblicke in Ihr Volume

Viele Leute fragen sich häufig, "wo ist docker meine Daten *tatsächlich* speichert, wenn ich ein benanntes Volume verwende?" Wenn Sie wissen möchten, können Sie den Befehl verwenden `docker volume inspect` .

```bash
docker volume inspect todo-db
[
    {
        "CreatedAt": "2019-09-26T02:18:36Z",
        "Driver": "local",
        "Labels": {},
        "Mountpoint": "/var/lib/docker/volumes/todo-db/_data",
        "Name": "todo-db",
        "Options": {},
        "Scope": "local"
    }
]
```

`Mountpoint`Ist der tatsächliche Speicherort auf dem Datenträger, auf dem die Daten gespeichert sind. Beachten Sie, dass Sie auf den meisten Computern über root-Zugriff verfügen müssen, um vom Host aus auf dieses Verzeichnis zuzugreifen. Aber an dieser Stelle ist es!

> [!NOTE]
> Direktes **zugreifen auf Volumedaten auf dem docker-Desktop** Während der Ausführung in docker Desktop werden die Docker-Befehle tatsächlich auf einer kleinen VM auf Ihrem Computer ausgeführt. Wenn Sie sich den eigentlichen Inhalt des Verzeichnisses " *Mountpoint* " ansehen möchten, müssen Sie sich zunächst in der VM befinden. In WSL 2 befindet sich dies innerhalb einer WSL 2-Distribution, auf die über den Datei-Explorer zugegriffen werden kann.

## <a name="recap"></a>Zusammenfassung

An diesem Punkt verfügen Sie über eine funktionierende Anwendung, die neu gestartet werden kann! Sie können Sie für ihre Investoren anzeigen und hoffen, dass Sie Ihre Vision abfangen können!

Sie haben jedoch bereits gesehen, dass das Neuerstellen von Images für jede Änderung etwas Zeit in sich bringt. Es gibt eine bessere Möglichkeit, Änderungen vorzunehmen, richtig? Mit BIND-bereit Stellungen (was wir vorhin angedeutet haben) gibt es eine bessere Möglichkeit! Sehen wir uns das jetzt an!

## <a name="next-steps"></a>Nächste Schritte

Fahren Sie mit dem Tutorial fort.

> [!div class="nextstepaction"]
> [Verwenden von Bindungs Zustellungen](use-bind-mounts.md)
