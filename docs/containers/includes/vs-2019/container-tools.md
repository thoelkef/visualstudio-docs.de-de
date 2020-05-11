---
title: Visual Studio-Tools für Docker mit ASP.NET
author: ghogen
description: Erfahren Sie mehr über die Verwendung von Visual Studio 2019-Tools und Docker für Windows.
ms.author: ghogen
ms.date: 02/01/2019
ms.prod: visual-studio-dev16
ms.technology: vs-azure
ms.topic: include
ms.openlocfilehash: d6d519483b350f2c1086c76bc17522b71a435fe9
ms.sourcegitcommit: cc58ca7ceae783b972ca25af69f17c9f92a29fc2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/15/2020
ms.locfileid: "81389957"
---
Mit Visual Studio können Sie .NET-, ASP.NET- und ASP.NET Core-Apps in Containern mühelos erstellen, debuggen, ausführen und anschließend in Azure Container Registry (ACR), Docker Hub, Azure App Service oder Ihrer eigenen Containerregistrierung veröffentlichen. In diesem Artikel veröffentlichen wir eine ASP.NET Core-App in ACR.

## <a name="prerequisites"></a>Voraussetzungen

* [Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-windows)
* [Visual Studio 2019](https://visualstudio.microsoft.com/downloads) mit installierten Workloads für **Webentwicklung**, **Azure-Tools** und/oder **plattformübergreifende .NET Core-Entwicklung**
* [.NET Core-Entwicklungstools](https://dotnet.microsoft.com/download/dotnet-core/) für die Entwicklung mit .NET Core
* Zum Veröffentlichen in Azure Container Registry ist ein Azure-Abonnement erforderlich. [Registrieren Sie sich für eine kostenlose Testversion.](https://azure.microsoft.com/free/dotnet/)

## <a name="installation-and-setup"></a>Installation und Einrichtung

Lesen Sie vor der Installation von Docker zunächst [Docker Desktop for Windows: What to know before you install (Docker Desktop für Windows: Was vor der Installation zu beachten ist)](https://docs.docker.com/docker-for-windows/install/#what-to-know-before-you-install). Installieren Sie anschließend [Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-windows).

## <a name="add-a-project-to-a-docker-container"></a>Hinzufügen eines Projekts zu einem Docker-Container

1. Erstellen Sie mithilfe der Vorlage **ASP.NET Core-Webanwendung** ein neues Projekt. Wenn Sie statt .NET Core lieber .NET Framework verwenden möchten, wählen Sie **ASP.NET Web Application (.NET Framework)** (ASP.NET-Webanwendung [.NET Framework]) aus.
1. Klicken Sie auf **Webanwendung**, und stellen Sie sicher, dass das Kontrollkästchen neben **Docker-Unterstützung aktivieren** aktiviert ist.

   ![Kontrollkästchen „Enable Docker Support“ (Docker-Unterstützung aktivieren)](../../media/container-tools/vs-2019/create-new-web-application.PNG)

   Im Screenshot wird .NET Core verwendet. Mit .NET Framework sieht der Bildschirm etwas anders aus.

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

Das obige *Dockerfile* basiert auf dem Image [microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) und enthält Anweisungen zum Anpassen des Basisimages durch Erstellen Ihres Projekts und anschließendem Hinzufügen zum Container. Wenn Sie .NET Framework verwenden, unterscheidet sich das Basisimage.

Wenn im neuen Projektdialogfeld das Kontrollkästchen **Configure for HTTPS** (Für HTTPS konfigurieren) aktiviert ist, werden durch die *Dockerfile*-Datei zwei Ports verfügbar gemacht. Ein Port wird für den HTTP-Datenverkehr, der andere für HTTPS verwendet. Wenn dieses Kontrollkästchen nicht aktiviert ist, wird nur der Port 80 für den HTTP-Datenverkehr verfügbar gemacht.

## <a name="debug"></a>Debug

Wählen Sie in der Symbolleiste im Dropdownmenü „Debuggen“ die Option **Docker** aus, und starten Sie das Debuggen der Anwendung. Möglicherweise wird eine Meldung mit einer Eingabeaufforderung zum Vertrauen eines Zertifikats angezeigt. Vertrauen Sie dem Zertifikat, um fortzufahren.

Die Option **Containertools** im Fenster **Ausgabe** zeigt, welche Aktionen ausgeführt werden. Beim ersten Mal kann der Download des Basisimages einige Zeit dauern. Bei nachfolgenden Ausführungen geht es aber deutlich schneller.

>[!NOTE]
> Wenn Sie die Ports zum Debuggen ändern müssen, können Sie diese Änderungen in der Datei *launchSettings.json* vornehmen. Weitere Informationen dazu finden Sie unter [Containerstarteinstellungen](../../container-launch-settings.md).

## <a name="containers-window"></a>Fenster „Container“

Wenn Sie Visual Studio 2019 Version 16.4 oder höher besitzen, können Sie über das Fenster **Container** die auf Ihrem Computer ausgeführten Container und verfügbare Images anzeigen.

Öffnen Sie das Fenster **Container** über das Suchfeld in der IDE (drücken Sie **STRG**+**Q**), geben Sie `container` ein, und wählen Sie **Container** aus der Liste aus.

Sie können das Fenster **Container** an einen beliebigen Ort verschieben, z. B. unter den Editor, indem Sie es bewegen und auf die Platzierungshinweise für Fenster achten.

Suchen Sie im Fenster Ihren Container, und sehen Sie sich jede Registerkarte an, um die Umgebungsvariablen, Portzuordnungen, Protokolle und das Dateisystem anzuzeigen.

![Screenshot des Fensters „Container“](../../media/overview/vs-2019/container-tools-window.png)

Weitere Informationen finden Sie unter [Anzeigen und Diagnostizieren von Containern und Images in Visual Studio](../../view-and-diagnose-containers.md).

## <a name="publish-docker-images"></a>Veröffentlichen von Docker-Images

Sobald der Entwicklungs- und Debugzyklus der App abgeschlossen ist, können Sie ein Produktionsimage der App erstellen.

1. Wählen Sie im Dropdownmenü „Konfiguration“ die Option **Release** aus, und erstellen Sie die App.
1. Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf das Projekt, und wählen Sie **Veröffentlichen**.
1. Wählen Sie im Dialogfeld „Ziel veröffentlichen“ die Registerkarte **Container Registry**.
1. Klicken Sie auf **Neue Azure Container Registry-Instanz erstellen**, und klicken Sie dann auf **Veröffentlichen**.
1. Geben Sie die gewünschten Werte im Feld **Neue Azure-Containerregistrierung erstellen** ein.

    | Einstellung      | Empfohlener Wert  | Beschreibung                                |
    | ------------ |  ------- | -------------------------------------------------- |
    | **DNS-Präfix** | Global eindeutiger Name | Name, der Ihre Containerregistrierung eindeutig identifiziert. |
    | **Abonnement** | Auswählen Ihres Abonnements | Das zu verwendende Azure-Abonnement. |
    | **[Ressourcengruppe](/azure/azure-resource-manager/resource-group-overview)** | myResourceGroup |  Name der Ressourcengruppe, in der die Containerregistrierung erstellt werden soll. Wählen Sie **Neu** aus, um eine neue Ressourcengruppe zu erstellen.|
    | **[SKU](/azure/container-registry/container-registry-skus)** | Standard | Dienstebene der Containerregistrierung  |
    | **Registrierungsstandort** | Ein Standort in Ihrer Nähe | Wählen Sie einen Standort in einer [Region](https://azure.microsoft.com/regions/) in Ihrer Nähe oder in der Nähe anderer Dienste aus, die Ihre Containerregistrierung verwenden werden. |

    ![Visual Studio-Dialogfeld zum Erstellen einer Azure-Containerregistrierung][0]

1. Klicken Sie auf **Erstellen**

   ![Screenshot mit erfolgreicher Veröffentlichung](../../media/container-tools/publish-succeeded.png)

## <a name="next-steps"></a>Nächste Schritte

Sie können jetzt den Container aus der Registrierung auf einen beliebigen Host ziehen, auf dem Docker-Images ausgeführt werden können. Beispiel: [Azure Container Instances](/azure/container-instances/container-instances-tutorial-deploy-app).

[0]:../../media/hosting-web-apps-in-docker/vs-acr-provisioning-dialog-2019.png
