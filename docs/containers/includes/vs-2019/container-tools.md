---
title: Visual Studio-Tools für Docker mit ASP.NET Core
author: ghogen
description: Erfahren Sie mehr über die Verwendung von Visual Studio 2019-Tools und Docker für Windows.
ms.author: ghogen
ms.date: 02/01/2019
ms.prod: visual-studio-dev16
ms.technology: vs-azure
ms.topic: include
ms.openlocfilehash: 7eae92f7c65208dfeda9cd19e14eaa627e12a22a
ms.sourcegitcommit: bbff780cda82bb64862d77fe8f407f1803beb876
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/16/2019
ms.locfileid: "74142196"
---
Mit Visual Studio können Sie ASP.NET Core-Apps in Containern mühelos erstellen, debuggen, ausführen und anschließend in Azure Container Registry (ACR), Docker Hub, Azure App Service oder Ihrer eigenen Containerregistrierung veröffentlichen. In diesem Artikel wird die Veröffentlichung in ACR veranschaulicht.

## <a name="prerequisites"></a>Erforderliche Komponenten

* [Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-windows)
* [Visual Studio 2019](https://visualstudio.microsoft.com/downloads) mit installierten Workloads für **Webentwicklung**, **Azure-Tools** und/oder **plattformübergreifende .NET Core-Entwicklung**
* [.NET Core 2.2-Entwicklungstools](https://dotnet.microsoft.com/download/dotnet-core/2.2) zur Entwicklung mit .NET Core 2.2
* Zum Veröffentlichen in Azure Container Registry ist ein Azure-Abonnement erforderlich. [Registrieren Sie sich für eine kostenlose Testversion.](https://azure.microsoft.com/offers/ms-azr-0044p/)

## <a name="installation-and-setup"></a>Installation und Einrichtung

Lesen Sie vor der Installation von Docker zunächst [Docker Desktop for Windows: What to know before you install (Docker Desktop für Windows: Was vor der Installation zu beachten ist)](https://docs.docker.com/docker-for-windows/install/#what-to-know-before-you-install). Installieren Sie anschließend [Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-windows).

## <a name="add-a-project-to-a-docker-container"></a>Hinzufügen eines Projekts zu einem Docker-Container

1. Erstellen Sie ein neues Projekt über die Vorlage **ASP.NET Core-Webanwendung**.
1. Klicken Sie auf **Webanwendung**, und stellen Sie sicher, dass das Kontrollkästchen neben **Docker-Unterstützung aktivieren** aktiviert ist.

   ![Kontrollkästchen „Enable Docker Support“ (Docker-Unterstützung aktivieren)](../../media/container-tools/vs-2019/create-new-web-application.PNG)

1. Wählen Sie den gewünschten Containertyp aus (Windows oder Linux), und klicken Sie auf **Erstellen**.

## <a name="dockerfile-overview"></a>Übersicht über die Dockerfile-Datei

Eine *Dockerfile*-Datei, der wichtigste Bestandteil beim Erstellen eines endgültigen Docker-Images, wird im Projekt erstellt. Einen Überblick über die enthaltenen Befehle finden Sie in der [Dockerfile-Referenz](https://docs.docker.com/engine/reference/builder/):

```
FROM microsoft/dotnet:2.2-aspnetcore-runtime-stretch-slim AS base
WORKDIR /app
EXPOSE 80
EXPOSE 443

FROM microsoft/dotnet:2.2-sdk-stretch AS build
WORKDIR /src
COPY ["HelloDockerTools/HelloDockerTools.csproj", "HelloDockerTools/"]
RUN dotnet restore "HelloDockerTools/HelloDockerTools.csproj"
COPY . .
WORKDIR "/src/HelloDockerTools"
RUN dotnet build "HelloDockerTools.csproj" -c Release -o /app

FROM build AS publish
RUN dotnet publish "HelloDockerTools.csproj" -c Release -o /app

FROM base AS final
WORKDIR /app
COPY --from=publish /app .
ENTRYPOINT ["dotnet", "HelloDockerTools.dll"]
```

Das obige *Dockerfile* basiert auf dem Image [microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) und enthält Anweisungen zum Anpassen des Basisimages durch Erstellen Ihres Projekts und anschließendem Hinzufügen zum Container.

Wenn im neuen Projektdialogfeld das Kontrollkästchen **Configure for HTTPS** (Für HTTPS konfigurieren) aktiviert ist, werden durch die *Dockerfile*-Datei zwei Ports verfügbar gemacht. Ein Port wird für den HTTP-Datenverkehr, der andere für HTTPS verwendet. Wenn dieses Kontrollkästchen nicht aktiviert ist, wird nur der Port 80 für den HTTP-Datenverkehr verfügbar gemacht.

## <a name="debug"></a>Debug

Wählen Sie in der Symbolleiste im Dropdownmenü „Debuggen“ die Option **Docker** aus, und starten Sie das Debuggen der Anwendung. Möglicherweise wird eine Meldung mit einer Eingabeaufforderung zum Vertrauen eines Zertifikats angezeigt. Vertrauen Sie dem Zertifikat, um fortzufahren.

Die Option **Containertools** im Fenster **Ausgabe** zeigt, welche Aktionen ausgeführt werden.

Öffnen Sie die **Paket-Manager-Konsole** über das Menü **Extras**> NuGet-Paket-Manager > **Paket-Manager-Konsole**.

Das resultierende Docker-Image der App wird mit dem Tag *dev* versehen. Das Image basiert auf dem Tag *2.2-aspnetcore-runtime* des Basisimages *microsoft/dotnet*. Führen Sie im Fenster **Paket-Manager-Konsole** den Befehl `docker images` aus. Die Images auf dem Computer werden angezeigt:

```console
REPOSITORY        TAG                     IMAGE ID      CREATED         SIZE
hellodockertools  dev                     d72ce0f1dfe7  30 seconds ago  255MB
microsoft/dotnet  2.2-aspnetcore-runtime  fcc3887985bb  6 days ago      255MB
```

> [!NOTE]
> Das **dev**-Image enthält weder die Binärdateien der App noch andere Inhalte, da die **Debugkonfigurationen** die Volumebereitstellung nutzen, um die iterativen Bearbeitungs- und Debugfunktionen bereitzustellen. Verwenden Sie die **Releasekonfiguration**, um ein Produktionsimage zu erstellen, das alle Inhalte enthält.

Führen Sie in der Paket-Manager-Konsole den Befehl `docker ps` aus. Beachten Sie, dass die App mithilfe des Containers ausgeführt wird:

```console
CONTAINER ID        IMAGE                  COMMAND               CREATED             STATUS              PORTS                                           NAMES
cf5d2ef5f19a        hellodockertools:dev   "tail -f /dev/null"   2 minutes ago       Up 2 minutes        0.0.0.0:52036->80/tcp, 0.0.0.0:44342->443/tcp   priceless_cartwright
```

## <a name="containers-window"></a>Fenster „Container“

Wenn Sie Visual Studio 2019 Version 16.4 oder höher besitzen, können Sie über das Fenster **Container** die auf Ihrem Computer ausgeführten Container und verfügbare Images anzeigen.

Öffnen Sie das Fenster **Container** über das Suchfeld in der IDE (drücken Sie **STRG**+**Q**), geben Sie `container` ein, und wählen Sie **Container** aus der Liste aus.

Sie können das Fenster **Container** an einen beliebigen Ort verschieben, z. B. unter den Editor, indem Sie es bewegen und auf die Platzierungshinweise für Fenster achten.

Suchen Sie im Fenster Ihren Container, und sehen Sie sich jede Registerkarte an, um die Umgebungsvariablen, Portzuordnungen, Protokolle und das Dateisystem anzuzeigen.

Weitere Informationen finden Sie unter [Anzeigen und Diagnostizieren von Containern und Images in Visual Studio](../../view-and-diagnose-containers.md).

## <a name="publish-docker-images"></a>Veröffentlichen von Docker-Images

Sobald der Entwicklungs- und Debugzyklus der App abgeschlossen ist, können Sie ein Produktionsimage der App erstellen.

1. Wählen Sie im Dropdownmenü „Konfiguration“ die Option **Release** aus, und erstellen Sie die App.
1. Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf das Projekt, und wählen Sie **Veröffentlichen**.
1. Wählen Sie im Dialogfeld „Ziel veröffentlichen“ die Registerkarte **Container Registry**.
1. Klicken Sie auf **Neue Azure Container Registry-Instanz erstellen**, und klicken Sie dann auf **Veröffentlichen**.
1. Geben Sie die gewünschten Werte im Feld **Neue Azure-Containerregistrierung erstellen** ein.

    | Einstellung      | Empfohlener Wert  | BESCHREIBUNG                                |
    | ------------ |  ------- | -------------------------------------------------- |
    | **DNS-Präfix** | Global eindeutiger Name | Name, der Ihre Containerregistrierung eindeutig identifiziert. |
    | **Abonnement** | Auswählen Ihres Abonnements | Das zu verwendende Azure-Abonnement. |
    | **[Ressourcengruppe](/azure/azure-resource-manager/resource-group-overview)** | myResourceGroup |  Name der Ressourcengruppe, in der die Containerregistrierung erstellt werden soll. Wählen Sie **Neu** aus, um eine neue Ressourcengruppe zu erstellen.|
    | **[SKU](https://docs.microsoft.com/azure/container-registry/container-registry-skus)** | Standard | Dienstebene der Containerregistrierung  |
    | **Registrierungsstandort** | Ein Standort in Ihrer Nähe | Wählen Sie einen Standort in einer [Region](https://azure.microsoft.com/regions/) in Ihrer Nähe oder in der Nähe anderer Dienste aus, die Ihre Containerregistrierung verwenden werden. |

    ![Visual Studio-Dialogfeld zum Erstellen einer Azure-Containerregistrierung][0]

1. Klicken Sie auf **Erstellen**

   ![Screenshot mit erfolgreicher Veröffentlichung](../../media/container-tools/publish-succeeded.png)

## <a name="next-steps"></a>Nächste Schritte

Sie können jetzt den Container aus der Registrierung auf einen beliebigen Host ziehen, auf dem Docker-Images ausgeführt werden können. Beispiel: [Azure Container Instances](/azure/container-instances/container-instances-tutorial-deploy-app).

[0]:../../media/hosting-web-apps-in-docker/vs-acr-provisioning-dialog-2019.png
