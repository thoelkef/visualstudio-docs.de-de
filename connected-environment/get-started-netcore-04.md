---
title: 'Erstellen einer .NET Core-Entwicklungsumgebung mit Containern unter Verwendung von Kubernetes in der Cloud, Schritt 4: Debuggen eines Containers in Kubernetes | Microsoft-Dokumentation'
author: johnsta
ms.author: johnsta
ms.date: 02/20/2018
ms.topic: get-started-article
ms.technology: vsce-kubernetes
description: Schnelle Kubernetes-Entwicklung mit Containern und Microservices in Azure
keywords: Docker, Kubernetes, Azure, AKS, Azure Container Service, Container
manager: ghogen
ms.openlocfilehash: f06489194f70a3e7e617f4022917cd1d4a96337f
ms.sourcegitcommit: 900ed1e299cd5bba56249cef8f5cf3981b10cb1c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/19/2018
---
# <a name="get-started-on-connected-environment-with-net-core"></a>Erste Schritte in Connected Environment mit .NET Core
 
Vorheriger Schritt: [Erstellen einer ASP.NET Core-Web-App](get-started-netcore-03.md)

[!INCLUDE[](includes/debug-intro.md)]

[!INCLUDE[](includes/init-debug-assets-vscode.md)]


## <a name="select-the-vsce-debug-configuration"></a>Auswählen der VSCE-Debugkonfiguration
1. Klicken Sie auf das Debuggersymbol in der **Aktivitätsleiste** neben Visual Studio Code, um die Debugansicht zu öffnen.
1. Wählen Sie **.NET Core Launch (VSCE)** (.NET Core-Start (VSCE)) als die aktive Debugkonfiguration aus.

![](media/debug-configuration.png)

> [!Note]
> Wenn keine Befehle für Connected Environment in der Befehlspalette angezeigt werden, stellen Sie sicher, dass Sie die [Visual Studio Code-Erweiterung für Connected Environment installiert haben](get-started-netcore-01.md#get-kubernetes-debugging-for-vs-code).


## <a name="debug-the-container-in-kubernetes"></a>Debuggen von Containern in Kubernetes
Drücken Sie **F5**, um Ihren Code in Kubernetes zu debuggen.

Ähnlich wie beim `up`-Befehl, wird der Code mit der Entwicklungsumgebung synchronisiert und ein Container wird erstellt und in Kubernetes bereitgestellt. Diesmal ist der Debugger an den Remotecontainer angeheftet.

[!INCLUDE[](includes/tip-vscode-status-bar-url.md)]

Legen Sie einen Breakpoint in einer serverseitigen Codedatei fest, z.B. in der `Index()`-Funktion in der Quelldatei `Controllers/HomeController.cs`. Aktualisieren der Browserseite löst den Breakpoint aus.

Genau wie bei lokal ausgeführtem Code verfügen Sie über Vollzugriff auf die Debuginformationen, z.B. die Aufrufliste, lokale Variablen, Ausnahmeinformationen usw.

## <a name="edit-code-and-refresh"></a>Bearbeiten und Aktualisieren von Code
Bearbeiten Sie den Code, während der Debugger aktiv ist. Ändern Sie zum Beispiel die Nachricht in `Controllers/HomeController.cs` auf der Seite „Info“. 

```csharp
public IActionResult About()
{
    ViewData["Message"] = "My custom message in the About page.";
    return View();
}
```

Speichern Sie die Datei, und klicken Sie auf die Schaltfläche **Aktualisieren** im Bereich **Debugaktionen**. 

![](media/debug-action-refresh.png)

Anstatt bei jeder Codeänderung ein neues Containerimage zu erstellen und bereitzustellen, was häufig viel Zeit beansprucht, kompiliert Visual Studio Connected Environment den Code inkrementell erneut in dem vorhandenen Container, um die Bearbeitungs- und Debugschleife zu beschleunigen.

Aktualisieren Sie die Web-App im Browser, und navigieren Sie zur Seite „Info“. Ihre benutzerdefinierte Nachricht sollte nun auf der Benutzeroberfläche angezeigt werden.

**Sie verfügen jetzt über eine Methode, mit der Sie direkt in Kubernetes schnell auf Ihrem Code aufbauen und diesen debuggen können.** Als Nächstes erfahren Sie, wie Sie einen zweiten Container erstellen und aufrufen.

> [!div class="nextstepaction"]
> [Aufrufen eines Diensts, der in einem separaten Container ausgeführt wird](get-started-netcore-05.md)
