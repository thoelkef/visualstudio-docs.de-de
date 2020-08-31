---
title: 'Docker-Tutorial-Teil 8: Bild Schicht'
description: Überprüfen und Verwalten von Bildebenen in docker-Images.
ms.date: 08/04/2020
author: nebuk89
ms.author: ghogen
manager: jillfra
ms.technology: vs-azure
ms.topic: conceptual
ms.workload:
- azure
ms.openlocfilehash: eae21a729f30a0c77fa52e5774a2f5157286dab1
ms.sourcegitcommit: c4212f40df1a16baca1247cac2580ae699f97e4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/31/2020
ms.locfileid: "89176701"
---
# <a name="image-layering"></a>Bild Schicht

Wussten Sie, dass Sie sehen können, was ein Bild ausmacht? Mit dem `docker image history` Befehl können Sie den Befehl sehen, der zum Erstellen der einzelnen Ebenen innerhalb eines Bilds verwendet wurde.

1. Verwenden Sie den- `docker image history` Befehl, um die Ebenen in dem Bild anzuzeigen, das `getting-started` Sie zuvor in diesem Tutorial erstellt haben.

    ```bash
    docker image history getting-started
    ```

    Sie sollten eine Ausgabe erhalten, die in etwa wie folgt aussieht (Datumsangaben/IDs können unterschiedlich sein).

    ```plaintext
    IMAGE               CREATED             CREATED BY                                      SIZE                COMMENT
    a78a40cbf866        18 seconds ago      /bin/sh -c #(nop)  CMD ["node" "/app/src/ind…   0B                  
    f1d1808565d6        19 seconds ago      /bin/sh -c yarn install --production            85.4MB              
    a2c054d14948        36 seconds ago      /bin/sh -c #(nop) COPY dir:5dc710ad87c789593…   198kB               
    9577ae713121        37 seconds ago      /bin/sh -c #(nop) WORKDIR /app                  0B                  
    b95baba1cfdb        13 days ago         /bin/sh -c #(nop)  CMD ["node"]                 0B                  
    <missing>           13 days ago         /bin/sh -c #(nop)  ENTRYPOINT ["docker-entry…   0B                  
    <missing>           13 days ago         /bin/sh -c #(nop) COPY file:238737301d473041…   116B                
    <missing>           13 days ago         /bin/sh -c apk add --no-cache --virtual .bui…   5.35MB              
    <missing>           13 days ago         /bin/sh -c #(nop)  ENV YARN_VERSION=1.21.1      0B                  
    <missing>           13 days ago         /bin/sh -c addgroup -g 1000 node     && addu…   74.3MB              
    <missing>           13 days ago         /bin/sh -c #(nop)  ENV NODE_VERSION=12.14.1     0B                  
    <missing>           13 days ago         /bin/sh -c #(nop)  CMD ["/bin/sh"]              0B                  
    <missing>           13 days ago         /bin/sh -c #(nop) ADD file:e69d441d729412d24…   5.59MB   
    ```

    Jede Zeile stellt eine Ebene im Bild dar. In der hier angezeigten Anzeige wird die Basis unten mit der neuesten Ebene angezeigt. Dadurch können Sie auch schnell die Größe der einzelnen Ebenen anzeigen, um große Images zu diagnostizieren.

1. Sie werden feststellen, dass einige der Zeilen abgeschnitten werden. Wenn Sie das- `--no-trunc` Flag hinzufügen, erhalten Sie die vollständige Ausgabe (ja, Sie verwenden ein abgeschnittenes Flag, um eine nicht gekürzte Ausgabe zu erhalten).

    ```bash
    docker image history --no-trunc getting-started
    ```

## <a name="layer-caching"></a>Ebenencaching

Nachdem Sie nun die Schichten in Aktion gesehen haben, ist eine wichtige Lektion zu erlernen, die Ihnen hilft, die Buildzeiten für Ihre Container Images zu verkürzen.

> Nachdem sich eine Ebene geändert hat, müssen alle downstreamschichten ebenfalls neu erstellt werden.

Sehen wir uns nun die dockerfile-Datei an, die Sie noch einmal verwendet haben...

```dockerfile
FROM node:12-alpine
WORKDIR /app
COPY . .
RUN yarn install --production
CMD ["node", "/app/src/index.js"]
```

Wenn Sie zur Ausgabe des Image Verlaufs zurückkehren, sehen Sie, dass jeder Befehl in der dockerfile-Datei zu einer neuen Ebene im Image wird. Möglicherweise erinnern Sie sich daran, dass bei einer Änderung an dem Image die Yarn-Abhängigkeiten neu installiert werden mussten. Gibt es eine Möglichkeit, dieses Problem zu beheben? Es ist nicht sinnvoll, bei jeder Erstellung dieselben Abhängigkeiten zu liefern.

Um dieses Problem zu beheben, können Sie die dockerfile-Datei neu strukturieren, um das Zwischenspeichern der Abhängigkeiten zu unterstützen. Bei Knoten basierten Anwendungen werden diese Abhängigkeiten in der `package.json` Datei definiert. Was geschieht, wenn Sie nur diese Datei in zuerst kopiert, die Abhängigkeiten installieren und *dann* in alles andere kopieren? Anschließend erstellen Sie nur die Yarn-Abhängigkeiten neu, wenn eine Änderung an der vorgenommen wurde `package.json` . Sinn machen?

1. Aktualisieren Sie die dockerfile-Datei, um Sie in die erste zu kopieren `package.json` , installieren Sie Abhängigkeiten, und kopieren Sie alles andere in.

    ```dockerfile hl_lines="3 4 5"
    FROM node:12-alpine
    WORKDIR /app
    COPY package.json yarn.lock ./
    RUN yarn install --production
    COPY . .
    CMD ["node", "/app/src/index.js"]
    ```

1. Erstellen Sie mithilfe von ein neues Image `docker build` .

    ```bash
    docker build -t getting-started .
    ```

    Es sollte eine Ausgabe wie die folgende angezeigt werden...

    ```plaintext
    Sending build context to Docker daemon  219.1kB
    Step 1/6 : FROM node:12-alpine
    ---> b0dc3a5e5e9e
    Step 2/6 : WORKDIR /app
    ---> Using cache
    ---> 9577ae713121
    Step 3/6 : COPY package* yarn.lock ./
    ---> bd5306f49fc8
    Step 4/6 : RUN yarn install --production
    ---> Running in d53a06c9e4c2
    yarn install v1.17.3
    [1/4] Resolving packages...
    [2/4] Fetching packages...
    info fsevents@1.2.9: The platform "linux" is incompatible with this module.
    info "fsevents@1.2.9" is an optional dependency and failed compatibility check. Excluding it from installation.
    [3/4] Linking dependencies...
    [4/4] Building fresh packages...
    Done in 10.89s.
    Removing intermediate container d53a06c9e4c2
    ---> 4e68fbc2d704
    Step 5/6 : COPY . .
    ---> a239a11f68d8
    Step 6/6 : CMD ["node", "/app/src/index.js"]
    ---> Running in 49999f68df8f
    Removing intermediate container 49999f68df8f
    ---> e709c03bc597
    Successfully built e709c03bc597
    Successfully tagged getting-started:latest
    ```

    Sie werden feststellen, dass alle Ebenen neu erstellt wurden. Ganz einfach, da Sie die dockerfile-Datei etwas geändert haben.

1. Nehmen Sie nun eine Änderung an der `src/static/index.html` Datei vor (wie z `<title>` . b. Ändern von "the awesome ToDo APP").

1. Erstellen Sie das docker-Image jetzt `docker build` erneut. Dieses Mal sollte die Ausgabe etwas anders aussehen.

    ```plaintext hl_lines="5 8 11"
    Sending build context to Docker daemon  219.1kB
    Step 1/6 : FROM node:12-alpine
    ---> b0dc3a5e5e9e
    Step 2/6 : WORKDIR /app
    ---> Using cache
    ---> 9577ae713121
    Step 3/6 : COPY package* yarn.lock ./
    ---> Using cache
    ---> bd5306f49fc8
    Step 4/6 : RUN yarn install --production
    ---> Using cache
    ---> 4e68fbc2d704
    Step 5/6 : COPY . .
    ---> cccde25a3d9a
    Step 6/6 : CMD ["node", "/app/src/index.js"]
    ---> Running in 2be75662c150
    Removing intermediate container 2be75662c150
    ---> 458e5c6f080c
    Successfully built 458e5c6f080c
    Successfully tagged getting-started:latest
    ```

    Zuerst sollten Sie feststellen, dass der Build viel schneller war! Und Sie sehen, dass die Schritte 1-4 alle enthalten `Using cache` . Und so: Sie verwenden den buildcache. Das übertragen und ziehen dieses Abbilds und Updates an dieses Bild werden ebenfalls viel schneller. Hurra!

## <a name="multi-stage-builds"></a>Mehrstufige Builds

Wir werden uns in diesem Tutorial nicht zu viel ansehen, aber mehrstufige Builds sind ein unglaublich leistungsfähiges Tool, mit dem Sie mehrere Stufen zum Erstellen eines Images verwenden können. Hierfür gibt es mehrere Vorteile:

- Trennen von Abhängigkeiten der Build-Zeit von Laufzeitabhängigkeiten
- Reduzieren Sie die Gesamtgröße des Images, indem Sie *nur* das Ausführen, was Ihre APP ausführen muss

### <a name="maventomcat-example"></a>Maven/Tomcat-Beispiel

Beim Erstellen von Java-basierten Anwendungen ist ein JDK erforderlich, um den Quellcode in Java-Bytecode zu kompilieren. Allerdings ist dieses JDK nicht in der Produktionsumgebung erforderlich. Sie können auch Tools wie Maven oder gradle verwenden, um die APP zu erstellen.
Diese werden auch in ihrem endgültigen Image nicht benötigt. Hilfe zu mehrstufigen Builds.

```dockerfile
FROM maven AS build
WORKDIR /app
COPY . .
RUN mvn package

FROM tomcat
COPY --from=build /app/target/file.war /usr/local/tomcat/webapps 
```

In diesem Beispiel wird eine Stufe ( `build` mit dem Namen) verwendet, um den eigentlichen Java-Build mithilfe von Maven auszuführen. In der zweiten Phase (beginnend bei `FROM tomcat` ) werden Dateien aus der `build` Stufe kopiert. Das abschließende Bild ist nur die letzte Phase, die erstellt wird (die mit dem-Flag überschrieben werden kann `--target` ).

### <a name="react-example"></a>Beispiel für Reaktion

Beim Erstellen von Anwendungen, die reagieren, benötigen Sie eine Node-Umgebung, um den JS-Code (in der Regel jsx), Sass-Stylesheets und vieles mehr in statische HTML, js und CSS zu kompilieren. Wenn Sie kein serverseitiges Rendering durchgeführt haben, benötigen Sie nicht einmal eine Node-Umgebung für den produktionsbuild. Warum werden die statischen Ressourcen nicht in einem statischen nginx-Container ausgeliefert?

```dockerfile
FROM node:12 AS build
WORKDIR /app
COPY package* yarn.lock ./
RUN yarn install
COPY public ./public
COPY src ./src
RUN yarn run build

FROM nginx:alpine
COPY --from=build /app/build /usr/share/nginx/html
```

Hier verwenden Sie ein `node:12` Bild zum Durchführen des Builds (Maximieren der ebenenzwischenspeicherung) und anschließendes Kopieren der Ausgabe in einen nginx-Container. Cool, huh?

## <a name="recap"></a>Zusammenfassung

Wenn Sie etwas über die Struktur von Bildern wissen, können Sie Images schneller erstellen und weniger Änderungen liefern. Mehrstufige Builds helfen auch, die gesamte Abbild Größe zu verringern und die endgültige Containersicherheit zu erhöhen, indem die Build-Zeit Abhängigkeiten von Laufzeitabhängigkeiten getrennt werden.

## <a name="next-steps"></a>Nächste Schritte

Fahren Sie mit dem Tutorial fort.

> [!div class="nextstepaction"]
> [Bereitstellen in der Cloud](deploy-to-cloud.md)