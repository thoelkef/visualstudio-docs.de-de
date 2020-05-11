---
title: Bereitstellen eines ASP.NET Core-Docker-Containers in Azure App Service | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie Visual Studio-Containertools zum Bereitstellen einer ASP.NET Core-Web-App in Azure App Service verwenden.
author: ghogen
manager: jillfra
ms.technology: vs-azure
ms.devlang: dotnet
ms.topic: article
ms.date: 01/27/2020
ms.author: ghogen
ms.openlocfilehash: 6c1d56f788294826853ad441313597255308bb39
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/18/2020
ms.locfileid: "77027288"
---
# <a name="deploy-an-aspnet-core-container-to-azure-app-service-using-visual-studio"></a>Bereitstellen eines ASP.NET Core-Containers in Azure App Service mit Visual Studio

Dieses Tutorial führt Sie durch die Verwendung von Visual Studio zum Veröffentlichen Ihrer ASP.NET Core-Containerwebanwendung in einer [Azure App Service-Instanz](/azure/app-service). Azure App Service ist ein geeigneter Dienst für Web-Apps mit einem Container, die in Azure gehostet werden.

Wenn Sie kein Azure-Abonnement besitzen, erstellen Sie ein [kostenloses Konto](https://azure.microsoft.com/free/dotnet/?utm_source=acr-publish-doc&utm_medium=docs&utm_campaign=docs), bevor Sie beginnen.

## <a name="prerequisites"></a>Voraussetzungen

Zum Abschließen dieses Tutorials benötigen Sie Folgendes:

::: moniker range="vs-2017"
- Installieren der neuesten Version von [Visual Studio 2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) mit der Workload „ASP.NET und Webentwicklung“
::: moniker-end
::: moniker range=">=vs-2019"
- [Visual Studio 2019](https://visualstudio.microsoft.com/downloads) mit der Workload *ASP.NET und Webentwicklung*
::: moniker-end
- Installation von [Docker Desktop](https://docs.docker.com/docker-for-windows/install/)

## <a name="create-an-aspnet-core-web-app"></a>Erstellen einer ASP.NET Core-Web-App

Die folgenden Schritte führen Sie durch die Erstellung einer einfachen ASP.NET Core-App, die in diesem Tutorial verwendet wird.

::: moniker range="vs-2017"
1. Wählen Sie im Menü von Visual Studio **Datei > Neu > Projekt** aus.
2. Wählen Sie im Abschnitt **Vorlagen** des Dialogfelds **Neues Projekt** die Option **Visual C# > Web** aus.
3. Klicken Sie auf **Neue ASP.NET Core-Webanwendung**.
4. Weisen Sie Ihrer neuen Anwendung einen Namen zu (oder übernehmen Sie den Standardnamen), und wählen Sie **OK**aus.
5. Klicken Sie auf **Webanwendung**.
6. Aktivieren Sie das Kontrollkästchen **Docker-Unterstützung aktivieren**.
7. Wählen Sie den Containertyp **Linux** aus, und klicken Sie auf **OK**. Windows-Container werden nicht für die Bereitstellung in Azure App Service unterstützt.
::: moniker-end
::: moniker range=">= vs-2019"
1. Wählen Sie im Startfenster von Visual Studio die Option **Neues Projekt erstellen**.
1. Wählen Sie **ASP.NET Core-Webanwendung** und dann **Weiter** aus.
1. Weisen Sie Ihrer neuen Anwendung einen Namen zu (oder übernehmen Sie den Standardnamen), und wählen Sie **Erstellen**aus.
1. Wählen Sie eine **Webanwendung** aus.
1. Wählen Sie im Kontrollkästchen **Für HTTPS konfigurieren** aus, ob Sie SSL unterstützen möchten.
1. Aktivieren Sie das Kontrollkästchen **Docker-Unterstützung aktivieren**.
1. Wählen Sie den Containertyp aus, und klicken Sie auf **Erstellen**. Windows-Container werden nicht für die Bereitstellung in Azure App Service unterstützt.
::: moniker-end

## <a name="deploy-the-container-to-azure"></a>Bereitstellen des Containers in Azure

1. Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf das Projekt, und wählen Sie **Veröffentlichen**.
1. Wählen Sie im Dialogfeld „Veröffentlichungsziel“ eine der Option **App Service Linux** oder **App Service** aus. Dabei handelt es sich um das Betriebssystem, das den Webserver hostet.
1. Sie können nur in App Service veröffentlichen oder sowohl in App Service als auch in Azure Container Registry (ACR) veröffentlichen. Wählen Sie **Create new App Service for containers** (Neue App Service-Instanz für Container erstellen) aus, und klicken Sie auf **Veröffentlichen**, um den Container in einer ACR-Instanz zu veröffentlichen.

   ![Screenshot: Dialogfeld „Veröffentlichen“](media/deploy-app-service/publish-app-service-linux.PNG)

   Klicken Sie auf **Neu erstellen** und dann auf **Veröffentlichen**, um nur in einer Azure App Service-Instanz ohne Azure Container Registry zu veröffentlichen.

1. Stellen Sie sicher, dass Sie mit dem Konto angemeldet sind, das Ihrem Azure-Abonnement zugeordnet ist, und wählen Sie einen eindeutigen Namen, ein Abonnement, eine Ressourcengruppe, einen Hostingplan und eine Containerregistrierung (falls zutreffend) aus, oder verwenden Sie die Standardwerte.

   ![Screenshot: Veröffentlichungseinstellungen](media/deploy-app-service/publish-app-service-linux2.png)

1. Wählen Sie **Erstellen**. Ihr Container wird in der ausgewählten Ressourcengruppe und Containerregistrierung in Azure bereitgestellt. Dieser Prozess kann ein wenig Zeit beanspruchen. Wenn er abgeschlossen ist, werden auf der Registerkarte **Veröffentlichen** Informationen zur Veröffentlichung, einschließlich der Website-URL, angezeigt.

   ![Screenshot: Registerkarte „Veröffentlichen“](media/deploy-app-service/publish-succeeded.PNG)

1. Klicken Sie auf den Websitelink, um zu überprüfen, ob Ihre App erwartungsgemäß in Azure funktioniert.

   ![Screenshot: Webanwendung](media/deploy-app-service/web-application-running.png)

1. Das Veröffentlichungsprofil wird mit allen ausgewählten Details gespeichert, z. B. die Ressourcengruppe und Containerregistrierung.

1. Sie können erneut eine Bereitstellung mit demselben Veröffentlichungsprofil durchführen, indem Sie auf **Veröffentlichen** oder im Fenster **Webveröffentlichungsaktivität** auf **Veröffentlichen** klicken oder indem Sie mit der rechten Maustaste auf das Projekt im **Projektmappen-Explorer** klicken und im Kontextmenü die Option **Veröffentlichen** auswählen.

## <a name="view-container-settings"></a>Anzeigen von Containereinstellungen

Im [Azure-Portal](https://portal.azure.com) können Sie Ihre App Service-Bereitstellung öffnen.

Sie können sich Einstellungen für Ihre App Service-Bereitstellung ansehen, indem Sie das Menü **Containereinstellungen* öffnen. Dies ist in Version 16.4 und höheren Versionen von Visual Studio 2019 möglich.

![Screenshot des Menüs „Containereinstellungen“ im Azure-Portal](media/deploy-app-service/container-settings-menu.png)

In diesem Menü können Sie sich Containerinformationen ansehen, Protokolle anzeigen oder herunterladen, oder Continuous Deployment einrichten. Weitere Informationen erhalten Sie im Artikel [Continuous Deployment mit Web-App für Container](/azure/app-service/containers/app-service-linux-ci-cd).

## <a name="clean-up-resources"></a>Bereinigen von Ressourcen

Löschen Sie die Ressourcengruppe über das [Azure-Portal](https://portal.azure.com), um alle Azure-Ressourcen für dieses Tutorial zu löschen. Klicken Sie auf **Ansicht** > **Weitere Fenster** > **Webveröffentlichungsaktivität**, und klicken Sie dann auf das Zahnradsymbol, um die Ressourcengruppe zu finden, die einer veröffentlichten Webanwendung zugeordnet ist. Daraufhin wird die Registerkarte **Veröffentlichen** geöffnet, die die Ressourcengruppe enthält.

Klicken Sie im Azure-Portal auf **Ressourcengruppen**, und wählen Sie dann die Ressourcengruppe aus, um ihre zugehörige Detailseite zu öffnen. Überprüfen Sie, ob es sich um die richtige Ressourcengruppe handelt, und klicken Sie dann auf **Ressourcengruppe entfernen**. Geben Sie anschließend den Namen der Ressourcengruppe ein, und klicken Sie auf **Löschen**.

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen finden Sie im Artikel [Einführung in Azure App Service unter Linux](/azure/app-service/containers/app-service-linux-intro).

## <a name="see-also"></a>Weitere Informationen

[Bereitstellen in Azure Container Registry](hosting-web-apps-in-docker.md)