---
title: 'Erstellen einer Node.js-Entwicklungsumgebung mit Containern unter Verwendung von Kubernetes in der Cloud, Schritt 3: Erstellen einer ASP.NET-Web-App | Microsoft-Dokumentation'
author: johnsta
ms.author: johnsta
ms.date: 02/20/2018
ms.topic: get-started-article
ms.technology: vsce-kubernetes
description: Schnelle Kubernetes-Entwicklung mit Containern und Microservices in Azure
keywords: Docker, Kubernetes, Azure, AKS, Azure Container Service, Container
manager: ghogen
ms.openlocfilehash: 26d6753bf17b459c33cd11c46186d272d477fe10
ms.sourcegitcommit: 900ed1e299cd5bba56249cef8f5cf3981b10cb1c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/19/2018
---
# <a name="get-started-on-connected-environment-with-nodejs"></a>Erste Schritte in Connected Environment mit Node.js

Vorheriger Schritt: [Erstellen einer Kubernetes-Entwicklungsumgebung in Azure](get-started-nodejs-02.md)

## <a name="create-a-nodejs-web-app"></a>Erstellen einer Node.js-Web-App
Laden Sie Code von GitHub herunter, indem Sie zu https://github.com/Azure/vsce navigieren und auf **Clone or Download** (Klonen oder herunterladen) klicken, um das GitHub-Repository in Ihre lokale Umgebung herunterzuladen. Der Code für diese Anleitung befindet sich unter `vsce/samples/nodejs/getting-started/webfrontend`.

[!INCLUDE[](includes/vsce-init.md)]

[!INCLUDE[](includes/ensure-env-created.md)]

[!INCLUDE[](includes/build-and-run-in-k8s-cli.md)]

## <a name="update-a-content-file"></a>Aktualisieren einer Inhaltsdatei
Bei Connected Environment dreht es sich nicht nur darum, Code in Kubernetes ausführen zu können. Es soll Ihnen ebenfalls ermöglicht werden, schnell und iterativ zu verfolgen, wie Ihre Codeänderungen in einer Kubernetes-Umgebung in der Cloud wirksam werden.

1. Suchen Sie die Datei `./public/index.html`, und nehmen Sie eine Änderung am HTML-Code vor. Sie können z.B. die Hintergrundfarbe der Seite in einen Blauton ändern.

```html
<body style="background-color: #95B9C7; margin-left:10px; margin-right:10px;">
```

2. Speichern Sie die Datei. Kurz darauf wird Ihnen im Terminalfenster die Meldung angezeigt, dass eine Datei im ausgeführten Container aktualisiert wurde.
1. Wechseln Sie zu Ihrem Browser, und aktualisieren Sie die Seite. Die Farbe sollte sich nun geändert haben.

Was ist passiert? Änderungen an Inhaltsdateien wie HTML- und CSS-Dateien erfordern keinen Neustart des Node.js-Prozesses. Deshalb synchronisiert ein aktiver `vsce up`-Befehl automatisch alle geänderten Inhaltsdateien direkt im ausgeführten Container in Azure. Dadurch können Ihre Änderungen an Inhalten schneller angezeigt werden.

### <a name="test-from-a-mobile-device"></a>Testen über ein mobiles Gerät
Wenn Sie die Web-App über ein mobiles Gerät öffnen, sollten Sie feststellen, dass die Benutzeroberfläche auf kleineren Geräten nicht richtig angezeigt wird.

Um dieses Problem zu beheben, können Sie ein `viewport`-META-Tag hinzufügen:
1. Öffnen Sie die Datei `./public/index.html`.
1. Fügen Sie zu dem bereits vorhandenen `head`-Element ein `viewport`-META-Tag hinzu:

```html
<head>
    <!-- Add this line -->
    <meta name="viewport" content="width=device-width, initial-scale=1">
</head>
```

1. Speichern Sie die Datei.
1. Aktualisieren Sie den Browser Ihres Geräts. Die Web-App sollte nun richtig gerendert werden. 

Dieses Beispiel macht deutlich, dass einige Probleme erst gefunden werden, wenn Sie die App auf den Geräten testen, für die sie bestimmt ist. Mithilfe von Visual Studio Connected Environment können Sie Ihren Code schnell durchlaufen und jegliche Änderungen auf den Zielgeräten überprüfen.

## <a name="update-a-code-file"></a>Aktualisieren einer Codedatei
Das Aktualisieren von Codedateien auf Serverseite erfordert ein wenig mehr Arbeit, da dafür eine Node.js-App neu gestartet werden muss.

1. Drücken Sie im Terminalfenster `Ctrl+C`, um `vsce up` zu beenden.
1. Öffnen Sie die Codedatei mit dem Namen `server.js`, und bearbeiten Sie die Begrüßungsmeldung des Dienstes: 

```javascript
res.send('Hello from webfrontend running in Azure!');
```

3. Speichern Sie die Datei.
1. Führen Sie `vsce up` im Terminalfenster aus. 

Dadurch wird das Containerimage neu erstellt, und das Helm-Diagramm wird erneut bereitgestellt. Laden Sie die Browserseite neu, damit Ihre Codeänderungen angewendet werden können.


Es gibt jedoch noch eine *schnellere Methode* zum Entwickeln von Code. Diese wird im nächsten Abschnitt erläutert. 
> [!div class="nextstepaction"]
> [Debuggen eines Containers in Kubernetes](get-started-nodejs-04.md)
