---
title: 'Docker-Tutorial-Teil 6: apps mit mehreren Containern'
description: Erfahren Sie, wie Sie Netzwerkverbindungen zwischen Containern einrichten und einen Container für eine MySQL-Datenbank hinzufügen.
ms.date: 08/04/2020
author: nebuk89
ms.author: ghogen
manager: jillfra
ms.technology: vs-azure
ms.topic: conceptual
ms.workload:
- azure
ms.openlocfilehash: 9513a3414a38aa02f6a4607a8c95bbf02c0e1cf6
ms.sourcegitcommit: c4212f40df1a16baca1247cac2580ae699f97e4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/31/2020
ms.locfileid: "89176695"
---
# <a name="multi-container-apps"></a>Apps mit mehreren Containern

Bis zu diesem Zeitpunkt haben Sie mit einzelcontaineranwendungen gearbeitet. Nun fügen Sie MySQL dem Anwendungs Stapel hinzu. Die folgende Frage kommt häufig vor: "wo wird MySQL ausgeführt? Installieren Sie Sie im gleichen Container, oder führen Sie Sie separat aus? " Im allgemeinen **sollte jeder Container eine Aktion durchführen und dies gut tun.** Einige Gründe:

- Es gibt eine gute Chance, APIs und Front-Ends anders als Datenbanken zu skalieren.
- Getrennte Container ermöglichen Ihnen die Isolation von Versions-und Update Versionen.
- Obwohl Sie einen Container für die-Datenbank lokal verwenden können, empfiehlt es sich, in der Produktion einen verwalteten Dienst für die Datenbank zu verwenden. Sie möchten die Datenbank-Engine dann nicht mit Ihrer APP versenden.
- Das Ausführen mehrerer Prozesse erfordert einen Prozess-Manager (der Container startet nur einen Prozess), wodurch die Komplexität beim Starten/Herunterfahren des Containers erhöht wird.

Und es gibt weitere Gründe. Daher aktualisieren Sie die Anwendung so, dass Sie wie folgt funktioniert:

![Mit MySQL-Container verbundene ToDo-APP](media/multi-app-architecture.png)

## <a name="container-networking"></a>Containernetzwerke

Beachten Sie, dass Container standardmäßig isoliert ausgeführt werden und nichts über andere Prozesse oder Container auf dem gleichen Computer weiß. Wie können Sie also einen Container mit einem anderen kommunizieren? Die Antwort ist " **Networking**". Nun müssen Sie kein Netzwerktechniker ("huoray!") sein. Merken Sie sich diese Regel...

> [!NOTE]
> Wenn sich zwei Container im gleichen Netzwerk befinden, können Sie miteinander kommunizieren. Wenn dies nicht der Fall ist, ist dies nicht möglich.

## <a name="start-mysql"></a>Starten Sie MySQL.

Es gibt zwei Möglichkeiten, einen Container in einem Netzwerk zu platzieren: weisen Sie ihn beim Starten oder Verbinden eines vorhandenen Containers zu. Zum jetzigen Zeitpunkt erstellen Sie zuerst das Netzwerk und fügen den MySQL-Container beim Start an.

1. Erstellen Sie das Netzwerk.

    ```bash
    docker network create todo-app
    ```

1. Starten Sie einen MySQL-Container, und fügen Sie ihn dem Netzwerk an. Wir definieren außerdem einige Umgebungsvariablen, die von der Datenbank zum Initialisieren der Datenbank verwendet werden (Weitere Informationen finden Sie im Abschnitt "Umgebungsvariablen" in der [MySQL docker Hub-Auflistung](https://hub.docker.com/_/mysql/)) (ersetzen Sie die ` \ ` Zeichen durch `` ` `` in Windows PowerShell).

    ```bash
    docker run -d \
        --network todo-app --network-alias mysql \
        -v todo-mysql-data:/var/lib/mysql \
        -e MYSQL_ROOT_PASSWORD=secret \
        -e MYSQL_DATABASE=todos \
        mysql:5.7
    ```

    Sie sehen auch, dass Sie das-Flag angegeben haben `--network-alias` . Wir kommen dann in Kürze darauf zurück.

    > [!TIP]
    > Sie werden feststellen, dass Sie hier einen `todo-mysql-data` Volumenamen verwenden und ihn an der Stelle bereitstellen `/var/lib/mysql` , an der MySQL seine Daten speichert. Sie haben jedoch nie einen `docker volume create` Befehl ausgeführt. Docker erkennt, dass Sie ein benanntes Volume verwenden möchten, und erstellt eine automatische Erstellung für Sie.

1. Stellen Sie eine Verbindung mit der Datenbank her, und überprüfen Sie, ob die Datenbank eine Verbindung herstellt, um zu bestätigen, dass Sie

    ```bash
    docker exec -it <mysql-container-id> mysql -p
    ```

    Wenn die Kenn Wort Eingabeaufforderung angezeigt wird, geben Sie **geheimer**Schlüssel ein. In der MySQL-Shell können Sie die Datenbanken auflisten und überprüfen, ob die Datenbank angezeigt wird `todos` .

    ```cli
    mysql> SHOW DATABASES;
    ```

    Eine ähnliche Ausgabe wie die folgende sollte angezeigt werden:

    ```plaintext
    +--------------------+
    | Database           |
    +--------------------+
    | information_schema |
    | mysql              |
    | performance_schema |
    | sys                |
    | todos              |
    +--------------------+
    5 rows in set (0.00 sec)
    ```

    Hurra! Ihre `todos` Datenbank ist einsatzbereit.

## <a name="connect-to-mysql"></a>Herstellen einer Verbindung mit MySQL

Nun, da Sie wissen, dass MySQL in Betrieb ist und ausgeführt wird, können Sie es verwenden. Die Frage ist jedoch... dass? Wenn Sie einen anderen Container im selben Netzwerk ausführen, wie finden Sie den Container (denken Sie daran, dass jeder Container über eine eigene IP-Adresse verfügt)?

Um dies herauszufinden, verwenden Sie den [nicolaka/Netshoot-](https://github.com/nicolaka/netshoot) Container, der mit *vielen* Tools ausgeliefert wird, die für die Problembehandlung oder das Debuggen von Netzwerkproblemen nützlich sind.

1. Starten Sie einen neuen Container mithilfe des `nicolaka/netshoot` Bilds. Stellen Sie sicher, dass Sie mit demselben Netzwerk verbunden sind.

    ```bash
    docker run -it --network todo-app nicolaka/netshoot
    ```

1. Verwenden Sie innerhalb des Containers den `dig` Befehl, bei dem es sich um ein nützliches DNS-Tool handelt. Suchen Sie nach der IP-Adresse für den Hostnamen `mysql` .

    ```bash
    dig mysql
    ```

    Und Sie erhalten eine Ausgabe wie diese...

    ```text
    ; <<>> DiG 9.14.1 <<>> mysql
    ;; global options: +cmd
    ;; Got answer:
    ;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 32162
    ;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 0

    ;; QUESTION SECTION:
    ;mysql.             IN  A

    ;; ANSWER SECTION:
    mysql.          600 IN  A   172.23.0.2

    ;; Query time: 0 msec
    ;; SERVER: 127.0.0.11#53(127.0.0.11)
    ;; WHEN: Tue Oct 01 23:47:24 UTC 2019
    ;; MSG SIZE  rcvd: 44
    ```

    Im Abschnitt "Antwort" wird ein Datensatz angezeigt, der `A` `mysql` zu aufgelöst wird `172.23.0.2` (Ihre IP-Adresse hat wahrscheinlich einen anderen Wert). Obwohl `mysql` normalerweise kein gültiger Hostname ist, konnte docker ihn in die IP-Adresse des Containers auflösen, der diesen Netzwerkalias besaß (merken Sie sich das Flag, das `--network-alias` Sie zuvor verwendet haben?).

    Dies bedeutet, dass... Ihre APP muss lediglich eine Verbindung mit einem Host namens herstellen, `mysql` der mit der Datenbank kommuniziert. Das ist nicht viel einfacher als das!

## <a name="run-your-app-with-mysql"></a>Ausführen der APP mit MySQL

Die ToDo-APP unterstützt das Festlegen einiger Umgebungsvariablen zum Angeben von MySQL-Verbindungseinstellungen. Sie lauten wie folgt:

- `MYSQL_HOST` : der Hostname für den laufenden MySQL-Server
- `MYSQL_USER` -der für die Verbindung zu verwendende Benutzername
- `MYSQL_PASSWORD` : das für die Verbindung zu verwendende Kennwort
- `MYSQL_DB` -die Datenbank, die nach der Verbindung verwendet werden soll

> [!WARNING]
> **Festlegen der Verbindungseinstellungen über Umgebungsvariablen** Die Verwendung von Umgebungsvariablen zum Festlegen der Verbindungseinstellungen ist im Allgemeinen für die Entwicklung geeignet Informationen zu den Grundlagen finden [Sie Untergründe für die Verwendung von Umgebungsvariablen für geheime Daten](https://diogomonica.com/2017/03/27/why-you-shouldnt-use-env-variables-for-secret-data/).
> Ein sichereren Mechanismus ist die Verwendung der von Ihrem containerorchestrierungs-Framework bereitgestellten Geheimnis Unterstützung. In den meisten Fällen werden diese geheimen Schlüssel als Dateien im laufenden Container bereitgestellt. Sie sehen, dass viele apps (einschließlich MySQL-Image und ToDo-APP) auch env-VARs mit einem Suffix unterstützen `_FILE` , um auf eine Datei zu verweisen, die die Datei enthält.
> Beispielsweise bewirkt das Festlegen der `MYSQL_PASSWORD_FILE` var, dass die APP den Inhalt der Datei, auf die verwiesen wird, als Verbindungs Kennwort verwendet. Docker unterstützt keine Informationen zur Unterstützung dieser erfv-vars. Ihre APP muss wissen, um nach der Variablen zu suchen und den Dateiinhalt zu erhalten.

Wenn Sie all dies erläutert haben, starten Sie Ihren Entwicklungs bereiten Container!

1. Geben Sie die oben aufgeführten Umgebungsvariablen an, und verbinden Sie den Container mit Ihrem App-Netzwerk (ersetzen Sie die ` \ ` Zeichen durch `` ` `` in Windows PowerShell).

    ```bash hl_lines="3 4 5 6 7"
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

1. Wenn Sie sich die Protokolle für den Container ( `docker logs <container-id>` ) ansehen, sollte eine Meldung angezeigt werden, die angibt, dass die MySQL-Datenbank verwendet wird.

    ```plaintext hl_lines="7"
    # Previous log messages omitted
    $ nodemon src/index.js
    [nodemon] 1.19.2
    [nodemon] to restart at any time, enter `rs`
    [nodemon] watching dir(s): *.*
    [nodemon] starting `node src/index.js`
    Connected to mysql db at host mysql
    Listening on port 3000
    ```

1. Öffnen Sie die app in Ihrem Browser, und fügen Sie Ihrer TODO-Liste einige Elemente hinzu.

1. Stellen Sie eine Verbindung mit der MySQL-Datenbank her, und prüfen Sie, ob die Elemente in die Datenbank geschrieben werden. Beachten Sie, dass das Kennwort **geheim**ist.

    ```bash
    docker exec -ti <mysql-container-id> mysql -p todos
    ```

    Führen Sie in der MySQL-Shell folgendes aus:

    ```plaintext
    mysql> select * from todo_items;
    +--------------------------------------+--------------------+-----------+
    | id                                   | name               | completed |
    +--------------------------------------+--------------------+-----------+
    | c906ff08-60e6-44e6-8f49-ed56a0853e85 | Do amazing things! |         0 |
    | 2912a79e-8486-4bc3-a4c5-460793a575ab | Be awesome!        |         0 |
    +--------------------------------------+--------------------+-----------+
    ```

    Natürlich sieht die Tabelle anders aus, da Sie Ihre Elemente enthält. Sie sollten dort jedoch angezeigt werden.

Wenn Sie sich die Docker-Erweiterung kurz ansehen, werden Sie feststellen, dass zwei App-Container ausgeführt werden. Aber es gibt keinen wirklichen Hinweis darauf, dass Sie in einer einzelnen App zusammengefasst werden. Sie werden erfahren, wie Sie das in Kürze verbessern können.

![Docker-Erweiterung, die zwei nicht gruppierte App-Container anzeigt](media/vs-multi-container-app.png)

## <a name="recap"></a>Zusammenfassung

An diesem Punkt verfügen Sie über eine Anwendung, die Ihre Daten nun in einer externen Datenbank speichert, die in einem separaten Container ausgeführt wird. Sie haben etwas über Container Netzwerke gelernt und gesehen, wie die Dienst Ermittlung mithilfe von DNS ausgeführt werden kann.

Es ist jedoch eine gute Chance, dass Sie sich mit allen Aufgaben vertraut machen, die Sie zum Starten dieser Anwendung benötigen. Sie müssen ein Netzwerk erstellen, Container starten, alle Umgebungsvariablen angeben, Ports verfügbar machen und vieles mehr! Das ist viel zu merken, und es macht es sicher, dass Dinge an andere Personen weitergereicht werden.

Im nächsten Abschnitt wird docker Compose erläutert. Mit docker Compose können Sie Ihre Anwendungs Stapel auf viel einfachere Weise freigeben und mit einem einzelnen Befehl (und einem einfachen Befehl) beginnen.

## <a name="next-steps"></a>Nächste Schritte

Fahren Sie mit dem Tutorial fort.

> [!div class="nextstepaction"]
> [Verwenden von Docker Compose](use-docker-compose.md)
