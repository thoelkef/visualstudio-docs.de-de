---
title: Debuggen von Apps in einem lokalen Docker-Container | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie eine in einem lokalen Docker-Container ausgeführte App ändern, den Container über das Feature zum Bearbeiten und Aktualisieren aktualisieren und dann Haltepunkte für das Debuggen festlegen.
ms.author: ghogen
author: ghogen
manager: jillfra
ms.assetid: 480e3062-aae7-48ef-9701-e4f9ea041382
ms.topic: conceptual
ms.workload: multiple
ms.date: 07/25/2019
ms.technology: vs-azure
ms.openlocfilehash: 48754834295a552e3b189ff05ff2d1c12cd221a3
ms.sourcegitcommit: 8e123bcb21279f2770b28696995450270b4ec0e9
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/25/2019
ms.locfileid: "75400906"
---
# <a name="debug-apps-in-a-local-docker-container"></a>Debuggen von Apps in einem lokalen Docker-Container

Visual Studio bietet eine zuverlässige Möglichkeit der Entwicklung in Docker-Containern und der lokalen Überprüfung Ihrer Anwendung. Sie können Ihre Anwendungen in Linux- oder Windows-Containern ausführen und debuggen, die auf Ihrem lokalen Windows-Desktop mit installiertem Docker ausgeführt werden, und Sie müssen den Container nicht jedes Mal neu starten, wenn Sie eine Codeänderung vornehmen.

In diesem Artikel erfahren Sie, wie Sie das Feature zum Bearbeiten und Aktualisieren nutzen, um eine App in einem lokalen Docker-Container zu starten, die erforderlichen Änderungen vorzunehmen und den Browser dann zu aktualisieren, um die Änderungen anzuzeigen. Außerdem erfahren Sie in diesem Artikel, wie Sie Haltepunkte für das Debuggen für die sich in Containern befindenden Apps festlegen. Zu den unterstützten Projekttypen gehören .NET Framework- und .NET Core Web- sowie Konsolen-Apps. In diesem Artikel verwenden wir ASP.NET Core-Web-Apps und .NET Framework-Konsolen-Apps.

Wenn Sie bereits über ein Projekt eines unterstützten Typs verfügen, kann Visual Studio eine Dockerfile erstellen und Ihr Projekt für die Ausführung in einem Container konfigurieren. Weitere Informationen finden Sie unter [Containertools in Visual Studio](overview.md).

## <a name="prerequisites"></a>Voraussetzungen

Zum Debuggen von Apps in einem lokalen Docker-Container müssen die folgenden Tools installiert werden:

::: moniker range="vs-2017"

* [Visual Studio 2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) mit installierter Workload für Webentwicklung

::: moniker-end

::: moniker range="vs-2019"

* [Visual Studio 2019](https://visualstudio.microsoft.com/downloads) mit installierter Workload für Webentwicklung

::: moniker-end

Sie benötigen einen lokalen Docker-Client, um Docker-Container lokal ausführen zu können. Sie können die [Docker-Toolbox](https://www.docker.com/products/docker-toolbox) verwenden, für die Hyper-V deaktiviert werden muss. Sie können auch [Docker für Windows](https://www.docker.com/get-docker) verwenden. Diese Anwendung verwendet Hyper-V und erfordert Windows 10.

Docker-Container sind für .NET Framework- und .NET Core-Projekte verfügbar. Nachfolgend sehen Sie zwei Beispiele. Zunächst sehen wir uns eine .NET Core-Web-App an. Dann sehen wir uns eine .NET Framework-Konsolen-App an.

## <a name="create-a-web-app"></a>Erstellen einer Web-App

Wenn Sie über ein Projekt verfügen und die Docker-Unterstützung wie in der [Übersicht](overview.md) beschrieben hinzugefügt haben, überspringen Sie diesen Abschnitt.

::: moniker range="vs-2017"
[!INCLUDE [create-aspnet5-app](../azure/includes/create-aspnet5-app.md)]
::: moniker-end
::: moniker range=">= vs-2019"
[!INCLUDE [create-aspnet5-app-2019](../azure/includes/vs-2019/create-aspnet5-app-2019.md)]
::: moniker-end

### <a name="edit-your-code-and-refresh"></a>Bearbeiten und Aktualisieren von Code

Sie können die Anwendung in einem Container starten, um Änderungen schnell zu durchlaufen. Nehmen Sie dann weiterhin Änderungen vor, und betrachten Sie sie wie IIS Express.

1. Stellen Sie sicher, dass Docker so eingerichtet ist, dass der von Ihnen verwendete Containertyp (Linux oder Windows) verwendet wird. Klicken Sie mit der rechten Maustaste auf das Docker-Symbol auf der Taskleiste und wählen Sie die Option zum **Wechseln zu Linux-Containern** oder **Wechseln zu Windows-Containern** aus.

1. Legen Sie die **Lösungskonfiguration** auf **Debuggen** fest. Drücken Sie dann **STRG**+**F5**, um Ihr Docker-Image zu erstellen und lokal auszuführen.

    Wenn das Containerimage erstellt wurde und in einem Docker-Container ausgeführt wird, startet Visual Studio die Web-App in Ihrem Standardbrowser.

1. Wechseln Sie zur *Index*-Seite. Wir nehmen auf dieser Seite Änderungen vor.
1. Kehren Sie zu Visual Studio zurück, und öffnen Sie *Index.cshtml*.
1. Fügen Sie den folgenden HTML-Inhalt am Ende der Datei hinzu, und speichern Sie dann die Änderungen.

    ```html
    <h1>Hello from a Docker container!</h1>
    ```

1. Sobald der .NET-Build fertig gestellt ist, sehen Sie im Ausgabefenster diese Zeilen. Kehren Sie zu Ihrem Browser zurück, und aktualisieren Sie die Seite:

   ```output
   Now listening on: http://*:80
   Application started. Press Ctrl+C to shut down.
   ```

Ihre Änderungen wurden übernommen!

### <a name="debug-with-breakpoints"></a>Debuggen mit Haltepunkten

Häufig ist für Änderungen eine weitere Überprüfung erforderlich. Sie können die Debugfunktionen von Visual Studio für diese Aufgabe verwenden.

1. Öffnen Sie *Index.cshtml.cs* in Visual Studio.
2. Ersetzen Sie den Inhalt der `OnGet`-Methode durch folgenden Code:

   ```csharp
       ViewData["Message"] = "Your application description page from within a container";
   ```

3. Legen Sie links neben die Codezeile einen Haltepunkt fest.
4. Drücken Sie F5, um das Debuggen zu starten und den Haltepunkt zu erreichen.
5. Wechseln Sie zu Visual Studio, um den Haltepunkt anzuzeigen. Überprüfen Sie die Werte.

   ![Haltepunkt](media/edit-and-refresh/breakpoint.png)

## <a name="create-a-net-framework-console-app"></a>Erstellen einer .NET Framework-Konsolen-App

Wenn Sie Projekte der .NET Framework-Konsolen-App verwenden, wird die Option, Docker-Unterstützung ohne Orchestrierung hinzuzufügen, nicht unterstützt. Sie können weiterhin das folgende Verfahren verwenden, auch wenn Sie nur ein einzelnes Docker-Projekt verwenden.

1. Erstellen Sie ein neues .NET Framework-Konsolen-App-Projekt.
1. Klicken Sie im Projektmappen-Explorer mit der rechten Maustaste auf den Projektknoten, und wählen Sie dann **Hinzufügen** > **Unterstützung für Containerorchestrierung** aus.  Klicken Sie im angezeigten Dialogfeld auf **Docker Compose**. Dem Projekt wird eine Dockerfile-Datei hinzugefügt, und es wird ein Docker Compose-Projekt mit zugeordneten Unterstützungsdateien hinzugefügt.

### <a name="debug-with-breakpoints"></a>Debuggen mit Haltepunkten

1. Öffnen Sie *Program.cs* im Projektmappen-Explorer.
2. Ersetzen Sie den Inhalt der `Main`-Methode durch folgenden Code:

   ```csharp
       System.Console.WriteLine("Hello, world!");
   ```

3. Legen Sie links neben die Codezeile einen Haltepunkt fest.
4. Drücken Sie F5, um das Debuggen zu starten und den Haltepunkt zu erreichen.
5. Kehren Sie zu Visual Studio zurück, um den Haltepunkt anzuzeigen und die Werte zu überprüfen.

   ![Haltepunkt](media/edit-and-refresh/breakpoint-console.png)

## <a name="container-reuse"></a>Wiederverwendung von Containern

Während des Entwicklungszeitraums erstellt Visual Studio nur Ihre Containerimages und den Container selbst neu, wenn Sie die Dockerfile-Datei ändern. Wenn Sie die Dockerfile-Datei nicht ändern, verwendet Visual Studio den Container von einem früheren Testlauf wieder.

Wenn Sie den Container manuell geändert haben und ihn mit einem sauberen Containerimage neu starten möchten, verwenden Sie den Befehl **Erstellen** > **Bereinigen** in Visual Studio, und führen Sie dann wie gewohnt den Erstellungsprozess aus.

## <a name="troubleshoot"></a>Problembehandlung

Informationen zur [Problembehandlung bei der Docker-Entwicklung in Visual Studio](troubleshooting-docker-errors.md).

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen finden Sie unter [Wie Visual Studio Containeranwendungen erstellt](container-build.md).

## <a name="more-about-docker-with-visual-studio-windows-and-azure"></a>Weitere Informationen zu Docker mit Visual Studio, Windows und Azure

* Nähere Informationen zur [Containerentwicklung mit Visual Studio](/visualstudio/containers).
* Informationen zum Erstellen und Bereitstellen eines Docker-Containers finden Sie unter [Docker-Integration für Azure Pipelines](https://aka.ms/dockertoolsforvsts).
* Einen Index von Windows Server- und Nano Server-Artikeln finden Sie unter [Informationen zu Windows-Containern](https://aka.ms/containers).
* Erfahren Sie mehr über den [Azure Kubernetes Service](https://azure.microsoft.com/services/kubernetes-service/) und überprüfen Sie die [Dokumentation zum Azure Kubernetes Service](/azure/aks).
