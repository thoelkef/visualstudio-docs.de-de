---
title: Remote Debug ASP.NET Core auf einem Remote-IIS-Computer | Microsoft Docs
ms.custom: remotedebugging
ms.date: 08/14/2017
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 573a3fc5-6901-41f1-bc87-557aa45d8858
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- aspnet
- dotnetcore
ms.openlocfilehash: e4c0311f8e011b8cab3e189f309cd618a485bd71
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/18/2018
---
# <a name="remote-debug-aspnet-core-on-a-remote-iis-computer-in-visual-studio-2017"></a>Remotedebuggen von ASP.NET Core auf einem Remote-IIS-Computer in Visual Studio 2017
Um eine ASP.NET-Anwendung debuggen, die in IIS bereitgestellt wurde, installieren Sie und führen Sie der Remotetools auf dem Computer aus, auf denen Sie Ihre app bereitgestellt haben, und fügen Sie an der ausgeführten app aus Visual Studio.

![Remotedebugger-Komponenten](../debugger/media/remote-debugger-aspnet.png "Remote_debugger_components")

Dieses Handbuch erläutert das Einrichten einer Visual Studio 2017 ASP.NET Core, für IIS bereitstellen und Konfigurieren von Visual Studio remote Debugger anfügen. Zum Remotedebuggen ASP.NET 4.5.2 finden Sie unter [Remote Debuggen von ASP.NET auf einem Computer mit IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md). Sie können auch bereitstellen und Debuggen von IIS mithilfe von Azure. Für Azure App Service, Sie einfache bereitstellen und Debuggen auf einem vorkonfigurierten Instanz von IIS und den Remotedebugger entweder können die [Momentaufnahme Debugger](../debugger/debug-live-azure-applications.md) oder [das Anfügen des Debuggers aus Server-Explorer](../debugger/remote-debugging-azure.md).

Diese Prozeduren haben auf diese Serverkonfigurationen getestet:
* Windows Server 2012 R2 und IIS 8
* WindowsServer 2016 und IIS 10

## <a name="requirements"></a>Anforderungen

Debuggen zwischen zwei Computern über einen Proxy verbunden wird nicht unterstützt. Remotedebuggen über eine hohe Latenz oder eine Verbindung mit geringer Bandbreite, z. B. DFÜ, Internet oder über das Internet Ländern wird nicht empfohlen und möglicherweise fehl oder sehr langsam sein. Eine vollständige Liste der Anforderungen, finden Sie unter [Anforderungen](../debugger/remote-debugging.md#requirements_msvsmon).

## <a name="create-the-aspnet-core-application-on-the-visual-studio-2017-computer"></a>Erstellen Sie die ASP.NET Core-Anwendung auf dem Computer Visual Studio 2017 

1. Erstellen einer neuen ASP.NET Core-Anwendung. (**Datei > Neu > Projekt**, und wählen Sie dann **Visual c# > Web > ASP.NET Core Web Application**).

    In der **ASP.NET Core** -Vorlagenabschnitt wählen **Webanwendung**.

2. Stellen Sie sicher, dass **ASP.NET Core 2.0** ausgewählt ist, **Docker-Unterstützung aktivieren** ist **nicht** ausgewählten und **Authentifizierung** auf festgelegt ist **Keine Authentifizierung**.

3. Nennen Sie das Projekt **MyASPApp** , und klicken Sie auf **OK** um die neue Projektmappe zu erstellen.

4. Öffnen Sie die Datei About.cshtml.cs, und legen Sie einen Haltepunkt der `OnGet` Methode (Öffnen Sie in älteren Vorlagen HomeController.cs stattdessen, und legen Sie den Haltepunkt der `About()` Methode).

## <a name="bkmk_configureIIS"></a> Installieren und Konfigurieren von IIS unter WindowsServer

[!INCLUDE [remote-debugger-install-iis-role](../debugger/includes/remote-debugger-install-iis-role.md)]

## <a name="update-browser-security-settings-on-windows-server"></a>Aktualisieren von Browsersicherheitseinstellungen unter Windows Server

Je nach Ihren Sicherheitseinstellungen kann es Speicherzeit Sie Ihren Browser die folgenden vertrauenswürdigen Sites hinzugefügt werden, damit Sie problemlos in diesem Lernprogramm beschriebene Software herunterladen können. Möglicherweise müssen Sie den Zugriff auf diese Websites:

- microsoft.com
- go.microsoft.com
- 0download.microsoft.com
- visualstudio.com

Wenn Sie Internet Explorer verwenden, können Sie den vertrauenswürdigen Sites hinzufügen, navigieren Sie zu **Internetoptionen > Sicherheit > Vertrauenswürdige Sites > Sites**. Diese Schritte sind für andere Browser unterschiedlich. (Wenn Sie eine ältere Version des Remotedebuggers von my.visualstudio.com herunterladen müssen, sind einige zusätzliche vertrauenswürdige Websites erforderlich, sich anzumelden.)

Wenn Sie die Software heruntergeladen haben, erhalten Sie möglicherweise Anforderungen an die Berechtigung zum Laden von verschiedenen Website-Skripts und Ressourcen gewähren. In den meisten Fällen sind die folgenden zusätzlichen Ressourcen beim Installieren der Clientsoftware nicht erforderlich.

## <a name="install-aspnet-core-on-windows-server"></a>Installieren Sie ASP.NET Core unter WindowsServer

1. Installieren der [.NET Core Windows Server-Hosting](https://aka.ms/dotnetcore-2-windowshosting) Paket auf dem Hostsystem. Das Paket wird installiert, die .NET Core-Laufzeit, .NET Core-Bibliothek und ASP.NET Core-Modul. Weitere ausführlichen Anweisungen finden Sie in [in IIS veröffentlichen](/aspnet/core/publishing/iis?tabs=aspnetcore2x#iis-configuration).

    > [!NOTE]
    > Wenn das System nicht über eine Internetverbindung verfügt, erhalten und installieren Sie die *[Microsoft Visual C++ 2015 Redistributable](https://www.microsoft.com/download/details.aspx?id=53840)* vor der Installation von .NET Core Windows Server-Hosting-Paket.

3. Das System neu starten (oder führen Sie **net Stop wurde/y** gefolgt von **Net start w3svc** über eine Eingabeaufforderung, um eine Änderung am System Pfad übernehmen).

## <a name="BKMK_install_webdeploy"></a> (Optional) Installieren Sie Web Deploy 3.6 unter WindowsServer

[!INCLUDE [remote-debugger-install-web-deploy](../debugger/includes/remote-debugger-install-web-deploy.md)]

## <a name="BKMK_deploy_asp_net"></a> Konfigurieren Sie ASP.NET-Website, auf dem Windows Server-computer

1. Öffnen Sie Windows Explorer, und erstellen Sie einen neuen Ordner **C:\Publish**, in dem ASP.NET-Projekt später bereitstellen möchten.

2. Öffnen der **Internetinformationsdienste (IIS) Manager**. (Wählen Sie im linken Bereich des Server-Managers **IIS**. Mit der rechten Maustaste in des Servers, und wählen Sie **(Internet Information Services, IIS) Manager**.)

3. Klicken Sie unter **Verbindungen** im linken Bereich, wechseln Sie zu **Sites**.

4. Wählen Sie die **Default Web Site**, wählen Sie **Grundeinstellungen**, und legen Sie die **physischen Pfad** auf **C:\Publish**.

4. Klicken Sie mit der rechten Maustaste auf den Knoten **Standardwebsite** , und wählen Sie **Anwendung hinzufügen**aus.

5. Festlegen der **Alias** Feld **MyASPApp**, übernehmen Sie den Standardnamen Anwendungspool (**DefaultAppPool**), und legen Sie die **physischen Pfad** auf  **C:\Publish**.

6. Klicken Sie unter **Verbindungen**Option **Anwendungspools**. Open **DefaultAppPool** und legen Sie das Feld "Anwendungspool" auf **kein verwalteter Code**.

7. Mit der rechten Maustaste in der neuen Website im IIS-Manager, wählen Sie **Berechtigungen bearbeiten**, und stellen Sie sicher, diese IUSR, IIS_IUSRS oder der Benutzer für den Zugriff auf die Web-app ein autorisierter Benutzer mit Berechtigungen für Lesen & ausführen wird konfiguriert.

    Wenn Sie einen dieser Benutzer mit Zugriff nicht angezeigt wird, wechseln Sie über die erforderlichen Schritte zum Hinzufügen des IUSR-Konto als Benutzer mit Berechtigungen für Lesen & ausführen.

## <a name="bkmk_webdeploy"></a> (Optional) Veröffentlichen und Bereitstellen der app mithilfe von Web Deploy von Visual Studio

[!INCLUDE [remote-debugger-deploy-app-web-deploy](../debugger/includes/remote-debugger-deploy-app-web-deploy.md)]

## <a name="optional-publish-and-deploy-the-app-by-publishing-to-a-local-folder-from-visual-studio"></a>(Optional) Veröffentlichen und Bereitstellen der Anwendung in einen lokalen Ordner durch die Veröffentlichung aus Visual Studio

Sie können auch veröffentlichen und Bereitstellen der app mit dem Dateisystem oder anderen Tools.

[!INCLUDE [remote-debugger-deploy-app-local](../debugger/includes/remote-debugger-deploy-app-local.md)]

## <a name="BKMK_msvsmon"></a> Herunterladen Sie und installieren Sie die Remoteserver-Verwaltungstools für Windows Server

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]

> [!TIP]
> In einigen Szenarien kann es am effizientesten, führen Sie den Remotedebugger aus einer Dateifreigabe sein. Weitere Informationen finden Sie unter [führen Sie den Remotedebugger aus einer Dateifreigabe](../debugger/remote-debugging.md#fileshare_msvsmon).
  
## <a name="BKMK_setup"></a> Einrichten des Remotedebuggers unter Windows Server

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]

> [!NOTE]
> Wenn Sie benötigen Berechtigungen für zusätzliche Benutzer hinzufügen ändern den Authentifizierungsmodus oder Portnummer für den Remotedebugger, finden Sie unter [Konfigurieren des Remotedebuggers](../debugger/remote-debugging.md#configure_msvsmon).

Informationen zu den Remotedebugger als Dienst ausführen, finden Sie unter [den Remotedebugger als Dienst ausführen](../debugger/remote-debugging.md#bkmk_configureService).

## <a name="BKMK_attach"></a> Anfügen an die ASP.NET-Anwendung vom Visual Studio-Computer aus

1. Öffnen Sie auf dem Visual Studio-Computer die **MyASPApp** Lösung.
2. Klicken Sie in Visual Studio auf **Debuggen > an den Prozess anhängen** (Strg + Alt + P).

    > [!TIP]
    > In Visual Studio 2017 können Sie erneut mit dem gleichen Prozess, die Sie zuvor angefügt mit **Debuggen > an Prozess anfügen...** (Umschalt + Alt + P). 

3. Legen Sie auf das Feld "Qualifizierer"  **\<Name des Remotecomputers >: 4022**.
4. Klicken Sie auf **aktualisieren**.
    Im Fenster sollten einige Prozesse **Verfügbare Prozesse** angezeigt werden.

    Wenn alle Prozesse nicht angezeigt wird, versuchen Sie die IP-Adresse anstelle des remote-Computer (der Port ist erforderlich). Sie können `ipconfig` in einer Befehlszeile, um die IPv4-Adresse abzurufen.

    Wenn Sie verwenden möchten die **suchen** Schaltfläche, müssen Sie möglicherweise [Öffnen von UDP-Port 3702](#bkmk_openports) auf dem Server.

5. Aktivieren Sie  **Prozesse aller Benutzer anzeigen**.
6. Geben Sie den ersten Buchstaben des Namens eines Prozesses, schnell zu finden **dotnet.exe** (für ASP.NET Core).

    ![RemoteDBG_AttachToProcess](../debugger/media/remotedbg_attachtoprocess_aspnetcore.png "RemoteDBG_AttachToProcess")

7. Klicken Sie auf **Anfügen**aus.

8. Öffnen Sie die Website des Remotecomputers. Navigieren Sie in einem Browser auf **http://\<Remotecomputername >**.
    
    Es sollte die ASP.NET-Webseite angezeigt werden.

9. Klicken Sie in der laufenden Anwendung ASP.NET auf den Link, um die **zu** Seite.

    Der Haltepunkt sollte in Visual Studio erreicht werden.

## <a name="bkmk_openports"></a> Zur Fehlerbehebung: Öffnen Sie erforderlichen Ports auf Windows Server

In den meisten Installationen werden die erforderlichen Ports durch die Installation von ASP.NET und den Remotedebugger geöffnet. Allerdings müssen Sie möglicherweise stellen Sie sicher, dass die Ports geöffnet sind.

> [!NOTE]
> Auf einem virtuellen Azure-Computer müssen Sie Ports durch Öffnen der [Netzwerksicherheitsgruppe](/azure/virtual-machines/virtual-machines-windows-hero-role#open-port-80). 

Erforderliche Ports:

- 80 - wird für IIS erforderlich.
- 4022 - erforderlich, für das Remotedebuggen aus Visual Studio 2017 (finden Sie unter [-Remotedebugger – Portzuweisungen](../debugger/remote-debugger-port-assignments.md) ausführliche Informationen.
- 8172 – (Optional) erforderlich für Web Deploy, um die app aus Visual Studio bereitstellen.
- UDP 3702 - erkennungsport (Optional) ermöglicht es Ihnen, die **suchen** Schaltfläche beim Anfügen an den Remotedebugger in Visual Studio.

1. Um einen Port unter Windows Server zu öffnen, öffnen die **starten** Menü, suchen Sie nach **Windows-Firewall mit erweiterter Sicherheit**.

2. Wählen Sie dann **eingehende Regeln > neue Regel > Port**, und klicken Sie dann auf **Weiter**. (Wählen Sie für UDP 3702, **ausgehende Regeln** stattdessen.)

3. Klicken Sie unter **bestimmte lokale Ports**, geben Sie die Portnummer an, klicken Sie auf **Weiter**.

4. Klicken Sie auf **Verbindung zulassen**, klicken Sie auf **Weiter**.

5. Wählen Sie eine oder mehrere Netzwerktypen für den Port zu aktivieren, und klicken Sie auf **Weiter**.

    Ein Typ muss das Netzwerk beinhalten, mit dem der Remotecomputer verbunden ist.
6. Fügen Sie den Namen (z. B. **IIS**, **Web Deploy**, oder **Msvsmon**) für die eingehende Regel und auf **Fertig stellen**.

    Die neue Regel in der Liste eingehende oder ausgehende Regeln sollte angezeigt werden.

    Wenn Sie weitere Informationen zum Windows-Firewall konfigurieren möchten, finden Sie unter [der Windows-Firewall für Remotedebuggen konfigurieren](../debugger/configure-the-windows-firewall-for-remote-debugging.md).

3. Erstellen Sie zusätzliche Regeln für die anderen erforderlichen Ports.
