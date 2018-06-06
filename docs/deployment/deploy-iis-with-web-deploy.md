---
title: Bereitstellen von ASP.NET in IIS mithilfe von Web Deploy
ms.custom: ''
ms.date: 06/04/2018
ms.technology: vs-ide-deployment
ms.topic: tutorial
ms.assetid: 9cb339b5-3caf-4755-aad1-4a5da54b2a23
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- aspnet
ms.openlocfilehash: a63d9947f544ddff1de81aaf34ed62c9646fba3d
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/05/2018
ms.locfileid: "34794204"
---
# <a name="deploy-aspnet-to-a-remote-iis-computer-using-web-deploy-in-visual-studio"></a>Bereitstellen von ASP.NET auf einem IIS-Remotecomputer in Visual Studio mithilfe von Web Deploy

In diesem Artikel wird erläutert, wie zum Einrichten und konfigurieren eine Visual Studio 2017 ASP.NET MVC 4.5.2-Anwendung auf IIS bereitgestellt wird. Dieser Artikel enthält die Schritte zum Einrichten einer Standardkonfiguration von IIS unter WindowsServer und zum Bereitstellen der app aus Visual Studio. Diese Schritte sind enthalten, um sicherzustellen, dass es sich bei der Server installierte Komponenten erforderlich ist und Sie bereitstellen möchten. Wenn Sie eine ASP.NET Core-Anwendung bereitstellen möchten, unterscheiden sich einige Schritte ausführen. Um eine ASP.NET Core-Anwendung bereitstellen, finden Sie unter [Veröffentlichen einer Anwendung in IIS durch Importieren von veröffentlichungseinstellungen](../deployment/tutorial-import-publish-settings-iis.md) Anweisungen. In einigen Szenarien ASP.NET und ASP.NET Core ist es schneller, zum Bereitstellen von IIS durch Importieren von veröffentlichungseinstellungen.

Diese Prozeduren haben auf diese Serverkonfigurationen getestet:
* Windows Server 2012 R2 und IIS 8 (für Windows Server 2008 R2 Server die Schritte sind verschiedene)

## <a name="create-the-aspnet-452-application-on-the-visual-studio-computer"></a>Erstellen Sie die ASP.NET 4.5.2 Anwendung auf dem Visual Studio-Computer
  
1. Wählen Sie auf dem Computer mit Visual Studio, **Datei > Neues Projekt**.

1. Klicken Sie unter **Visual C#-** oder **Visual Basic**, wählen Sie **Web**, und wählen Sie dann im mittleren Bereich entweder **ASP.NET-Webanwendung ((.NET Framework)**, und klicken Sie dann auf **OK**.

    Wenn die angegebene-Projektvorlagen nicht angezeigt wird, klicken Sie auf die **Installer für Visual Studio öffnen** Link im linken Bereich des der **neues Projekt** (Dialogfeld). Der Visual Studio-Installer wird gestartet. Siehe die Voraussetzungen in diesem Artikel, um die erforderlichen Visual Studio-arbeitsauslastungen, identifiziert werden, die Sie installieren müssen.

1. Wählen Sie **MVC** ((.NET Framework) und stellen Sie sicher, dass **keine Authentifizierung** ausgewählt ist, und klicken Sie dann auf **OK**.

1. Geben Sie einen Namen wie **MyWebApp** , und klicken Sie auf **OK**.

    Visual Studio erstellt daraufhin das Projekt.

1. Wählen Sie **erstellen > Projektmappe** zum Erstellen des Projekts.

## <a name="bkmk_configureIIS"></a> Installieren und Konfigurieren von IIS unter WindowsServer

[!INCLUDE [remote-debugger-install-iis-role](../debugger/includes/remote-debugger-install-iis-role.md)]

## <a name="update-browser-security-settings-on-windows-server"></a>Aktualisieren von Browsersicherheitseinstellungen unter Windows Server

Wenn die verstärkte Sicherheitskonfiguration in Internet Explorer aktiviert ist (er ist standardmäßig aktiviert), müssen Sie einige Domänen hinzufügen, als vertrauenswürdigen Sites ermöglichen Ihnen, einige Web-Server-Komponenten herunterzuladen. Fügen Sie der vertrauenswürdigen Sites hinzu, durch das Aufrufen **Internetoptionen > Sicherheit > Vertrauenswürdige Sites > Sites**. Fügen Sie die folgenden Domänen hinzu.

- microsoft.com
- go.microsoft.com
- 0download.microsoft.com
- IIS.NET

Wenn Sie die Software heruntergeladen haben, erhalten Sie möglicherweise Anforderungen an die Berechtigung zum Laden von verschiedenen Website-Skripts und Ressourcen gewähren. Einige dieser Ressourcen sind nicht erforderlich, aber den Prozess zu vereinfachen, klicken Sie auf **hinzufügen** Aufforderung.

## <a name="BKMK_deploy_asp_net"></a> Installieren Sie ASP.NET 4.5 unter WindowsServer

Wenn Sie ausführlichere Informationen zur ASP.NET auf IIS installieren möchten, finden Sie unter [IIS 8.0 mithilfe von ASP.NET 3.5 und ASP.NET 4.5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45).

1. Wählen Sie im linken Bereich des Server-Managers **IIS**. Mit der rechten Maustaste in des Servers, und wählen Sie **(Internet Information Services, IIS) Manager**.

1. Verwenden Sie den Webplattform-Installer (WebPI), um ASP.NET 4.5 installieren (Wählen Sie den Serverknoten in Windows Server 2012 R2, **neue Webplattformkomponenten abrufen** und suchen Sie nach ASP.NET)

    ![RemoteDBG_IIS_AspNet_45](../debugger/media/remotedbg_iis_aspnet_45.png "RemoteDBG_IIS_AspNet_45")

    > [!NOTE]
    > Wenn Sie Windows Server 2008 R2 verwenden, installieren Sie ASP.NET 4 stattdessen mit dem folgenden Befehl:

     **C:\Windows\Microsoft.NET\Framework64\v4.0.30319\aspnet_regiis.exe -ir**

2. Das System neu starten (oder führen Sie **net Stop wurde/y** gefolgt von **Net start w3svc** über eine Eingabeaufforderung, um eine Änderung am System Pfad übernehmen).

## <a name="BKMK_install_webdeploy"></a> Installieren Sie Web Deploy 3.6 unter WindowsServer

[!INCLUDE [remote-debugger-install-web-deploy](../debugger/includes/remote-debugger-install-web-deploy.md)]

## <a name="BKMK_deploy_asp_net"></a> Konfigurieren Sie ASP.NET-Website, auf dem Windows Server-computer

1. Öffnen Sie Windows Explorer, und erstellen Sie einen neuen Ordner **C:\Publish**, in dem ASP.NET-Projekt später bereitstellen möchten.

2. Wenn es nicht bereits geöffnet ist, öffnen Sie die **(Internet Information Services, IIS) Manager**. (Wählen Sie im linken Bereich des Server-Managers **IIS**. Mit der rechten Maustaste in des Servers, und wählen Sie **(Internet Information Services, IIS) Manager**.)

3. Klicken Sie unter **Verbindungen** im linken Bereich, wechseln Sie zu **Sites**.

4. Wählen Sie die **Default Web Site**, wählen Sie **Grundeinstellungen**, und legen Sie die **physischen Pfad** auf **C:\Publish**.

5. Klicken Sie mit der rechten Maustaste auf den Knoten **Standardwebsite** , und wählen Sie **Anwendung hinzufügen**aus.

6. Festlegen der **Alias** Feld **MyASPApp**, übernehmen Sie den Standardnamen Anwendungspool (**DefaultAppPool**), und legen Sie die **physischen Pfad** auf  **C:\Publish**.

7. Klicken Sie unter **Verbindungen**Option **Anwendungspools**. Open **DefaultAppPool** und legen Sie das Feld "Anwendungspool" auf **ASP.NET v4. 0** (ASP.NET 4.5 ist keine Option für den Anwendungspool).

8. Mit den Standort im IIS-Manager ausgewählt haben, wählen Sie **Berechtigungen bearbeiten**, und stellen Sie sicher, diese IUSR, IIS_IUSRS oder der Benutzer, die für den Anwendungspool ein autorisierter Benutzer mit Berechtigungen für Lesen & ausführen wird konfiguriert. Wenn keiner dieser Benutzer vorhanden ist, fügen Sie IUSR als ein Benutzer Berechtigungen für Lesen & ausführen.

## <a name="bkmk_webdeploy"></a> Veröffentlichen und Bereitstellen der app mithilfe von Web Deploy von Visual Studio

[!INCLUDE [deploy-app-web-deploy](../deployment/includes/deploy-app-web-deploy.md)]

Darüber hinaus möglicherweise auf den Abschnitt lesen [Problembehandlung Ports](#bkmk_openports).

## <a name="bkmk_openports"></a> Zur Fehlerbehebung: Öffnen Sie erforderlichen Ports auf Windows Server

In den meisten Installationen werden die erforderlichen Ports durch die Installation von ASP.NET und Web Deploy geöffnet. Allerdings müssen Sie möglicherweise stellen Sie sicher, dass die Ports geöffnet sind.

> [!NOTE]
> Auf einem virtuellen Azure-Computer müssen Sie Ports durch Öffnen der [Netzwerksicherheitsgruppe](/azure/virtual-machines/virtual-machines-windows-hero-role#open-port-80). 

Erforderliche Ports:

* 80 - wird für IIS erforderlich.
* 8172 - wird für Web Deploy zum Bereitstellen der app aus Visual Studio erforderlich.

1. Um einen Port unter Windows Server zu öffnen, öffnen die **starten** Menü, suchen Sie nach **Windows-Firewall mit erweiterter Sicherheit**.

2. Wählen Sie dann **eingehende Regeln > neue Regel > Port**. Wählen Sie **Weiter** und wählen Sie unter **bestimmte lokale Ports**, geben Sie die Portnummer an, klicken Sie auf **Weiter**, klicken Sie dann **Verbindung zulassen**, klicken Sie auf Weiter, und Fügen Sie den Namen (**IIS**, **Web Deploy**, oder **Msvsmon**) für die eingehende Regel.

    Wenn Sie weitere Informationen zum Windows-Firewall konfigurieren möchten, finden Sie unter [der Windows-Firewall für Remotedebuggen konfigurieren](../debugger/configure-the-windows-firewall-for-remote-debugging.md).

3. Erstellen Sie zusätzliche Regeln für die anderen erforderlichen Ports.

## <a name="next-steps"></a>Nächste Schritte

In diesem Lernprogramm erstellt eine Datei mit veröffentlichungseinstellungen, Visual Studio importiert und eine ASP.NET app in IIS bereitgestellt. Sie können auch bereitstellen, durch das Importieren von veröffentlichungseinstellungen.

> [!div class="nextstepaction"]
> [Bereitstellen für IIS durch Importieren von veröffentlichungseinstellungen](../deployment/tutorial-import-publish-settings-iis.md)