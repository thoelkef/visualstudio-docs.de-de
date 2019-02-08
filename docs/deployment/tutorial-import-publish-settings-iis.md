---
title: Veröffentlichen in IIS durch Importieren von Veröffentlichungseinstellungen
description: Erstellen und Importieren eines Veröffentlichungsprofils zum Bereitstellen einer Anwendung aus Visual Studio in IIS
ms.date: 01/31/2019
ms.topic: tutorial
helpviewer_keywords:
- deployment, publish settings
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b38f9d951be37619c84095c379879e1acd51cf7b
ms.sourcegitcommit: 0f7411c1a47d996907a028e920b73b53c2098c9f
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/04/2019
ms.locfileid: "55690449"
---
# <a name="publish-an-application-to-iis-by-importing-publish-settings-in-visual-studio"></a>Veröffentlichen einer Anwendung in IIS durch Importieren von Veröffentlichungseinstellungen in Visual Studio

Sie können das Tool **Veröffentlichen** zum Importieren von Veröffentlichungseinstellungen verwenden. Anschließend können Sie die App bereitstellen. In diesem Artikel werden Veröffentlichungseinstellungen für IIS verwendet, allerdings können Sie die gleiche Vorgehensweise zum Importieren von Veröffentlichungseinstellungen für [Azure App Service](../deployment/tutorial-import-publish-settings-azure.md) verwenden. Die Verwendung eines Veröffentlichungseinstellungsprofils kann sich in einigen Szenarios als schneller als das manuelle Konfigurieren der Bereitstellung in IIS für jede Installation von Visual Studio erweisen.

Die in diesem Artikel genannten Schritte gelten für ASP.NET, ASP.NET Core und .NET Core-Apps in Visual Studio. Die Schritte sind auf dem Stand von Visual Studio 2017, Version 15.6.

In diesem Tutorial werden Sie Folgendes durchführen:

> [!div class="checklist"]
> * Konfigurieren von IIS, sodass Sie ein Veröffentlichungseinstellungsprofil generieren können
> * Erstellen einer Veröffentlichungseinstellungsdatei
> * Importieren der Veröffentlichungseinstellungsdatei in Visual Studio
> * Bereitstellen der App in IIS

Eine Veröffentlichungseinstellungsdatei (*\*.publishsettings*) unterscheidet sich von einem in Visual Studio erstellten Veröffentlichungsprofil (*\*.pubxml*). Eine Veröffentlichungseinstellungsdatei wird von IIS oder Azure App Service erstellt. Sie können sie aber auch manuell erstellen und dann in Visual Studio importieren.

> [!NOTE]
> Sie müssen lediglich ein Visual Studio-Veröffentlichungsprofil (\*.pubxml-Datei) aus einer Installation von Visual Studio in eine andere kopieren. Das Veröffentlichungsprofil *\<Profilname\>.pubxml* finden Sie im Ordner *\\<Projektname\>\Properties\PublishProfiles* für verwaltete Projekttypen. Suchen Sie im Ordner *\App_Data* nach Websites. Die Veröffentlichungsprofile sind XML-Dateien von MSBuild.

## <a name="prerequisites"></a>Erforderliche Komponenten

* Sie müssen Visual Studio 2017 und die Workload **ASP.NET und Webentwicklung** auf Ihrem Entwicklungscomputer installiert haben.

    Wenn Sie Visual Studio noch nicht installiert haben, können Sie es auf der Seite  [Visual Studio-Downloads](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017)  kostenlos herunterladen.

* Sie müssen Windows Server 2012 oder Windows Server 2016 auf Ihrem Server ausführen, und die [IIS-Webserverrolle](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45) muss ordnungsgemäß installiert sein (zum Generieren der Veröffentlichungseinstellungsdatei (*\*.publishsettings*) erforderlich). Außerdem muss entweder ASP.NET 4.5 oder ASP.NET Core auf dem Server installiert sein. Informationen zum Einrichten von ASP.NET 4.5 finden Sie unter [IIS 8.0 Using ASP.NET 3.5 and ASP.NET 4.5 (IIS 8.0 mit ASP.NET 3.5 und ASP.NET 4.5)](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45). Informationen zum Einrichten von ASP.NET Core finden Sie unter [Hosten von ASP.NET Core unter Windows mit IIS](/aspnet/core/publishing/iis?tabs=aspnetcore2x#iis-configuration). 

## <a name="create-a-new-aspnet-project-in-visual-studio"></a>Erstellen eines neuen ASP.NET-Projekts in Visual Studio

1. Klicken Sie auf dem Computer, auf dem Visual Studio ausgeführt wird, auf **Datei** > **Neues Projekt**.

1. Klicken Sie in **Visual C#** oder **Visual Basic** auf **Web**, wählen Sie dann im mittleren Bereich entweder **ASP.NET-Webanwendung (.NET Framework)** oder **ASP.NET Core-Webanwendung** (nur für C#) aus, und klicken Sie anschließend auf **OK**.

    Wenn Ihnen die angegebenen Projektvorlagen nicht angezeigt werden, klicken Sie im linken Bereich des Dialogfelds **Neues Projekt** auf den Link **Visual Studio-Installer öffnen**. Der Visual Studio-Installer wird gestartet. Installieren Sie die Workload **ASP.NET und Webentwicklung**.

    Die ausgewählte Projektvorlage (ASP.NET oder ASP.NET Core) muss 

1. Wählen Sie entweder **MVC** (für .NET Framework) oder **Webanwendung (Model-View-Controller)** (für .NET Core) aus, und stellen Sie sicher, dass **Keine Authentifizierung** ausgewählt ist, klicken Sie anschließend auf **OK**.

1. Geben Sie einen Namen wie **MyWebApp** ein, und klicken Sie auf **OK**.

    Visual Studio erstellt daraufhin das Projekt.

1. Klicken Sie auf **Erstellen** > **Projektmappe erstellen**, um das Projekt zu erstellen.

## <a name="install-and-configure-web-deploy-on-windows-server"></a>Installieren und Konfigurieren von Web Deploy unter Windows Server

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/install-web-deploy-with-hosting-server.md)]

## <a name="create-the-publish-settings-file-in-iis-on-windows-server"></a>Erstellen der Veröffentlichungseinstellungsdatei in IIS unter Windows Server

[!INCLUDE [create-publish-settings-iis](../deployment/includes/create-publish-settings-iis.md)]

## <a name="import-the-publish-settings-in-visual-studio-and-deploy"></a>Importieren und Bereitstellen der Veröffentlichungseinstellungen in Visual Studio

[!INCLUDE [import-publish-settings](../deployment/includes/import-publish-settings-vs.md)]

Nachdem die App erfolgreich bereitgestellt wurde, sollte sie automatisch gestartet werden. Wenn sie nicht über Visual Studio gestartet wird, starten Sie sie in IIS. Für ASP.NET Core müssen Sie sicherstellen, dass das Feld „Anwendungspool“ für **DefaultAppPool** auf **Kein verwalteter Code** festgelegt ist.

## <a name="next-steps"></a>Nächste Schritte

In diesem Tutorial haben Sie eine Veröffentlichungseinstellungsdatei erstellt, diese in Visual Studio importiert und eine ASP.NET-App in IIS bereitgestellt. Sie sollten sich einen Überblick über andere Veröffentlichungsoptionen in Visual Studio verschaffen.

> [!div class="nextstepaction"]
> [Erster Einblick in die Bereitstellung](../deployment/deploying-applications-services-and-components.md)
