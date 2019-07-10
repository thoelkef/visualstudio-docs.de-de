---
title: 'Tutorial: Erstellen einer App mit mehreren Containern mit Docker Compose'
description: Erfahren Sie, wie Sie mehr als einen Container verwalten und zwischen ihnen in Visual Studio für Mac kommunizieren können.
author: asb3993
ms.author: amburns
ms.date: 06/17/2019
ms.openlocfilehash: 7570788b50a83d9a74657408d4f38fbce21bd1c3
ms.sourcegitcommit: 7fbfb2a1d43ce72545096c635df2b04496b0be71
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/09/2019
ms.locfileid: "67691709"
---
# <a name="create-a-multi-container-app-with-docker-compose"></a>Erstellen einer App mit mehreren Containern mit Docker Compose

In diesem Tutorial erfahren Sie, wie Sie mehrere Container verwalten und zwischen ihnen kommunizieren können, wenn Sie Docker Compose in Visual Studio für Mac verwenden.

## <a name="prerequisites"></a>Erforderliche Komponenten

* [Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-mac)
* [Visual Studio für Mac 2019](https://visualstudio.microsoft.com/vs/mac)

## <a name="create-an-aspnet-core-web-application-and-add-docker-support"></a>Erstellen einer ASP.NET Core-Webanwendung und Hinzufügen von Docker-Unterstützung

1. Erstellen Sie eine neue Projektmappe, indem Sie zu **Datei > Neue Projektmappe** wechseln.
1. Wählen Sie unter **.NET Core > App** die Vorlage **Webanwendung** aus: ![Erstellen einer neuen ASP.NET-Anwendung](media/docker-quickstart-1.png)
1. Wählen Sie das Zielframework aus. Bei diesem Beispiel verwenden wir .NET Core 2.2: ![Festlegen des Zielframeworks](media/docker-quickstart-2.png)
1. Geben Sie die Projektdetails, z.B. den Projektnamen (_DockerDemoFrontEnd_ in diesem Beispiel) und einen Projektmappennamen (_DockerDemo_) ein. Das erstellte Projekt enthält alle Grundinformationen, die Sie für Aufbau und Betrieb einer ASP.NET Core-Website benötigen.
1. Klicken Sie im Lösungspad mit der rechten Maustaste auf das Projekt DockerDemoFrontEnd, und wählen Sie **Hinzufügen > Docker-Unterstützung hinzufügen** aus: ![Hinzufügen von Docker-Unterstützung](media/docker-quickstart-3.png)

Visual Studio für Mac fügt Ihrer Projektmappe automatisch ein neues Projekt namens **docker-compose** und dem bestehenden Projekt eine **Dockerfile** hinzu.

## <a name="create-an-aspnet-core-web-api-and-add-docker-support"></a>Erstellen einer ASP.NET Core-Web-API und Hinzufügen von Docker-Unterstützung

Als Nächstes erstellen wir ein zweites Projekt, das als unsere Back-End-API fungiert. Die Vorlage **.NET Core-API** enthält einen Controller, der es uns ermöglicht, RESTful-Anforderungen zu verarbeiten.

1. Fügen Sie der bestehenden Projektmappe ein neues Projekt hinzu, indem Sie mit der rechten Maustaste auf die Projektmappe klicken und **Hinzufügen > Neues Projekt hinzufügen** wählen.
1. Wählen Sie unter **.NET Core > App** die Vorlage **API** aus.
1. Wählen Sie das Zielframework aus. Bei diesem Beispiel verwenden wir .NET Core 2.2.
1. Geben Sie die Projektdetails ein, z.B. den Projektnamen (_DockerDemoAPI_ in diesem Beispiel).
1. Klicken Sie nach der Erstellung im Lösungspad mit der rechten Maustaste auf das Projekt DockerDemoAPI, und wählen Sie **Hinzufügen > Docker-Unterstützung hinzufügen** aus.

Die Datei **docker-compose.yml** im Projekt **docker-compose** wird automatisch so aktualisiert, dass sie neben dem bestehenden Web-App-Projekt auch das API-Projekt enthält. Wenn wir das **docker-compose**-Projekt erstellen und ausführen, wird jedes dieser Projekte in einem eigenen Docker-Container bereitgestellt.

```
version: '3.4'

services:
  dockerdemofrontend:
    image: ${DOCKER_REGISTRY-}dockerdemofrontend
    build:
      context: .
      dockerfile: DockerDemoFrontEnd/Dockerfile

  dockerdemoapi:
    image: ${DOCKER_REGISTRY-}dockerdemoapi
    build:
      context: .
      dockerfile: DockerDemoAPI/Dockerfile
```

## <a name="integrate-the-two-containers"></a>Integrieren der beiden Container

Wir haben nun zwei ASP.NET-Projekte in unserer Projektmappe, die beide mit Docker-Unterstützung konfiguriert sind. Als Nächstes müssen wir Code hinzufügen.

1. Öffnen Sie im Projekt `DockerDemoFrontEnd` die Datei *Index.cshtml.cs*, und ersetzen Sie die `OnGet`-Methode durch den folgenden Code:

   ```csharp
    public async Task OnGet()
    {
       ViewData["Message"] = "Hello from webfrontend";

       using (var client = new System.Net.Http.HttpClient())
       {
          // Call *mywebapi*, and display its response in the page
          var request = new System.Net.Http.HttpRequestMessage();
          request.RequestUri = new Uri("http://dockerdemoapi/api/values/1");
          var response = await client.SendAsync(request);
          ViewData["Message"] += " and " + await response.Content.ReadAsStringAsync();
       }
    }
   ```

1. Fügen Sie der Datei *Index.cshtml* eine Zeile hinzu, um `ViewData["Message"]` so anzuzeigen, dass die Datei wie der folgende Code aussieht:

      ```cshtml
      @page
      @model IndexModel
      @{
          ViewData["Title"] = "Home page";
      }

      <div class="text-center">
          <h1 class="display-4">Welcome</h1>
          <p>Learn about <a href="https://docs.microsoft.com/aspnet/core">building Web apps with ASP.NET Core</a>.</p>
          <p>@ViewData["Message"]</p>
      </div>
      ```

1. Fügen Sie nun im Web-API-Projekt Code zum Controller „Values“ hinzu, um die von der API zurückgegebene Nachricht für den Aufruf anzupassen, den Sie über *webfrontend* hinzugefügt haben:

      ```csharp
        // GET api/values/5
        [HttpGet("{id}")]
        public ActionResult<string> Get(int id)
        {
            return "webapi (with value " + id + ")";
        }
      ```

1. Legen Sie das Projekt `docker-compose` als Startprojekt fest, und wechseln Sie zu **Ausführen > Debuggen starten**. Wenn alles ordnungsgemäß konfiguriert ist, erhalten Sie die Meldung "Hello from webfrontend and webapi (with value 1).":

![Ausgeführte Docker-Lösung mit mehreren Containern](media/docker-multicontainer-debug.png)
