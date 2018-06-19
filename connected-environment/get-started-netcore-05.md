---
title: 'Erstellen einer .NET Core-Entwicklungsumgebung mit Containern unter Verwendung von Kubernetes in der Cloud, Schritt 5: Aufrufen eines weiteren Containers | Microsoft-Dokumentation'
author: ghogen
ms.author: ghogen
ms.date: 02/20/2018
ms.topic: tutorial
ms.prod: visual-studio-dev15
ms.technology: vs-azure
description: Schnelle Kubernetes-Entwicklung mit Containern und Microservices in Azure
keywords: Docker, Kubernetes, Azure, AKS, Azure Container Service, Container
manager: douge
ms.openlocfilehash: 6ef3a79d0b79feae64adcaebe31daa48ba75ab75
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
ms.locfileid: "31887335"
---
# <a name="get-started-on-connected-environment-with-net-core"></a>Erste Schritte in Connected Environment mit .NET Core

Vorheriger Schritt: [Debuggen eines Containers in Kubernetes](get-started-netcore-04.md)

Im folgenden Abschnitt soll ein zweiter Dienst (`mywebapi`) erstellt werden, der von `webfrontend` aufgerufen werden soll. Jeder Dienst wird in einem separaten Container ausgeführt. Anschließend wird der Debugvorgang in beiden Containern ausgeführt.

![](media/multi-container.png)

## <a name="download-sample-code-for-mywebapi"></a>Herunterladen von Beispielcode für *mywebapi*
Laden Sie Beispielcode aus einem GitHub-Repository herunter, um Zeit zu sparen. Navigieren Sie zu https://github.com/Azure/vsce, und klicken Sie auf **Clone or Download** (Klonen oder herunterladen), um das GitHub-Repository herunterzuladen. Sie finden den Code, der für den folgenden Abschnitt benötigt wird, unter `vsce/samples/dotnetcore/getting-started/mywebapi`.


## <a name="run-mywebapi"></a>Ausführen von *mywebapi*
1. Öffnen Sie den Ordner `mywebapi` in einem *separaten Visual Studio Code-Fenster*.
1. Drücken Sie F5, und warten Sie, bis der Dienst erstellt und bereitgestellt wurde. Die Leiste „Debuggen“ für Visual Studio Code wird nach dem Abschluss des Vorgangs angezeigt.
1. Beachten Sie die Endpunkt-URL, die etwa folgendermaßen aussehen sollte: http://localhost:\<portnumber\>. **Tipp: Die Statusleiste in Visual Studio Code zeigt eine klickbare URL an.** Möglicherweise sieht es so aus, als werde der Container lokal ausgeführt, obwohl er eigentlich in der Entwicklungsumgebung in Azure ausgeführt wird. Die Adresse des Localhosts lautet wie oben genannt, da für `mywebapi` keine öffentlichen Endpunkte definiert sind und auf dieses Element nur über eine Kubernetes-Instanz zugegriffen werden kann. Der Einfachheit halber und zur Vereinfachung der Interaktion mit dem privaten Dienst Ihres lokalen Computers erstellt Connected Environment einen temporären SSH-Tunnel zu dem in Azure ausgeführten Container.
1. Öffnen Sie über Ihren Browser die Adresse des Localhosts, wenn `mywebapi` bereit ist. Fügen Sie `/api/values` an die URL an, um die Standard-GET-API für `ValuesController` aufzurufen. 
1. Wenn alle Schritte erfolgreich ausgeführt wurden, wird Ihnen eine Antwort des `mywebapi`-Diensts angezeigt.


## <a name="make-a-request-from-webfrontend-to-mywebapi"></a>Senden einer Anforderung an *mywebapi* über *webfrontend*
Im Folgenden wird erläutert, wie Sie Code in `webfrontend` schreiben, um eine Anforderung an `mywebapi` zu senden.
1. Wechseln Sie im Visual Studio Code-Fenster zu `webfrontend`.
1. *Ersetzen* Sie den Code für die About-Methode:

```csharp
public async Task<IActionResult> About()
{
    ViewData["Message"] = "Hello from webfrontend";
    
    // Use HeaderPropagatingHttpClient instead of HttpClient so we can propagate
    // headers in the incoming request to any outgoing requests
    using (var client = new HeaderPropagatingHttpClient(this.Request))
    {
        // Call *mywebapi*, and display its response in the page
        var response = await client.GetAsync("http://mywebapi/api/values/1");
        ViewData["Message"] += " and " + await response.Content.ReadAsStringAsync();
    }

    return View();
}
```

Beachten Sie, wie die DNS-Dienstsuche von Kubernetes genutzt wird, um auf den Dienst als `http://mywebapi` zu verweisen. **Der Code wird in der Entwicklungsumgebung auf dieselbe Weise ausgeführt wie während der Produktion.**

Im obenstehenden Codebeispiel wird ebenfalls eine `HeaderPropagatingHttpClient`-Klasse verwendet. Diese Hilfsprogrammklasse wurde zu Ihrem Codeordner hinzugefügt, als Sie `vsce init` ausgeführt haben. `HeaderPropagatingHttpClient` wird von der bekannten `HttpClient`-Klasse abgeleitet und fügt eine Funktion hinzu, mit der bestimmte Header von einem vorhandenen HttpRequest-Objekt von ASP.NET an ein ausgehendes HttpRequestMessage-Objekt weitergeleitet werden können. Nachfolgend wird erläutert, wie mithilfe dieses Vorgangs das Entwickeln im Team produktiver gestaltet werden kann.


## <a name="debug-across-multiple-services"></a>Debuggen für mehrere Dienste
1. Zum jetzigen Zeitpunkt sollte an das `mywebapi`-Element immer noch der Debugger angefügt sein. Außerdem sollte es weiterhin ausgeführt werden. Wenn dies nicht der Fall ist, drücken Sie im `mywebapi`-Projekt F5.
1. Legen Sie in der `Get(int id)`-Methode, die `api/values/{id}`-GET-Anforderungen verarbeitet, einen Breakpoint fest.
1. Legen Sie im `webfrontend`-Projekt einen Breakpoint fest, bevor eine GET-Anforderung an `mywebapi/api/values` gesendet wird.
1. Drücken Sie im `webfrontend`-Projekt F5.
1. Rufen Sie die Web-App auf, und überprüfen Sie in beiden Diensten ausführlich den Code.
1. Die Seite „Info“ der Web-App zeigt eine Nachricht an, die von diesen beiden Diensten verkettet wird: „Hello from webfrontend and Hello from mywebapi“ (Willkommen in webfrontend und willkommen in mywebapi).


Und das war‘s schon. Sie verfügen jetzt über eine Anwendung mit mehreren Containern, in der jeder Container separat entwickelt und bereitgestellt werden kann.

> [!div class="nextstepaction"]
> [Informationen zur Entwicklung im Team](get-started-netcore-06.md)

