---
title: 'Erstellen einer .NET Core-Entwicklungsumgebung mit Containern unter Verwendung von Kubernetes in der Cloud, Schritt 3: Erstellen einer ASP.NET Core-Web-App | Microsoft-Dokumentation'
author: johnsta
ms.author: johnsta
ms.date: 02/20/2018
ms.topic: get-started-article
ms.technology: vsce-kubernetes
description: Schnelle Kubernetes-Entwicklung mit Containern und Microservices in Azure
keywords: Docker, Kubernetes, Azure, AKS, Azure Container Service, Container
manager: ghogen
ms.openlocfilehash: f858a013e4b0c2ce1c30b8f26f2dc33eebf19c27
ms.sourcegitcommit: 900ed1e299cd5bba56249cef8f5cf3981b10cb1c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/19/2018
---
# <a name="get-started-on-connected-environment-with-net-core"></a>Erste Schritte in Connected Environment mit .NET Core

Vorheriger Schritt: [Erstellen einer Kubernetes-Entwicklungsumgebung in Azure](get-started-netcore-02.md)

## <a name="create-an-aspnet-core-web-app"></a>Erstellen einer ASP.NET Core-Web-App
Wenn Sie [.NET Core](https://www.microsoft.com/net) installiert haben, können Sie eine ASP.NET Core-Web-App schnell in einem Ordner namens `webfrontend` erstellen.
```cmd
dotnet new mvc --name webfrontend
```

Alternativ **können Sie Beispielcode von GitHub herunterladen**, indem Sie zu https://github.com/Azure/vsce navigieren und **Clone or Download** (Klonen oder herunterladen) anklicken, um das GitHub-Repository in Ihre lokale Umgebung herunterzuladen. Der Code für diesen Leitfaden befindet sich unter `vsce/samples/dotnetcore/getting-started/webfrontend`.

[!INCLUDE[](includes/vsce-init.md)]

[!INCLUDE[](includes/ensure-env-created.md)]

[!INCLUDE[](includes/build-and-run-in-k8s-cli.md)]

## <a name="update-a-content-file"></a>Aktualisieren einer Inhaltsdatei
Bei Connected Environment dreht es sich nicht nur darum, Code in Kubernetes ausführen zu können. Es soll Ihnen ebenfalls ermöglicht werden, schnell und iterativ zu verfolgen, wie Ihre Codeänderungen in einer Kubernetes-Umgebung in der Cloud wirksam werden.

1. Suchen Sie die Datei `./Views/Home/Index.cshtml`, und nehmen Sie eine Änderung im HTML-Code vor. Ändern Sie beispielsweise Zeile 70 (`<h2>Application uses</h2>`) in `<h2>Hello k8s in Azure!</h2>`.
1. Speichern Sie die Datei. Kurz darauf wird Ihnen im Terminalfenster die Meldung angezeigt, dass eine Datei im ausgeführten Container aktualisiert wurde.
1. Wechseln Sie zu Ihrem Browser, und aktualisieren Sie die Seite. Die Webseite sollte nun den aktualisierten Inhalt anzeigen.

Was ist passiert? Änderungen an Inhaltsdateien wie HTML- und CSS-Dateien erfordern keine erneute Kompilierung in einer .NET Core-Web-App. Deshalb synchronisiert ein aktiver `vsce up`-Befehl automatisch alle geänderten Inhaltsdateien im ausgeführten Container in Azure. Dadurch können Ihre Änderungen an Inhalten schneller angezeigt werden.

## <a name="update-a-code-file"></a>Aktualisieren einer Codedatei
Das Aktualisieren von Codedateien erfordert mehr Arbeit, da eine .NET Core-App erneut erstellt werden und aktualisierte Anwendungsbinärdateien erzeugen muss.

1. Drücken Sie im Terminalfenster `Ctrl+C`, um `vsce up` zu beenden.
1. Öffnen Sie die Codedatei namens `Controllers/HomeController.cs`, und bearbeiten Sie die Meldung, die auf der Seite „Info“ angezeigt wird: `ViewData["Message"] = "Your application description page.";`.
1. Speichern Sie die Datei.
1. Führen Sie `vsce up` im Terminalfenster aus. 

Dadurch wird das Containerimage neu erstellt, und das Helm-Diagramm wird erneut bereitgestellt. Navigieren Sie zum Menü „Info“ in der Web-App, um zu sehen, wie Ihre Codeänderung in der laufenden Anwendung wirksam werden.


Es gibt jedoch noch eine *schnellere Methode* zum Entwickeln von Code. Diese wird im nächsten Abschnitt erläutert. 
> [!div class="nextstepaction"]
> [Debuggen eines Containers in Kubernetes](get-started-netcore-04.md)

