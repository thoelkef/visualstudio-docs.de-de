---
title: Veröffentlichen in IIS durch das Importieren der veröffentlichungseinstellungen
ms.custom: Create and import a publishing profile to deploy an application from Visual Studio to IIS
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
ms.openlocfilehash: e6df935578955d3c72b6f4fa61efdf614229bca0
ms.sourcegitcommit: c57ae28181ffe14a30731736661bf59c3eff1211
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/11/2018
ms.locfileid: "38808464"
---
# <a name="publish-an-application-to-iis-by-importing-publish-settings-in-visual-studio"></a>Veröffentlichen einer Anwendung in IIS Importieren von veröffentlichungseinstellungen in Visual Studio

Sie können die **veröffentlichen** Tool zum Importieren von veröffentlichungseinstellungen aus, und klicken Sie dann Ihre app bereitstellen. In diesem Artikel verwenden wir die veröffentlichungseinstellungen für IIS, jedoch können Sie ähnliche Schritte zum Importieren der veröffentlichungseinstellungen für [Azure App Service](../deployment/tutorial-import-publish-settings-azure.md). Verwenden Sie in einigen Szenarien, der ein veröffentlichen, die schneller als das manuelle Konfigurieren der Bereitstellung in IIS für jede Installation von Visual Studio Profils werden kann.

Diese Schritte gelten für ASP.NET, ASP.NET Core und .NET Core-apps in Visual Studio. Die Schritte entsprechen den Visual Studio 2017 Version 15.6.

In diesem Tutorial werden Sie Folgendes durchführen:

> [!div class="checklist"]
> * Konfigurieren Sie IIS so, dass Sie eine Datei mit veröffentlichungseinstellungen generieren können
> * Erstellen Sie eine Datei mit veröffentlichungseinstellungen
> * In Visual Studio die Datei mit veröffentlichungseinstellungen importieren
> * Bereitstellen der app in IIS

Eine Datei mit veröffentlichungseinstellungen (*\*.publishsettings*) unterscheidet sich ein Veröffentlichungsprofil (*\*pubxml*) in Visual Studio erstellt. Eine Datei mit veröffentlichungseinstellungen wird erstellt, indem Sie IIS oder Azure App Service oder manuell erstellt werden, und klicken Sie dann in Visual Studio importiert werden können.

> [!NOTE]
> Wenn Sie lediglich ein Visual Studio mit dem Veröffentlichungsprofil zu kopieren (\*pubxml-Datei) von einer Installation von Visual Studio in eine andere finden Sie das Veröffentlichungsprofil,  *\<Profilename\>pubxml*, in der  *\\< Projectname\>\Properties\PublishProfiles* Ordner für verwaltete Projekttypen zur Verfügung. Für Websites, suchen Sie unter den *\App_Data* Ordner. Die Veröffentlichungsprofile handelt es sich um MSBuild XML-Dateien.

## <a name="prerequisites"></a>Erforderliche Komponenten

* Sie müssen Visual Studio 2017 installiert haben und die **ASP.NET** und **.NET Framework** entwicklungsworkload. Für eine .NET Core-app müssen Sie auch die **.NET Core** arbeitsauslastung.

    Wenn Sie Visual Studio noch nicht installiert haben, können Sie es auf der Seite [Visual Studio-Downloads](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) kostenlos herunterladen.

* Um die Datei mit veröffentlichungseinstellungen aus IIS generieren zu können, benötigen Sie einen Computer, auf denen Windows Server 2012 oder Windows Server 2016 ausgeführt wird, und benötigen Sie die IIS-Webserver-Rolle, die ordnungsgemäß konfiguriert. Entweder ASP.NET 4.5 oder ASP.NET Core muss installiert sein. ASP.NET Core, finden Sie unter [Publishing to IIS](/aspnet/core/publishing/iis?tabs=aspnetcore2x#iis-configuration). ASP.NET 4.5 finden Sie unter [IIS 8.0 mithilfe von ASP.NET 3.5 und ASP.NET 4.5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45).

## <a name="create-a-new-aspnet-project-in-visual-studio"></a>Erstellen eines neuen ASP.NET-Projekts in Visual Studio

1. Wählen Sie auf dem Computer mit Visual Studio, **Datei** > **neues Projekt**.

1. Klicken Sie unter **Visual C#-** oder **Visual Basic**, wählen Sie **Web**, und wählen Sie dann im mittleren Bereich entweder **ASP.NET-Webanwendung ((.NET Framework)** oder (nur c#) **ASP.NET Core-Webanwendung**, und klicken Sie dann auf **OK**.

    Wenn die angegebene-Projektvorlagen nicht angezeigt wird, klicken Sie auf die **Visual Studio-Installer öffnen** Link im linken Bereich des der **neues Projekt** Dialogfeld. Der Visual Studio-Installer wird gestartet. Siehe die Voraussetzungen in diesem Artikel sind die erforderlichen Visual Studio-arbeitsauslastungen, die installiert werden muss.

1. Wählen Sie entweder **MVC** ((.NET Framework) oder **Webanwendung (Model-View-Controller)** (für .NET Core), und stellen Sie sicher, dass **keine Authentifizierung** ausgewählt ist, und klicken Sie dann auf **OK**.

1. Geben Sie einen Namen wie **MyWebApp** , und klicken Sie auf **OK**.

    Visual Studio erstellt daraufhin das Projekt.

1. Wählen Sie **erstellen** > **Projektmappe** zum Erstellen des Projekts.

## <a name="install-and-configure-web-deploy-on-windows-server"></a>Installieren und Konfigurieren von Web Deploy unter Windows Server

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/install-web-deploy-with-hosting-server.md)]

## <a name="create-the-publish-settings-file-in-iis-on-windows-server"></a>Erstellen Sie die Datei mit veröffentlichungseinstellungen in IIS unter Windows Server

[!INCLUDE [create-publish-settings-iis](../deployment/includes/create-publish-settings-iis.md)]

## <a name="import-the-publish-settings-in-visual-studio-and-deploy"></a>Die Einstellungen für die Veröffentlichung in Visual Studio importieren und bereitstellen

[!INCLUDE [import-publish-settings](../deployment/includes/import-publish-settings-vs.md)]

Nachdem die app erfolgreich bereitgestellt wurde, sollten sie automatisch gestartet. Wenn sie nicht über Visual Studio gestartet wird, starten Sie die app in IIS. Für ASP.NET Core, müssen Sie sicherstellen, dass der Anwendungspool für Feld der **DefaultAppPool** nastaven NA hodnotu **kein verwalteter Code**.

## <a name="next-steps"></a>Nächste Schritte

In diesem Tutorial haben Sie erstellt eine Datei mit veröffentlichungseinstellungen importiert es in Visual Studio und eine ASP.NET-App in IIS bereitgestellt. Sie sollten einen Überblick über die anderen Optionen für die Veröffentlichung in Visual Studio.

> [!div class="nextstepaction"]
> [Erster Einblick in die Bereitstellung](../deployment/deploying-applications-services-and-components.md)
