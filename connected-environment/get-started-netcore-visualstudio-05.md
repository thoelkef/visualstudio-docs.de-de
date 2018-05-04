---
title: 'Erstellen einer .NET Core-Entwicklungsumgebung mit Containern unter Verwendung von Kubernetes in der Cloud mit Visual Studio, Schritt 5: Aufrufen eines weiteren Containers | Microsoft-Dokumentation'
author: ghogen
ms.author: ghogen
ms.date: 02/20/2018
ms.topic: tutorial
ms.prod: visual-studio-dev15
ms.technology: vs-azure
description: Schnelle Kubernetes-Entwicklung mit Containern und Microservices in Azure
keywords: Docker, Kubernetes, Azure, AKS, Azure Container Service, Container
manager: douge
ms.openlocfilehash: ab3934e6f7f013dd21309dc8c98461983bdfe30a
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
---
# <a name="get-started-on-connected-environment-with-net-core-and-visual-studio"></a>Erste Schritte in Connected Environment mit .NET Core und Visual Studio

Vorheriger Schritt: [Debuggen eines Containers in Kubernetes](get-started-netcore-visualstudio-04.md)

## <a name="call-another-container"></a>Aufrufen eines weiteren Containers
Im folgenden Abschnitt soll ein zweiter Dienst (`mywebapi`) erstellt werden, der von `webfrontend` aufgerufen werden soll. Jeder Dienst wird in einem separaten Container ausgeführt. Anschließend wird der Debugvorgang in beiden Containern ausgeführt.

![](media/multi-container.png)

## <a name="download-sample-code-for-mywebapi"></a>Herunterladen von Beispielcode für *mywebapi*
Laden Sie Beispielcode aus einem GitHub-Repository herunter, um Zeit zu sparen. Navigieren Sie zu https://github.com/Azure/vsce, und klicken Sie auf **Clone or Download** (Klonen oder herunterladen), um das GitHub-Repository herunterzuladen. Sie finden den Code, der für den folgenden Abschnitt benötigt wird, unter `vsce/samples/dotnetcore/getting-started/mywebapi`.

## <a name="run-mywebapi"></a>Ausführen von *mywebapi*
1. Öffnen Sie das Projekt `mywebapi` in einem *separaten Fenster von Visual Studio*.
1. Klicken Sie im Dropdownmenü für die Starteinstellungen wie zuvor im `webfrontend`-Projekt auf **Connected Environment for AKS** (Connected Environment für AKS). Wählen Sie diesmal eine bereits erstellte Entwicklungsumgebung aus, statt eine neue zu erstellen. Behalten Sie wie zuvor den Standardwert `mainline` für den Bereich bei, und klicken Sie auf **OK**. Im Ausgabefenster wird nun angezeigt, dass Visual Studio damit beginnt, diesen neuen Dienst in Ihrer Entwicklungsumgebung „aufzuwärmen“, um die Abläufe beim Debuggen zu beschleunigen.
1. Drücken Sie F5, und warten Sie, bis der Dienst erstellt und bereitgestellt wurde. Der Dienst ist bereit, wenn die Farbe der Statusleiste von Visual Studio sich in orange ändert.
1. Notieren Sie sich die Endpunkt-URL, die im Bereich **Connected Environment for AKS** (Connected Environment für AKS) im **Ausgabefenster** angezeigt wird. Diese entspricht in etwa dem Format http://localhost:\<Portnummer\>. Möglicherweise sieht es so aus, als werde der Container lokal ausgeführt, obwohl er eigentlich in der Entwicklungsumgebung in Azure ausgeführt wird.
1. Wenn `mywebapi` bereit ist, öffnen Sie die localhost-Adresse in Ihrem Browser, und fügen Sie der URL `/api/values` an, um die Standard-GET API für `ValuesController` aufzurufen. 
1. Wenn alle Schritte erfolgreich ausgeführt wurden, wird Ihnen eine Antwort des `mywebapi`-Diensts angezeigt, die folgendermaßen aussieht.

    ![](images/WebAPIResponse.png)

## <a name="make-a-request-from-webfrontend-to-mywebapi"></a>Senden einer Anforderung an *mywebapi* über *webfrontend*
Im Folgenden wird erläutert, wie Sie Code in `webfrontend` schreiben, um eine Anforderung an `mywebapi` zu senden. Wechseln Sie zu dem Fenster von Visual Studio, das das `webfrontend`-Projekt enthält. *Ersetzen* Sie in der `HomeController.cs`-Datei den Code für die About-Methode durch folgenden Code:

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

Im obenstehenden Codebeispiel wird ebenfalls eine `HeaderPropagatingHttpClient`-Klasse verwendet. Die Hilfsklasse ist in der Datei `HeaderPropagation.cs` enthalten, die zum Projekt hinzugefügt wurde, als Sie dieses für die Verwendung von Connected Environment konfiguriert haben. `HeaderPropagatingHttpClient` wird von der bekannten `HttpClient`-Klasse abgeleitet und fügt die Funktion hinzu, bestimmte Header von einem vorhandenen HttpRequest-Objekt von ASP.NET an ein ausgehendes HttpRequestMessage-Objekt weiterzuleiten. Nachfolgend wird erläutert, wie mithilfe dieses Vorgangs das Entwickeln im Team produktiver gestaltet werden kann.

## <a name="debug-across-multiple-services"></a>Debuggen für mehrere Dienste
1. Zum jetzigen Zeitpunkt sollte an das `mywebapi`-Element immer noch der Debugger angefügt sein. Außerdem sollte es weiterhin ausgeführt werden. Wenn dies nicht der Fall ist, drücken Sie im `mywebapi`-Projekt F5.
1. Legen Sie in der `Get(int id)`-Methode in der `ValuesController.cs`-Datei, die `api/values/{id}`-GET-Anforderungen verarbeitet, einen Breakpoint fest.
1. Legen Sie im `webfrontend`-Projekt, in das der oben stehende Code eingefügt wurde, einen Breakpoint fest, bevor eine GET-Anforderung an `mywebapi/api/values` gesendet wird.
1. Drücken Sie im `webfrontend`-Projekt F5. Visual Studio öffnet erneut einen Browser, der zum entsprechenden localhost-Port navigiert, und die Web-App wird angezeigt.
1. Klicken Sie im oberen Bereich der Seite auf den Link **Info**, um den Breakpoint im `webfrontend`-Projekt auszulösen. 
1. Drücken Sie F10, um den Vorgang fortzusetzen. Der Breakpoint im `mywebapi`-Projekt wird nun ausgelöst.
1. Drücken Sie F5, um den Vorgang fortzusetzen. Sie befinden sich dann wieder im Code des `webfrontend`-Projekts.
1. Wenn Sie erneut auf F5 drücken, wird die Anforderung abgeschlossen, und im Browser wird eine Seite zurückgegeben. Die Seite „Info“ der Web-App zeigt eine Nachricht an, die von diesen beiden Diensten verkettet wird: „Hello from webfrontend and Hello from mywebapi“ (Willkommen in webfrontend und willkommen in mywebapi).

Und das war‘s schon. Sie verfügen jetzt über eine Anwendung mit mehreren Containern, in der jeder Container separat entwickelt und bereitgestellt werden kann.

> [!div class="nextstepaction"]
> [Informationen zur Entwicklung im Team](get-started-netcore-visualstudio-06.md)

