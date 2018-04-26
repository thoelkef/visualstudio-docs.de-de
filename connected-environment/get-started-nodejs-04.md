---
title: 'Erstellen einer Node.js-Entwicklungsumgebung mit Containern unter Verwendung von Kubernetes in der Cloud, Schritt 4: Debuggen eines Containers in Kubernetes | Microsoft-Dokumentation'
author: ghogen
ms.author: ghogen
ms.date: 02/20/2018
ms.topic: tutorial
ms.prod: visual-studio-dev15
ms.technology: vs-azure
description: Schnelle Kubernetes-Entwicklung mit Containern und Microservices in Azure
keywords: Docker, Kubernetes, Azure, AKS, Azure Container Service, Container
manager: douge
ms.openlocfilehash: 2d1ec5fe0436b394083a247faa4519505aa21ceb
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
---
# <a name="get-started-on-connected-environment-with-nodejs"></a>Erste Schritte in Connected Environment mit Node.js

Vorheriger Schritt: [Erstellen eines Node.js-Containers in Kubernetes](get-started-nodejs-03.md)

[!INCLUDE[](includes/debug-intro.md)]

[!INCLUDE[](includes/init-debug-assets-vscode.md)]


## <a name="select-the-vsce-debug-configuration"></a>Auswählen der Debugkonfiguration für Visual Studio Connected Environment (VSCE)
1. Klicken Sie auf das Debuggersymbol in der **Aktivitätsleiste** neben Visual Studio Code, um die Debugansicht zu öffnen.
1. Wählen Sie **Launch Program (VSCE)** ((VSCE)-Programm starten) als aktive Debugkonfiguration aus.

![](media/debug-configuration-nodejs.png)

> [!Note]
> Wenn keine Befehle für Connected Environment in der Befehlspalette angezeigt werden, stellen Sie sicher, dass Sie die [VS Code-Erweiterung für Connected Environment installiert haben](get-started-nodejs-01.md#get-kubernetes-debugging-for-vs-code).

## <a name="debug-the-container-in-kubernetes"></a>Debuggen von Containern in Kubernetes
Drücken Sie **F5**, um Ihren Code in Kubernetes zu debuggen.

Ähnlich wie beim `up`-Befehl wird der Code mit der Entwicklungsumgebung synchronisiert, wenn Sie mit dem Debuggen beginnen, und es wird ein Container erstellt und für Kubernetes bereitgestellt. Dieses Mal ist der Debugger an den Remotecontainer angeheftet.

[!INCLUDE[](includes/tip-vscode-status-bar-url.md)]

Legen Sie einen Breakpoint in einer serverseitigen Codedatei fest, z.B. innerhalb von `app.get('/api'...` in `server.js`. Aktualisieren Sie die Browserseite, oder drücken Sie auf die Schaltfläche „Say it again“ (Wiederholen). Dann sollten Sie den Breakpoint erreichen und den Code ausführlich überprüfen können.

Genau wie bei lokal ausgeführtem Code verfügen Sie über Vollzugriff auf die Debuginformationen, z.B. die Aufrufliste, lokale Variablen, Ausnahmeinformationen usw.

## <a name="edit-code-and-refresh-the-debug-session"></a>Bearbeiten von Code und Aktualisieren der Debugsitzung
Lassen Sie den Debugger aktiviert, und bearbeiten Sie den Code. Sie können beispielsweise die Begrüßungsmeldung erneut bearbeiten:

```javascript
app.get('/api', function (req, res) {
    res.send('**** Hello from webfrontend running in Azure! ****');
});
```

Speichern Sie die Datei, und klicken Sie auf die Schaltfläche **Aktualisieren** im Bereich **Debugaktionen**. 

![](media/debug-action-refresh-nodejs.png)

Es muss nicht mehr aufwendig bei jeder Änderung des Codes ein neues Containerimage erstellt und erneut bereitgestellt werden. Stattdessen startet Connected Environment den Node.js-Prozess zwischen einzelnen Debugsitzungen neu, um die Bearbeitungs- und Debugschleife zu beschleunigen.

Aktualisieren Sie die Web-App im Browser, oder drücken Sie auf die Schaltfläche *Say It Again* (Wiederholen). Ihre benutzerdefinierte Nachricht sollte nun auf der Benutzeroberfläche angezeigt werden.


## <a name="use-nodemon-to-develop-even-faster"></a>Verwenden von Nodemon zur schnelleren Entwicklung
Bei *Nodemon* handelt es sich um ein beliebtes Tool, das Node.js-Entwickler verwenden, um den Entwicklungsprozess zu beschleunigen. Sie starten den Node-Prozess nicht mehr bei jeder Codeänderung auf Serverseite manuell neu, sondern konfigurieren Ihre Node-Projekte so, dass *Nodemon* Änderungen an den Dateien überwacht und den Serverprozess automatisch neu startet. Im Zusammenhang mit dieser Vorgehensweise aktualisieren die Entwickler nur Ihre Browser, nachdem sie ihren Code verändert haben.

Connected Environment soll es Ihnen ermöglichen, dieselben produktiven Entwicklungsworkflows wie bei der lokalen Entwicklung zu verwenden. Das Beispielprojekt `webfrontend` wurde für die Verwendung von *Nodemon* (als Entwicklungsabhängigkeit in `package.json`) konfiguriert, um dies darzustellen.

Versuchen Sie Folgendes:
1. Beenden Sie den VS Code-Debugger.
1. Klicken Sie auf das Debuggersymbol in der **Aktivitätsleiste** an der Seite von VS Code. 
1. Wählen Sie **Attach (VSCE)** (Anfügen (VSCE)) als aktive Debugkonfiguration aus.
1. Drücken Sie F5.

In dieser Konfiguration ist der Container für den Start von *Nodemon* konfiguriert. Wenn Änderungen am Servercode vorgenommen werden, startet *Nodemon* wie bei der lokalen Entwicklung den Node-Prozess automatisch neu. 
1. Bearbeiten Sie die Begrüßungsmeldung erneut in `server.js`, und speichern Sie die Datei.
1. Aktualisieren Sie den Browser, oder klicken Sie auf die Schaltfläche *Say It Again* (Wiederholen), damit Ihre Änderungen übernommen werden.

**Sie verfügen jetzt über eine Methode, mit der Sie direkt in Kubernetes schnell auf Ihrem Code aufbauen und diesen debuggen können.** Als Nächstes erfahren Sie, wie Sie einen zweiten Container erstellen und aufrufen können.

> [!div class="nextstepaction"]
> [Aufrufen eines Diensts, der in einem separaten Container ausgeführt wird](get-started-nodejs-05.md)

