---
title: Veröffentlichen in Azure durch Importieren der veröffentlichungseinstellungen
ms.description: Create and import a publishing profile to deploy an application from Visual Studio to Azure App Service
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
ms.openlocfilehash: 2b4b0e4ea963f20199267f32a8c87440c8cc350b
ms.sourcegitcommit: c57ae28181ffe14a30731736661bf59c3eff1211
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/11/2018
ms.locfileid: "38808320"
---
# <a name="publish-an-application-to-azure-app-service-by-importing-publish-settings-in-visual-studio"></a>Veröffentlichen einer Anwendung in Azure App Service Importieren von veröffentlichungseinstellungen in Visual Studio

Sie können die **veröffentlichen** Tool zum Importieren von veröffentlichungseinstellungen aus, und klicken Sie dann Ihre app bereitstellen. In diesem Artikel verwenden wir die veröffentlichungseinstellungen für Azure App Service, jedoch können Sie ähnliche Schritte zum Importieren der veröffentlichungseinstellungen von [IIS](../deployment/tutorial-import-publish-settings-iis.md). Verwenden Sie in einigen Szenarien, der ein veröffentlichen, die schneller als manuell konfigurierte Bereitstellung für den Dienst bei jeder Installation von Visual Studio Profils werden kann.

Diese Schritte gelten für ASP.NET, ASP.NET Core und .NET Core-apps in Visual Studio. Sie können auch Importieren der veröffentlichungseinstellungen für [Python](../python/publishing-python-web-applications-to-azure-from-visual-studio.md) apps. Die Schritte entsprechen den Visual Studio 2017 Version 15.6.

In diesem Tutorial werden Sie Folgendes durchführen:

> [!div class="checklist"]
> * Generieren Sie eine Datei mit veröffentlichungseinstellungen von Azure App Service
> * In Visual Studio die Datei mit veröffentlichungseinstellungen importieren
> * Bereitstellen der app in Azure App Service

Eine Datei mit veröffentlichungseinstellungen (*\*.publishsettings*) unterscheidet sich ein Veröffentlichungsprofil (*\*pubxml*) in Visual Studio erstellt. Eine Datei mit veröffentlichungseinstellungen wird von Azure App Service erstellt, und klicken Sie dann in Visual Studio importiert werden können.

> [!NOTE]
> Wenn Sie lediglich ein Visual Studio mit dem Veröffentlichungsprofil zu kopieren (*\*pubxml* Datei) von einer Installation von Visual Studio in eine andere finden Sie das Veröffentlichungsprofil,  *\<Profilename\>pubxml*in die  *\\< Projectname\>\Properties\PublishProfiles* Ordner für verwaltete Projekttypen zur Verfügung. Für Websites, suchen Sie unter den *\App_Data* Ordner. Die Veröffentlichungsprofile handelt es sich um MSBuild XML-Dateien.

## <a name="prerequisites"></a>Erforderliche Komponenten

* Sie müssen Visual Studio 2017 installiert haben und die **ASP.NET** und. **NET Framework** entwicklungsworkload. Für eine .NET Core-app müssen Sie auch die. **NET Core** arbeitsauslastung.

    Wenn Sie Visual Studio noch nicht installiert haben, können Sie es auf der Seite [Visual Studio-Downloads](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) kostenlos herunterladen.

* Erstellen einer Azure App Service. Ausführliche Anweisungen finden Sie unter [bereitstellen eine ASP.NET Core-Web-app in Azure mithilfe von Visual Studio](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs).

## <a name="create-a-new-aspnet-project-in-visual-studio"></a>Erstellen eines neuen ASP.NET-Projekts in Visual Studio

1. Wählen Sie auf dem Computer mit Visual Studio, **Datei** > **neues Projekt**.

1. Klicken Sie unter **Visual C#-** oder **Visual Basic**, wählen Sie **Web**, und wählen Sie dann im mittleren Bereich entweder **ASP.NET-Webanwendung ((.NET Framework)** oder (nur c#) **ASP.NET Core-Webanwendung**, und klicken Sie dann auf **OK**.

    Wenn die angegebene-Projektvorlagen nicht angezeigt wird, klicken Sie auf die **Visual Studio-Installer öffnen** Link im linken Bereich des der **neues Projekt** Dialogfeld. Der Visual Studio-Installer wird gestartet. Siehe die Voraussetzungen in diesem Artikel sind die erforderlichen Visual Studio-arbeitsauslastungen, die installiert werden muss.

1. Wählen Sie entweder **MVC** ((.NET Framework) oder **Webanwendung (Model-View-Controller)** (für .NET Core), und stellen Sie sicher, dass **keine Authentifizierung** ausgewählt ist, und klicken Sie dann auf **OK**.

1. Geben Sie einen Namen wie **MyWebApp** , und klicken Sie auf **OK**.

    Visual Studio erstellt daraufhin das Projekt.

1. Wählen Sie **erstellen** > **Projektmappe** zum Erstellen des Projekts.

## <a name="create-the-publish-settings-file-in-azure-app-service"></a>Erstellen Sie die Datei mit veröffentlichungseinstellungen in Azure App Service

1. Öffnen Sie im Azure-Portal Azure App Service aus.

1. Klicken Sie auf **Veröffentlichungsprofil abrufen** und speichern Sie das Profil lokal.

    ![Abrufen des Veröffentlichungsprofils](../deployment/media/tutorial-azure-app-service-get-publish-profile.png)

    Eine Datei mit einem *.publishsettings* Dateierweiterung generiert wurde, in dem Speicherort, in dem Sie gespeichert. Der folgende Code zeigt ein teilbeispiel des der Datei (in einem besser lesbaren Formatierung).

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
    Die oben angegebene *.PUBLISHSETTINGS-Datei enthält in der Regel zwei Veröffentlichungsprofile, die Sie in Visual Studio, eine Bereitstellung mithilfe von Web Deploy und eine zum Bereitstellen über FTP verwenden können. Der vorhergehende Code zeigt das Profil Web Deploy. Beide Profile werden später importiert werden, wenn Sie das Profil importieren.

## <a name="import-the-publish-settings-in-visual-studio-and-deploy"></a>Die Einstellungen für die Veröffentlichung in Visual Studio importieren und bereitstellen

[!INCLUDE [import publish settings](../deployment/includes/import-publish-settings-vs.md)]

## <a name="next-steps"></a>Nächste Schritte

In diesem Tutorial haben Sie erstellt eine Datei mit veröffentlichungseinstellungen importiert es in Visual Studio und eine ASP.NET-App in Azure App Service bereitgestellt. Sie sollten einen Überblick über Veröffentlichungsoptionen in Visual Studio.

> [!div class="nextstepaction"]
> [Erster Einblick in die Bereitstellung](../deployment/deploying-applications-services-and-components.md)
