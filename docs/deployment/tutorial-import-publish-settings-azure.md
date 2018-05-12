---
title: Veröffentlichen in Azure durch Importieren von veröffentlichungseinstellungen
ms.custom: Create and import a publishing profile to deploy an application from Visual Studio to Azure App Service
ms.date: 05/07/2018
ms.technology: vs-ide-deployment
ms.topic: tutorial
helpviewer_keywords:
- deployment, publish settings
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3e844e2177d01d5b308472eae5661b25798f0838
ms.sourcegitcommit: 046a9adc5fa6d6d05157204f5fd1a291d89760b7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/11/2018
---
# <a name="publish-an-application-to-azure-app-service-by-importing-publish-settings-in-visual-studio"></a>Veröffentlichen von einer Anwendung in Azure App Service durch Importieren von veröffentlichungseinstellungen in Visual Studio

Können Sie die **veröffentlichen** Tool zum Importieren von veröffentlichungseinstellungen, und klicken Sie dann die app bereitstellen. In diesem Artikel verwenden wir veröffentlichungseinstellungen für Azure App Service, jedoch können Sie ähnliche Schritte zum Importieren von veröffentlichungseinstellungen aus [IIS](../deployment/tutorial-import-publish-settings-iis.md). In einigen Szenarien ist die Verwendung von veröffentlichen, Einstellungsprofil, das schneller sein kann als das manuelle Konfigurieren der Bereitstellung an den Dienst für jede Installation von Visual Studio, aus.

Diese Schritte gelten für ASP.NET, ASP.NET Core und .NET Core-apps in Visual Studio. Sie können auch importieren veröffentlichungseinstellungen für [Python](/visualstudio/python/publishing-python-web-applications-to-azure-from-visual-studio) apps. Die Schritte entsprechen den Visual Studio 2017 Version 15,6.

In diesem Tutorial werden Sie Folgendes durchführen:

> [!div class="checklist"]
> * Generieren Sie eine Datei mit veröffentlichungseinstellungen aus Azure App Service
> * Importieren Sie die Datei mit veröffentlichungseinstellungen in Visual Studio
> * Bereitstellen der app in Azure App Service

Eine Datei mit veröffentlichungseinstellungen (*\*publishsettings*) unterscheidet sich ein Veröffentlichungsprofil angeben (*\*pubxml*) in Visual Studio erstellt wurden. Eine Datei mit veröffentlichungseinstellungen von Azure App Service erstellt wird, und klicken Sie dann in Visual Studio importiert werden können.

> [!NOTE]
> Wenn Sie nur eine Visual Studio Veröffentlichungsprofil kopieren müssen (*\*pubxml* Datei) aus einer Installation von Visual Studio in einen anderen finden Sie das Veröffentlichungsprofil  *\<Profilename\>pubxml*in der  *\\< Projectname\>\Properties\PublishProfiles* Ordner für verwaltete Projekttypen zur Verfügung. Für Websites, suchen Sie unter der *\App_Data* Ordner. Die publishing Profile handelt es sich um MSBuild XML-Dateien.

## <a name="prerequisites"></a>Erforderliche Komponenten

* Sie müssen Visual Studio installiert haben und die **ASP.NET** und **.NET Framework** Entwicklungsaufwand. Für eine .NET Core-app müssen Sie auch die **.NET Core** arbeitsauslastung.

    Falls Sie Visual Studio noch nicht installiert haben, können Sie es [hier](http://www.visualstudio.com) gratis herunterladen.

* Erstellen Sie ein Azure-App-Dienst. Ausführliche Anweisungen finden Sie unter [eine ASP.NET Core Web-app in Azure mithilfe von Visual Studio bereitstellen](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs). 

## <a name="create-a-new-aspnet-project-in-visual-studio"></a>Erstellen eines neuen ASP.NET-Projekts in Visual Studio

1. Wählen Sie auf dem Computer mit Visual Studio, **Datei > Neues Projekt**.

1. Klicken Sie unter **Visual C#-** oder **Visual Basic**, wählen Sie **Web**, und wählen Sie dann im mittleren Bereich entweder **ASP.NET-Webanwendung ((.NET Framework)** oder (nur c#) **ASP.NET-Webanwendung für Core**, und klicken Sie dann auf **OK**.

    Wenn die angegebene-Projektvorlagen nicht angezeigt wird, klicken Sie auf die **Installer für Visual Studio öffnen** Link im linken Bereich des der **neues Projekt** (Dialogfeld). Der Visual Studio-Installer wird gestartet. Siehe die Voraussetzungen in diesem Artikel, um die erforderlichen Visual Studio-arbeitsauslastungen, identifiziert werden, die Sie installieren müssen.

1. Wählen Sie entweder **MVC** ((.NET Framework) oder **Webanwendung (Model-View-Controller)** (für .NET Core), und stellen Sie sicher, dass **keine Authentifizierung** ausgewählt ist, und klicken Sie dann auf **OK**.

1. Geben Sie einen Namen wie **MyWebApp** , und klicken Sie auf **OK**.

    Visual Studio erstellt daraufhin das Projekt.

1. Wählen Sie **erstellen > Projektmappe** zum Erstellen des Projekts.

## <a name="create-the-publish-settings-file-in-azure-app-service"></a>Erstellen Sie die Datei mit veröffentlichungseinstellungen in Azure App Service

1. Öffnen Sie im Azure-Portal Azure App Service ein.

1. Klicken Sie auf **Get Veröffentlichungsprofil** und speichern Sie das Profil lokal.

    ![Abrufen des Veröffentlichungsprofils](../deployment/media/tutorial-azure-app-service-get-publish-profile.png)

    Eine Datei mit einem *publishsettings* -Erweiterung generiert wurde, an dem Speicherort, in dem Sie gespeichert. Der folgende Code zeigt eine partielle Beispiel der Datei (in einem besser lesbaren Formatierung).

    ```xml
    <publishData>
      <publishProfile
        profileName="DeployASPDotNetCore - Web Deploy"
        publishMethod="MSDeploy"
        publishUrl="deployaspdotnetcore.scm.azurewebsites.net:443"
        msdeploySite="DeployASPDotNetCore"
        userName="$DeployASPDotNetCore"
        userPWD="abcdefghijklmnopqrstuzwxyz"
        destinationAppUrl="http://deployaspdotnetcore20180508031824.azurewebsites.net"
        SQLServerDBConnectionString=""
        mySQLDBConnectionString=""
        hostingProviderForumLink=""
        controlPanelLink="http://windows.azure.com"
        webSystem="WebSites">
        <databases />
      </publishProfile>
    </publishData>
    ```
    Die oben angegebene *.PUBLISHSETTINGS-Datei enthält in der Regel zwei Veröffentlichungsprofile, mit denen Sie in Visual Studio mithilfe von Web Deploy und eine Bereitstellung mithilfe von FTP bereitstellen können. Der vorhergehende Code zeigt das Web Deploy-Profil. Beide Profile werden später erneut importiert werden, wenn Sie das Profil importieren.

## <a name="import-the-publish-settings-in-visual-studio-and-deploy"></a>Die Einstellungen für die Veröffentlichung in Visual Studio importieren und bereitstellen

1. Klicken Sie auf dem Computer, die dort stehen Ihnen die ASP.NET-Projekt in Visual Studio öffnen, mit der rechten Maustaste des Projekts im Projektmappen-Explorer, und wählen Sie **veröffentlichen**.

1. Wenn Sie Veröffentlichungsprofile zuvor konfiguriert haben die **veröffentlichen** Bereich wird angezeigt. Klicken Sie auf **neues Profil erstellen**.

1. In der **Veröffentlichungsziel auswählen** (Dialogfeld), klicken Sie auf **Profil importieren**.

    ![Wählen Sie veröffentlichen](../deployment/media/tutorial-publish-tool-import-profile.png)

1. Navigieren Sie zum Speicherort der Datei mit den veröffentlichungseinstellungen, den Sie im vorherigen Abschnitt erstellt haben.

1. In der **veröffentlichen-Einstellungsdatei importieren** (Dialogfeld), wählen Sie das Profil, das Sie im vorherigen Abschnitt erstellt haben, und klicken Sie auf **öffnen**.

1. Wählen Sie eines der beiden importierten Profile aus, und klicken Sie auf **veröffentlichen**.

    Visual Studio startet den Bereitstellungsprozess, und das Ausgabefenster zeigt Status und die Ergebnisse.

## <a name="next-steps"></a>Nächste Schritte

In diesem Lernprogramm erstellt eine Datei mit veröffentlichungseinstellungen, Visual Studio importiert und eine ASP.NET-Anwendung in Azure App Service bereitgestellt.

> [!div class="nextstepaction"]
> [Erster Einblick in die Bereitstellung](../deployment/deploying-applications-services-and-components.md)
