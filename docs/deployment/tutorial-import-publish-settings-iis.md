---
title: Veröffentlichen in IIS durch Importieren von veröffentlichungseinstellungen
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
ms.openlocfilehash: 02e6ae6e06daf43a6aec08097df2b37a21d2aaa3
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/05/2018
ms.locfileid: "34766673"
---
# <a name="publish-an-application-to-iis-by-importing-publish-settings-in-visual-studio"></a>Veröffentlichen von einer Anwendung in IIS durch Importieren von veröffentlichungseinstellungen in Visual Studio

Können Sie die **veröffentlichen** Tool zum Importieren von veröffentlichungseinstellungen, und klicken Sie dann die app bereitstellen. In diesem Artikel verwenden wir veröffentlichungseinstellungen für IIS, jedoch können Sie ähnliche Schritte zum Importieren von veröffentlichungseinstellungen für [Azure App Service](../deployment/tutorial-import-publish-settings-azure.md). In einigen Szenarien ist die Verwendung von veröffentlichen, Einstellungsprofil, das schneller sein kann als das manuelle Konfigurieren der Bereitstellung in IIS für jede Installation von Visual Studio, aus.

Diese Schritte gelten für ASP.NET, ASP.NET Core und .NET Core-apps in Visual Studio. Die Schritte entsprechen den Visual Studio 2017 Version 15,6.

In diesem Tutorial werden Sie Folgendes durchführen:

> [!div class="checklist"]
> * Konfigurieren Sie IIS so, dass eine Datei mit veröffentlichungseinstellungen generiert werden kann
> * Erstellen Sie eine Datei mit veröffentlichungseinstellungen
> * Importieren Sie die Datei mit veröffentlichungseinstellungen in Visual Studio
> * Bereitstellen der app in IIS

Eine Datei mit veröffentlichungseinstellungen (*\*publishsettings*) unterscheidet sich ein Veröffentlichungsprofil angeben (*\*pubxml*) in Visual Studio erstellt wurden. Eine Datei mit veröffentlichungseinstellungen wird erstellt, indem der IIS- oder Azure App Service, oder kann manuell erstellt werden, und klicken Sie dann in Visual Studio importiert werden können.

> [!NOTE]
> Wenn Sie nur eine Visual Studio Veröffentlichungsprofil kopieren müssen (\*Datei "pubxml") aus einer Installation von Visual Studio in einen anderen finden Sie das Veröffentlichungsprofil  *\<Profilename\>pubxml*, in der  *\\< Projectname\>\Properties\PublishProfiles* Ordner für verwaltete Projekttypen zur Verfügung. Für Websites, suchen Sie unter der *\App_Data* Ordner. Die publishing Profile handelt es sich um MSBuild XML-Dateien.

## <a name="prerequisites"></a>Erforderliche Komponenten

* Sie müssen Visual Studio 2017 installiert haben und die **ASP.NET** und **.NET Framework** Entwicklungsaufwand. Für eine .NET Core-app müssen Sie auch die **.NET Core** arbeitsauslastung.

    Wenn Sie Visual Studio noch nicht installiert haben, können Sie es auf der Seite [Visual Studio-Downloads](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) kostenlos herunterladen.

* Zum Generieren der Datei mit veröffentlichungseinstellungen aus IIS benötigen Sie einen Computer mit Windows Server 2012 oder Windows Server 2016 und benötigen Sie die IIS-Webserver-Rolle ordnungsgemäß konfiguriert. ASP.NET 4.5 oder ASP.NET Core muss installiert sein. ASP.NET Core, finden Sie unter [in IIS veröffentlichen](/aspnet/core/publishing/iis?tabs=aspnetcore2x#iis-configuration). ASP.NET 4.5 finden Sie unter [IIS 8.0 mithilfe von ASP.NET 3.5 und ASP.NET 4.5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45).

## <a name="create-a-new-aspnet-project-in-visual-studio"></a>Erstellen eines neuen ASP.NET-Projekts in Visual Studio

1. Wählen Sie auf dem Computer mit Visual Studio, **Datei > Neues Projekt**.

1. Klicken Sie unter **Visual C#-** oder **Visual Basic**, wählen Sie **Web**, und wählen Sie dann im mittleren Bereich entweder **ASP.NET-Webanwendung ((.NET Framework)** oder (nur c#) **ASP.NET-Webanwendung für Core**, und klicken Sie dann auf **OK**.

    Wenn die angegebene-Projektvorlagen nicht angezeigt wird, klicken Sie auf die **Installer für Visual Studio öffnen** Link im linken Bereich des der **neues Projekt** (Dialogfeld). Der Visual Studio-Installer wird gestartet. Siehe die Voraussetzungen in diesem Artikel, um die erforderlichen Visual Studio-arbeitsauslastungen, identifiziert werden, die Sie installieren müssen.

1. Wählen Sie entweder **MVC** ((.NET Framework) oder **Webanwendung (Model-View-Controller)** (für .NET Core), und stellen Sie sicher, dass **keine Authentifizierung** ausgewählt ist, und klicken Sie dann auf **OK**.

1. Geben Sie einen Namen wie **MyWebApp** , und klicken Sie auf **OK**.

    Visual Studio erstellt daraufhin das Projekt.

1. Wählen Sie **erstellen > Projektmappe** zum Erstellen des Projekts.

## <a name="install-and-configure-web-deploy-on-windows-server"></a>Installieren und Konfigurieren von Web Deploy unter Windows Server

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/install-web-deploy-with-hosting-server.md)]

## <a name="create-the-publish-settings-file-in-iis-on-windows-server"></a>Erstellen Sie die Datei mit veröffentlichungseinstellungen in IIS unter Windows Server

[!INCLUDE [create-publish-settings-iis](../deployment/includes/create-publish-settings-iis.md)]

## <a name="import-the-publish-settings-in-visual-studio-and-deploy"></a>Die Einstellungen für die Veröffentlichung in Visual Studio importieren und bereitstellen

[!INCLUDE [import-publish-settings](../deployment/includes/import-publish-settings-vs.md)]

Nachdem die app erfolgreich bereitgestellt hat, sollte er automatisch gestartet. Wenn sie nicht über Visual Studio startet, starten Sie die app in IIS. Für ASP.NET Core, müssen Sie sicherstellen, dass der Anwendungspool für Feld der **DefaultAppPool** festgelegt ist, um **kein verwalteter Code**.

## <a name="next-steps"></a>Nächste Schritte

In diesem Lernprogramm erstellt eine Datei mit veröffentlichungseinstellungen, Visual Studio importiert und eine ASP.NET app in IIS bereitgestellt. Sie sollten einen Überblick über die anderen Optionen für die Veröffentlichung in Visual Studio.

> [!div class="nextstepaction"]
> [Erster Einblick in die Bereitstellung](../deployment/deploying-applications-services-and-components.md)
