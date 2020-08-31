---
title: 'Docker-Tutorial-Teil 7: Verwenden von Docker Compose'
description: Hier wird beschrieben, wie Sie docker Compose installieren und verwenden.
ms.date: 08/04/2020
author: nebuk89
ms.author: ghogen
manager: jillfra
ms.technology: vs-azure
ms.topic: conceptual
ms.workload:
- azure
ms.openlocfilehash: 81f70612b05920ea58c752a878831f1d6de34098
ms.sourcegitcommit: c4212f40df1a16baca1247cac2580ae699f97e4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/31/2020
ms.locfileid: "89176693"
---
# <a name="use-docker-compose"></a>Verwenden von Docker Compose

[Docker Compose](https://docs.docker.com/compose/) ist ein Tool, das zum Definieren und Freigeben von Anwendungen mit mehreren Containern entwickelt wurde. Mit Compose können Sie eine YAML-Datei erstellen, um die Dienste zu definieren. mit einem einzigen Befehl können Sie alles nach oben oder unten aufteilen.

Der *große* Vorteil bei der Verwendung von Compose besteht darin, dass Sie Ihren Anwendungs Stapel in einer Datei definieren, ihn im Stammverzeichnis Ihres Projekt-Repository aufbewahren können (es ist nun versionsgesteuert), und eine andere Person auf einfache Weise zum mitwirken Ihres Projekts aktivieren. Jemand muss nur Ihr Repository Klonen und die Compose-app starten. In der Tat werden Ihnen möglicherweise einige Projekte auf GitHub/gitlab angezeigt, die genau das tun.

Wie fangen Sie an?

## <a name="install-docker-compose"></a>Installieren von Docker Compose

Wenn Sie docker Desktop sowohl für Windows als auch für Mac installiert haben, verfügen Sie bereits über docker Compose! Für Play-with-docker-Instanzen ist bereits docker Compose installiert. Wenn Sie sich auf einem Linux-Computer befinden, müssen Sie docker Compose mithilfe [der hier beschriebenen Anweisungen](https://docs.docker.com/compose/install/)installieren.

Nach der Installation sollten Sie Folgendes ausführen und Versionsinformationen anzeigen können.

```bash
docker-compose version
```

## <a name="create-the-compose-file"></a>Erstellen der Compose-Datei

1. Erstellen Sie im Stammverzeichnis des App-Projekts eine Datei mit dem Namen `docker-compose.yml` .

1. In der Compose-Datei beginnen wir mit der Definition der Schema Version. In den meisten Fällen empfiehlt es sich, die neueste unterstützte Version zu verwenden. Informationen zu den aktuellen Schema Versionen und zur Kompatibilitäts Matrix finden Sie in der [Compose-Datei](https://docs.docker.com/compose/compose-file/) .

    ```yaml
    version: "3.7"
    ```

1. Definieren Sie als nächstes die Liste der Dienste (oder Container), die Sie als Teil Ihrer Anwendung ausführen möchten.

    ```yaml hl_lines="3"
    version: "3.7"

    services:
    ```

Und jetzt beginnen Sie, einen Dienst zu einem Zeitpunkt in der Compose-Datei zu migrieren.

## <a name="define-the-app-service"></a>Definieren des App Service

Dies ist der Befehl, den Sie zum Definieren des App-Containers verwendet haben (ersetzen Sie die ` \ ` Zeichen durch `` ` `` in Windows PowerShell).

```bash
docker run -dp 3000:3000 \
  -w /app -v ${PWD}:/app \
  --network todo-app \
  -e MYSQL_HOST=mysql \
  -e MYSQL_USER=root \
  -e MYSQL_PASSWORD=secret \
  -e MYSQL_DB=todos \
  node:12-alpine \
  sh -c "yarn install && yarn run dev"
```

1. Definieren Sie zunächst den Dienst Eintrag und das Image für den Container. Sie können einen beliebigen Namen für den Dienst auswählen. Der Name wird automatisch zu einem Netzwerkalias, der beim Definieren des MySQL-Dienstanbieter nützlich ist.

    ```yaml hl_lines="4 5"
    version: "3.7"

    services:
      app:
        image: node:12-alpine
    ```

1. In der Regel wird der Befehl in der Nähe der `image` Definition angezeigt, obwohl die Reihenfolge nicht angefordert werden muss. Und verschieben Sie die Datei in die Datei.

    ```yaml hl_lines="6"
    version: "3.7"

    services:
      app:
        image: node:12-alpine
        command: sh -c "yarn install && yarn run dev"
    ```

1. Migrieren Sie den `-p 3000:3000` Teil des Befehls, indem Sie den `ports` für den Dienst definieren. Sie verwenden die [kurze Syntax](https://docs.docker.com/compose/compose-file/#short-syntax-1) hier, aber es gibt auch eine ausführlichere [lange Syntax](https://docs.docker.com/compose/compose-file/#long-syntax-1) .

    ```yaml hl_lines="7 8"
    version: "3.7"

    services:
      app:
        image: node:12-alpine
        command: sh -c "yarn install && yarn run dev"
        ports:
          - 3000:3000
    ```

1. Migrieren Sie als nächstes das Arbeitsverzeichnis ( `-w /app` ) und die volumezuordnung ( `-v ${PWD}:/app` ) mithilfe `working_dir` der `volumes` Definitionen und. Volumes verfügen auch über eine [kurze](https://docs.docker.com/compose/compose-file/#short-syntax-3) und [lange](https://docs.docker.com/compose/compose-file/#long-syntax-3) Syntax.

   Ein Vorteil docker Compose Volumedefinitionen ist, dass Sie relative Pfade aus dem aktuellen Verzeichnis verwenden können.

    ```yaml hl_lines="9 10 11"
    version: "3.7"

    services:
      app:
        image: node:12-alpine
        command: sh -c "yarn install && yarn run dev"
        ports:
          - 3000:3000
        working_dir: /app
        volumes:
          - ./:/app
    ```

1. Migrieren Sie schließlich die Umgebungsvariablen Definitionen mithilfe des `environment` Schlüssels.

    ```yaml hl_lines="12 13 14 15 16"
    version: "3.7"

    services:
      app:
        image: node:12-alpine
        command: sh -c "yarn install && yarn run dev"
        ports:
          - 3000:3000
        working_dir: /app
        volumes:
          - ./:/app
        environment:
          MYSQL_HOST: mysql
          MYSQL_USER: root
          MYSQL_PASSWORD: secret
          MYSQL_DB: todos
    ```

### <a name="define-the-mysql-service"></a>Definieren des MySQL-Dienes

Nun ist es an der Zeit, den MySQL-Dienst zu definieren. Der Befehl, den Sie für diesen Container verwendet haben, lautete wie folgt (ersetzen Sie die ` \ ` Zeichen durch `` ` `` in Windows PowerShell):

```bash
docker run -d \
  --network todo-app --network-alias mysql \
  -v todo-mysql-data:/var/lib/mysql \
  -e MYSQL_ROOT_PASSWORD=secret \
  -e MYSQL_DATABASE=todos \
  mysql:5.7
```

1. Definieren Sie zunächst den neuen Dienst, und benennen Sie ihn `mysql` so, dass automatisch der Netzwerkalias abgerufen wird. Geben Sie auch das zu verwendende Bild an.

    ```yaml hl_lines="6 7"
    version: "3.7"

    services:
      app:
        # The app service definition
      mysql:
        image: mysql:5.7
    ```

1. Als nächstes definieren Sie die volumezuordnung. Wenn Sie den Container mit ausgeführt `docker run` haben, wurde das benannte Volume automatisch erstellt. Dies geschieht jedoch nicht, wenn die Ausführung mit Compose erfolgt. Sie müssen das Volume im Abschnitt der obersten Ebene definieren `volumes:` und dann den Bereitstellungspunkt in der Dienst Konfiguration angeben. Wenn Sie einfach nur den Volumenamen bereitstellen, werden die Standardoptionen verwendet. Es stehen jedoch noch [viele weitere Optionen zur Verfügung](https://docs.docker.com/compose/compose-file/#volume-configuration-reference) .

    ```yaml hl_lines="8 9 10 11 12"
    version: "3.7"

    services:
      app:
        # The app service definition
      mysql:
        image: mysql:5.7
        volumes:
          - todo-mysql-data:/var/lib/mysql
    
    volumes:
      todo-mysql-data:
    ```

1. Schließlich müssen Sie nur die Umgebungsvariablen angeben.

    ```yaml hl_lines="10 11 12"
    version: "3.7"

    services:
      app:
        # The app service definition
      mysql:
        image: mysql:5.7
        volumes:
          - todo-mysql-data:/var/lib/mysql
        environment: 
          MYSQL_ROOT_PASSWORD: secret
          MYSQL_DATABASE: todos
    
    volumes:
      todo-mysql-data:
    ```

An diesem Punkt sollte der gesamte Vorgang `docker-compose.yml` wie folgt aussehen:

```yaml
version: "3.7"

services:
  app:
    image: node:12-alpine
    command: sh -c "yarn install && yarn run dev"
    ports:
      - 3000:3000
    working_dir: /app
    volumes:
      - ./:/app
    environment:
      MYSQL_HOST: mysql
      MYSQL_USER: root
      MYSQL_PASSWORD: secret
      MYSQL_DB: todos

  mysql:
    image: mysql:5.7
    volumes:
      - todo-mysql-data:/var/lib/mysql
    environment: 
      MYSQL_ROOT_PASSWORD: secret
      MYSQL_DATABASE: todos

volumes:
  todo-mysql-data:
```

## <a name="run-the-application-stack"></a>Ausführen des Anwendungs Stapels

Nun, da Sie über die `docker-compose.yml` Datei verfügen, können Sie Sie starten.

1. Stellen Sie zunächst sicher, dass keine anderen Kopien der APP und der Datenbank ausgeführt werden ( `docker ps` und `docker rm -f <ids>` ).

1. Starten Sie den Anwendungs Stapel mit dem `docker-compose up` Befehl. Fügen Sie das- `-d` Flag hinzu, um im Hintergrund alles auszuführen. Alternativ dazu können Sie auch mit der rechten Maustaste auf die Compose-Datei klicken und die Option **Compose up** für die vs Code Seitenleiste auswählen. 

    ```bash
    docker-compose up -d
    ```

    Wenn Sie dies ausführen, sollte eine Ausgabe wie die folgende angezeigt werden:

    ```plaintext
    Creating network "app_default" with the default driver
    Creating volume "app_todo-mysql-data" with default driver
    Creating app_app_1   ... done
    Creating app_mysql_1 ... done
    ```

    Sie werden feststellen, dass das Volume und ein Netzwerk erstellt wurden. Standardmäßig erstellt docker Compose automatisch ein Netzwerk speziell für den Anwendungs Stapel (aus diesem Grund haben Sie keinen in der Compose-Datei definiert).

1. Sehen Sie sich die Protokolle mit dem `docker-compose logs -f` Befehl an. Sie sehen, dass sich die Protokolle der einzelnen Dienste in einem einzigen Stream befinden. Dies ist äußerst nützlich, wenn Sie auf zeitbezogene Probleme achten möchten. Das `-f` Flag "folgt" das Protokoll, sodass Sie eine Live Ausgabe erhalten, während Sie generiert wird.

    Wenn Sie dies noch nicht getan haben, wird eine Ausgabe angezeigt, die wie folgt aussieht:

    ```plaintext
    mysql_1  | 2019-10-03T03:07:16.083639Z 0 [Note] mysqld: ready for connections.
    mysql_1  | Version: '5.7.27'  socket: '/var/run/mysqld/mysqld.sock'  port: 3306  MySQL Community Server (GPL)
    app_1    | Connected to mysql db at host mysql
    app_1    | Listening on port 3000
    ```

    Der Dienst Name wird am Anfang der Zeile (häufig farbig) angezeigt, um Meldungen zu unterscheiden. Wenn Sie die Protokolle für einen bestimmten Dienst anzeigen möchten, können Sie den Dienstnamen am Ende des Befehls "Logs" (z `docker-compose logs -f app` . b.) hinzufügen.

    > [!TIP]
    > **Warten auf die Datenbank, bevor die APP gestartet** wird Wenn die APP gestartet wird, wird Sie tatsächlich ausgeführt, und es wird darauf gewartet, dass MySQL bereit ist, bevor versucht wird, eine Verbindung herzustellen, it.DocKer nicht über eine integrierte Unterstützung verfügt, um zu warten, bis ein anderer Container vollständig betriebsbereit ist und bereit ist, bevor ein anderer Container gestartet wird. Bei Knoten basierten Projekten können Sie die [Wait-Port](https://github.com/dwmkerr/wait-port) -Abhängigkeit verwenden. Ähnliche Projekte sind für andere Sprachen/Frameworks vorhanden.

1. An diesem Punkt sollten Sie in der Lage sein, Ihre APP zu öffnen und die Ausführung anzuzeigen. Und Hallo! Sie sind auf einen einzelnen Befehl festgelegt.

## <a name="see-the-app-stack-in-the-docker-extension"></a>Anzeigen des App-Stapels in der Docker-Erweiterung

Wenn Sie die Docker-Erweiterung betrachten, können Sie die Gruppierungs Optionen mithilfe von "Cog" und "Group by" ändern. In diesem Fall möchten Sie Container nach dem Projektnamen "compose" gruppiert sehen:

![VS-Erweiterung mit Compose](media/vs-app-project-collapsed.png)

Wenn Sie das Netzwerk im Netzwerk optimieren, werden die beiden Container angezeigt, die Sie in der Compose-Datei definiert haben.

![VS-Erweiterung mit erweitertem Compose](media/vs-app-project-expanded.png)

## <a name="tear-it-all-down"></a>Alles zerreißen

Wenn Sie bereit sind, Sie vollständig zu beenden, führen Sie einfach aus `docker-compose down` , oder klicken Sie in der Liste Container in der vs Code docker-Erweiterung mit der rechten Maustaste auf die Anwendung, und wählen Sie **Compose Down**aus. Die Container werden angehalten, und das Netzwerk wird entfernt.

> [!WARNING]
> **Entfernen von Volumes** Benannte Volumes in der Compose-Datei werden standardmäßig nicht entfernt, wenn Sie ausgeführt werden `docker-compose down` . Wenn Sie die Volumes entfernen möchten, müssen Sie das-Flag hinzufügen `--volumes` .

Nach dem Herunterfahren können Sie zu einem anderen Projekt wechseln, Ausführen `docker-compose up` und bereit sein, zu diesem Projekt beizutragen! Das ist wirklich nicht viel einfacher als das!

## <a name="recap"></a>Zusammenfassung

In diesem Abschnitt haben Sie erfahren, wie Sie docker Compose und wie Sie die Definition und Freigabe von multidienstanwendungen erheblich vereinfachen. Sie haben eine Compose-Datei erstellt, indem Sie die von Ihnen verwendeten Befehle in das entsprechende Compose-Format übersetzen.

An dieser Stelle beginnen Sie mit der Zusammenfassung des Tutorials. Es gibt jedoch einige bewährte Methoden für die Abbild Bildung, da es ein großes Problem mit der dockerfile-Datei gibt, die Sie bereits verwendet haben. Schauen wir uns das Mal an!

## <a name="next-steps"></a>Nächste Schritte

Fahren Sie mit dem Tutorial fort.

> [!div class="nextstepaction"]
> [Bewährte Methoden für die Image Bildung](image-building-best-practices.md)
