---
title: 'Erstellen einer Node.js-Entwicklungsumgebung mit Containern unter Verwendung von Kubernetes in der Cloud, Schritt 5: Aufrufen eines weiteren Containers | Microsoft-Dokumentation'
author: ghogen
ms.author: ghogen
ms.date: 02/20/2018
ms.topic: tutorial
ms.prod: visual-studio-dev15
ms.technology: vs-azure
description: Schnelle Kubernetes-Entwicklung mit Containern und Microservices in Azure
keywords: Docker, Kubernetes, Azure, AKS, Azure Container Service, Container
manager: douge
ms.openlocfilehash: 89565869feec746aff75327b59ee7d0b466f26c1
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
---
# <a name="get-started-on-connected-environment-with-nodejs"></a>Erste Schritte in Connected Environment mit Node.js

Vorheriger Schritt: [Debuggen eines Containers in Kubernetes](get-started-nodejs-04.md)

Im folgenden Abschnitt soll ein zweiter Dienst (`mywebapi`) erstellt werden, der von `webfrontend` aufgerufen werden soll. Jeder Dienst wird in einem separaten Container ausgeführt. Anschließend wird der Debugvorgang in beiden Containern ausgeführt.

![](media/multi-container.png)

## <a name="open-sample-code-for-mywebapi"></a>Öffnen von Beispielcode für *mywebapi*
Der Beispielcode für `mywebapi`, der zu dieser Anleitung gehört, sollte bereits in dem Ordner mit dem Namen `vsce/samples` gespeichert sein. Falls dies jedoch nicht der Fall ist, navigieren Sie zu https://github.com/Azure/vsce, klicken Sie auf **Clone or Download** (Klonen oder herunterladen), um das GitHub-Repository herunterzuladen. Sie finden den Code, der für den folgenden Abschnitt benötigt wird, unter `vsce/samples/nodejs/getting-started/mywebapi`.

## <a name="run-mywebapi"></a>Ausführen von *mywebapi*
1. Öffnen Sie den Ordner `mywebapi` in einem *separaten Visual Studio Code-Fenster*.
1. Drücken Sie F5, und warten Sie, bis der Dienst erstellt und bereitgestellt wurde. Die Leiste „Debuggen“ für Visual Studio Code wird nach dem Abschluss des Vorgangs angezeigt.
1. Beachten Sie die Endpunkt-URL, die etwa folgendermaßen aussehen sollte: http://localhost:\<portnumber\>. **Tipp: Die Statusleiste in Visual Studio Code zeigt eine klickbare URL an.** Möglicherweise sieht es so aus, als werde der Container lokal ausgeführt, obwohl er eigentlich in der Entwicklungsumgebung in Azure ausgeführt wird. Die Adresse des Localhosts lautet wie oben genannt, da für `mywebapi` keine öffentlichen Endpunkte definiert sind und auf dieses Element nur über eine Kubernetes-Instanz zugegriffen werden kann. Der Einfachheit halber und zur Vereinfachung der Interaktion mit dem privaten Dienst Ihres lokalen Computers erstellt Connected Environment einen temporären SSH-Tunnel zu dem in Azure ausgeführten Container.
1. Öffnen Sie über Ihren Browser die Adresse des Localhosts, wenn `mywebapi` bereit ist. Dann sollte Ihnen eine Antwort des `mywebapi`-Diensts angezeigt werden („Hello from mywebapi“ (Willkommen bei mywebapi)).


## <a name="make-a-request-from-webfrontend-to-mywebapi"></a>Senden einer Anforderung an *mywebapi* über *webfrontend*
Im Folgenden wird erläutert, wie Sie Code in `webfrontend` schreiben, um eine Anforderung an `mywebapi` zu senden.
1. Wechseln Sie im Visual Studio Code-Fenster zu `webfrontend`.
1. Fügen Sie im oberen Bereich von `server.js` die folgenden Zeilen hinzu:
```javascript
var request = require('request');
var propagateHeaders = require('./propagateHeaders');
```

3. *Ersetzen* Sie den Code für den GET-Handler `/api`. Wenn dieser eine Anforderung verarbeitet, ruft er wiederum `mywebapi` auf und gibt anschließend die Ergebnisse beider Dienste zurück.

```javascript
app.get('/api', function (req, res) {
    request({
        uri: 'http://mywebapi',
        headers: propagateHeaders.from(req) // propagate headers to outgoing requests
    }, function (error, response, body) {
        res.send('Hello from webfrontend and ' + body);
    });
});
```

Beachten Sie, wie die DNS-Dienstsuche von Kubernetes genutzt wird, um auf den Dienst als `http://mywebapi` zu verweisen. **Der Code wird in der Entwicklungsumgebung auf dieselbe Weise ausgeführt wie während der Produktion.**

Im obenstehenden Codebeispiel wird ein Hilfsprogrammmodul mit dem Namen `propagateHeaders` verwendet. Dieses Hilfsprogramm wurde zu Ihrem Codeordner hinzugefügt, als Sie `vsce init` ausgeführt haben. Die `propagateHeaders.from()`-Funktion verteilt bestimmte Header von einem bestimmten http.IncomingMessage-Objekt an ein Headerobjekt für eine ausgehende Anforderung. Nachfolgend wird erläutert, wie mithilfe dieses Vorgangs das Entwickeln im Team produktiver gestaltet werden kann.


## <a name="debug-across-multiple-services"></a>Debuggen für mehrere Dienste
1. Zum jetzigen Zeitpunkt sollte an das `mywebapi`-Element immer noch der Debugger angefügt sein. Außerdem sollte es weiterhin ausgeführt werden. Wenn dies nicht der Fall ist, drücken Sie im `mywebapi`-Projekt F5.
1. Legen Sie im Standard-GET-Handler `/` einen Breakpoint fest.
1. Legen Sie im `webfrontend`-Projekt einen Breakpoint fest, bevor eine GET-Anforderung an `http://mywebapi` gesendet wird.
1. Drücken Sie im `webfrontend`-Projekt F5.
1. Öffnen Sie die Web-App, und überprüfen Sie in beiden Diensten ausführlich den Code. In der Web-App sollte eine Nachricht angezeigt werden, die von diesen beiden Diensten verkettet wird: „Hello from webfrontend and Hello from mywebapi“ (Willkommen bei webfrontend und Willkommen bei mywebapi).


Und das war‘s schon. Sie verfügen jetzt über eine Anwendung mit mehreren Containern, in der jeder Container separat entwickelt und bereitgestellt werden kann.

> [!div class="nextstepaction"]
> [Informationen zur Entwicklung im Team](get-started-nodejs-06.md)
