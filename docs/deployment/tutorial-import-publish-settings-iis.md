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
ms.openlocfilehash: b023349454f71835e13e7cc891b8be92b90c153f
ms.sourcegitcommit: 046a9adc5fa6d6d05157204f5fd1a291d89760b7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/11/2018
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

* Sie müssen Visual Studio installiert haben und die **ASP.NET** und **.NET Framework** Entwicklungsaufwand. Für eine .NET Core-app müssen Sie auch die **.NET Core** arbeitsauslastung.

    Falls Sie Visual Studio noch nicht installiert haben, können Sie es [hier](http://www.visualstudio.com) gratis herunterladen.

    Die Schritte in diesem Artikel basieren auf Visual Studio 2017

* Zum Generieren der Datei mit veröffentlichungseinstellungen aus IIS benötigen Sie einen Computer mit Windows Server 2012 mit der IIS 8.0-Webserver-Rolle ordnungsgemäß konfiguriert und ASP.NET 4.5 oder ASP.NET Core installiert. ASP.NET Core, finden Sie unter [in IIS veröffentlichen](/aspnet/core/publishing/iis?tabs=aspnetcore2x#iis-configuration). ASP.NET 4.5 finden Sie unter [IIS 8.0 mithilfe von ASP.NET 3.5 und ASP.NET 4.5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45).

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

1. In IIS, mit der Maustaste die **Default Web Site**, wählen Sie **bereitstellen** > **konfigurieren bereitstellen Webveröffentlichung**.

    ![Konfigurieren von Web Deploy-Konfiguration](../deployment/media/tutorial-configure-web-deploy-publishing.png)

1. In der **konfigurieren bereitstellen Webveröffentlichung** Dialogfeld sehen Sie die Einstellungen.

1. Klicken Sie auf **Setup**.

    In der **Ergebnisse** Bereich die Ausgabe zeigt an, die Zugriffsrechte erteilt wurde für den angegebenen Benutzer und, eine Datei mit einer *publishsettings* -Erweiterung generiert wurde, an der Stelle angezeigt, der Das Dialogfeld.

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <publishData>
      <publishProfile
        publishUrl="https://myhostname:8172/msdeploy.axd"
        msdeploySite="Default Web Site"
        destinationAppUrl="http://myhostname:80/"
        mySQLDBConnectionString=""
        SQLServerDBConnectionString=""
        profileName="Default Settings"
        publishMethod="MSDeploy"
        userName="myhostname\myusername" />
    </publishData>
    ```

    Abhängig von Ihrer Windows Server und IIS-Konfiguration sehen Sie unterschiedliche Werte. Nachfolgend sind einige Details zu den Werten, die Sie sehen:

    * Die *msdeploy.axd* Datei verwiesen wird, dem `publishUrl` -Attribut ist eine dynamisch generierte HTTP-Handler-Datei für Web Deploy. (Für Testzwecke wird `http://myhostname:8172` in der Regel optimal funktioniert.)
    * Die `publishUrl` Port in der Regel auf Port 8172, dies ist die Standardeinstellung für Web Deploy ist festgelegt.
    * Die `destinationAppUrl` Port in der Regel auf Port 80, dies die Standardgröße für IIS ist festgelegt.
    * Wenn Sie keine Verbindung mit dem Remotehost in Visual Studio unter Verwendung des Hostnamens (in späteren Schritten) möglich sind, testen Sie die IP-Adresse anstelle der Hostname.

    > [!NOTE]
    > Wenn Sie auf einer Azure-VM unter IIS veröffentlichen, müssen Web Deploy und IIS-Ports in der Netzwerk-Sicherheitsgruppe geöffnet werden. Ausführliche Informationen finden Sie unter [installieren und Ausführen von IIS](/azure/virtual-machines/windows/quick-create-portal#open-port-80-for-web-traffic).

1. Kopieren Sie diese Datei auf dem Computer, auf dem Sie Visual Studio ausgeführt werden.

## <a name="import-the-publish-settings-in-visual-studio-and-deploy"></a>Die Einstellungen für die Veröffentlichung in Visual Studio importieren und bereitstellen

1. Klicken Sie auf dem Computer, die dort stehen Ihnen die ASP.NET-Projekt in Visual Studio öffnen, mit der rechten Maustaste des Projekts im Projektmappen-Explorer, und wählen Sie **veröffentlichen**.

1. Wenn Sie Veröffentlichungsprofile zuvor konfiguriert haben die **veröffentlichen** Bereich wird angezeigt. Klicken Sie auf **neues Profil erstellen**.

1. In der **Veröffentlichungsziel auswählen** (Dialogfeld), klicken Sie auf **Profil importieren**.

    ![Wählen Sie veröffentlichen](../deployment/media/tutorial-publish-tool-import-profile.png)

1. Navigieren Sie zum Speicherort der Datei mit den veröffentlichungseinstellungen, den Sie im vorherigen Abschnitt erstellt haben.

1. In der **veröffentlichen-Einstellungsdatei importieren** (Dialogfeld), navigieren Sie zu und wählen Sie das Profil, das Sie im vorherigen Abschnitt erstellt haben, und klicken Sie auf **öffnen**.

    Visual Studio startet den Bereitstellungsprozess, und das Ausgabefenster zeigt Status und die Ergebnisse.

    Wenn Sie einer Bereitstellung Fehler angezeigt werden, klicken Sie auf **Einstellungen** Einstellungen bearbeiten. Ändern Sie die Einstellungen, und klicken Sie auf **Validate** So testen Sie die neue Einstellungen.

    ![Bearbeiten von Einstellungen in den Tools zum Veröffentlichen](../deployment/media/tutorial-configure-publish-settings-in-tool.png)

## <a name="next-steps"></a>Nächste Schritte

In diesem Lernprogramm erstellt eine Datei mit veröffentlichungseinstellungen, Visual Studio importiert und eine ASP.NET app in IIS bereitgestellt.

> [!div class="nextstepaction"]
> [Erster Einblick in die Bereitstellung](../deployment/deploying-applications-services-and-components.md)
