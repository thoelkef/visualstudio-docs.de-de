---
title: Remote Debug ASP.NET Core unter IIS und Azure | Microsoft Docs
ms.custom: remotedebugging
ms.date: 08/14/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a6c04b53-d1b9-4552-a8fd-3ed6f4902ce6
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4e42513e431fd81a85d54a3e9784ebaa6cd26eb2
ms.sourcegitcommit: 38097344f3ff74ba7b03bcfa45910015ca6bc2be
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/11/2017
---
# <a name="remote-debug-aspnet-core-on-iis-and-azure-in-visual-studio-2017"></a>Remotedebuggen ASP.NET Core unter IIS und Azure in Visual Studio 2017
Sie können eine ASP.NET-Webanwendung auf einem Windows Server-Computer mit IIS bereitstellen und für das Remotedebuggen einrichten. Dieses Handbuch erläutert das Einrichten und konfigurieren eine Visual Studio 2017 ASP.NET Core-app, auf IIS mithilfe von Azure bereitgestellt und von Visual Studio remote Debugger anfügen.

> [!WARNING]
> Achten Sie darauf, dass Sie die Azure-Ressourcen zu löschen, die Sie erstellen, wenn Sie die Schritte in diesem Lernprogramm abgeschlossen haben. Auf diese Weise vermeiden Sie unnötige Gebühren anfallen.

In diesem Thema wird gezeigt, wie Sie:

* Remotedebuggen ASP.NET Core unter Azure App Service

* Remotedebuggen ASP.NET Core auf einer Azure-VM

Für Azure App Service müssen Sie Ihre app aus Visual Studio in Azure bereitstellen, aber Sie müssen nicht manuell installieren oder Konfigurieren von IIS oder des Remotedebuggers (diese Komponenten sind mit gepunkteten Linien dargestellt), wie in der folgenden Abbildung dargestellt.

![Remotedebugger-Komponenten](../debugger/media/remote-debugger-azure-app-service.png "Remote_debugger_components")

Für eine Azure-VM müssen Sie Ihre app aus Visual Studio in Azure bereitstellen, und müssen Sie auch manuell installieren Sie die IIS-Rolle und den Remotedebugger wie in der folgenden Abbildung dargestellt.

![Remotedebugger-Komponenten](../debugger/media/remote-debugger-azure-vm.png "Remote_debugger_components")

> [!NOTE]
> Zum Debuggen von ASP.NET Core auf Azure Service Fabric finden Sie unter [Debuggen eine Remoteanwendung Service Fabric](/azure/service-fabric/service-fabric-debugging-your-application#debug-a-remote-service-fabric-application).

### <a name="requirements"></a>Anforderungen

Debuggen zwischen zwei Computern über einen Proxy verbunden wird nicht unterstützt. Remotedebuggen über eine hohe Latenz oder niedriger Bandbreite, wie z. B. DFÜ, Internet oder über das Internet Ländern wird nicht empfohlen und möglicherweise fehl oder sehr langsam sein. Eine vollständige Liste der Anforderungen, finden Sie unter [Anforderungen](../debugger/remote-debugging.md#requirements_msvsmon).

## <a name="create-the-aspnet-core-application-on-the-visual-studio-2017-computer"></a>Erstellen Sie die ASP.NET Core-Anwendung auf dem Computer Visual Studio 2017 

1. Erstellen einer neuen ASP.NET Core-Anwendung. (Wählen Sie **Datei > Neu > Projekt**, und wählen Sie dann **Visual c# > Web > ASP.NET Core Web Application**).

    In der **ASP.NET Core** -Vorlagenabschnitt wählen **Webanwendung**.

2. Stellen Sie sicher, dass **ASP.NET Core 2.0** ausgewählt ist, **Docker-Unterstützung aktivieren** ist **nicht** ausgewählten und **Authentifizierung** auf festgelegt ist **Keine Authentifizierung**.

3. Nennen Sie das Projekt **MyASPApp** , und klicken Sie auf **OK** um die neue Projektmappe zu erstellen.

4. Öffnen Sie die Datei About.cshtml.cs, und legen Sie einen Haltepunkt der `OnGet` Methode (Öffnen Sie in älteren Vorlagen HomeController.cs stattdessen, und legen Sie den Haltepunkt der `About()` Methode).

## <a name="remote-debug-aspnet-core-on-an-azure-app-service"></a>Remotedebuggen ASP.NET Core unter Azure App Service

In Visual Studio können Sie schnell veröffentlichen und Debuggen der app auf eine vollständig bereitgestellte Instanz von IIS. Allerdings ist die Konfiguration von IIS voreingestellt und kann nicht angepasst. Ausführliche Anweisungen finden Sie unter [eine ASP.NET Core Web-app in Azure mithilfe von Visual Studio bereitstellen](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs). (Wenn Sie die Möglichkeit, IIS anpassen möchten, versuchen Sie es Debuggen auf einem [Azure-VM](#BKMK_azure_vm).) 

#### <a name="to-deploy-the-app-and-remote-debug"></a>Zur Bereitstellung der app und das Remotedebuggen

1. Klicken Sie in Visual Studio mit der rechten Maustaste des Projektknotens, und wählen Sie **veröffentlichen**.

2. Wählen Sie **Microsoft Azure App Service** aus der **veröffentlichen** wählen Sie im Dialogfeld **neu erstellen**, und befolgen Sie die Anweisungen zum Veröffentlichen.

    Ausführliche Anweisungen finden Sie unter [eine ASP.NET Core Web-app in Azure mithilfe von Visual Studio bereitstellen](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs).

3. In **Server-Explorer**mit der rechten Maustaste auf die App Service-Instanz, und wählen Sie **Debugger anfügen**.

4. Klicken Sie in der laufenden Anwendung ASP.NET auf den Link, um die **zu** Seite.

    Der Haltepunkt sollte in Visual Studio erreicht werden.

    Das ist alles! Die restlichen Schritte in diesem Thema gelten für das Remotedebuggen auf einer Azure-VM.

## <a name="BKMK_azure_vm"></a>Remotedebuggen von ASP.NET Core auf einer Azure-VM

Erstellen ein Azure-VM für Windows Server und dann installieren, und Konfigurieren von IIS und die erforderlichen Softwarekomponenten. Dies dauert länger als die Bereitstellung in Azure App Service und setzt voraus, dass Sie die restlichen Schritte in diesem Lernprogramm ausführen.

Führen Sie zunächst die in beschriebenen Schritte [installieren und Ausführen von IIS](/azure/virtual-machines/virtual-machines-windows-hero-role).

Beim Öffnen von Port 80 in der Sicherheitsgruppe "Netzwerk" Öffnen Sie Port 4022 auch für den Remotedebugger. Auf diese Weise müssen Sie es später erneut zu öffnen.

### <a name="update-browser-security-settings-on-windows-server"></a>Aktualisieren von Browsersicherheitseinstellungen unter Windows Server

Je nach Ihrer Browsersicherheitseinstellungen kann es Speicherzeit Sie Ihrem Browser die folgenden vertrauenswürdigen Sites hinzugefügt werden, damit Sie problemlos in diesem Lernprogramm beschriebene Software herunterladen können. Möglicherweise müssen Sie den Zugriff auf diese Websites:

- "Microsoft.com"
- go.microsoft.com
- 0download.microsoft.com
- VisualStudio

Wenn Sie Internet Explorer verwenden, können Sie den vertrauenswürdigen Sites hinzufügen, navigieren Sie zu **Internetoptionen > Sicherheit > Vertrauenswürdige Sites > Sites**. Diese Schritte sind für andere Browser unterschiedlich. (Wenn Sie eine ältere Version des Remotedebuggers von my.visualstudio.com herunterladen müssen, sind einige zusätzliche vertrauenswürdige Websites erforderlich, sich anzumelden.)

Wenn Sie die Software heruntergeladen haben, erhalten Sie möglicherweise Anforderungen an die Berechtigung zum Laden von verschiedenen Website-Skripts und Ressourcen gewähren. In den meisten Fällen sind die folgenden zusätzlichen Ressourcen beim Installieren der Clientsoftware nicht erforderlich.

### <a name="install-aspnet-core-on-windows-server"></a>Installieren Sie ASP.NET Core unter WindowsServer

1. Installieren der [.NET Core Windows Server-Hosting](https://aka.ms/dotnetcore-2-windowshosting) Paket auf dem Hostsystem. Das Paket wird die .NET Core-Laufzeit, .NET Core-Bibliothek und ASP.NET Core-Modul installiert. Weitere ausführlichen Anweisungen finden Sie in [in IIS veröffentlichen](/aspnet/core/publishing/iis?tabs=aspnetcore2x#iis-configuration).

    > [!NOTE]
    > Wenn das System nicht über eine Internetverbindung verfügt, erhalten und installieren Sie die  *[Microsoft Visual C++ 2015 Redistributable](https://www.microsoft.com/download/details.aspx?id=53840)*  vor der Installation von .NET Core Windows Server-Hosting-Paket.

3. Das System neu starten (oder führen Sie **net Stop wurde/y** gefolgt von **Net start w3svc** über eine Eingabeaufforderung, um eine Änderung am System Pfad übernehmen).

### <a name="BKMK_install_webdeploy"></a>(Optional) Installieren Sie Web Deploy 3.6 unter WindowsServer

[!INCLUDE [remote-debugger-install-web-deploy](../debugger/includes/remote-debugger-install-web-deploy.md)]

### <a name="BKMK_deploy_asp_net"></a>Konfigurieren Sie ASP.NET-Website, auf dem Windows Server-computer

1. Öffnen Sie den **Internetinformationsdienste-Manager (IIS)** , und navigieren Sie zu **Websites**.

2. Klicken Sie mit der rechten Maustaste auf den Knoten **Standardwebsite** , und wählen Sie **Anwendung hinzufügen**aus.

3. Legen Sie die **Alias** Feld **MyASPApp** und das Feld "Anwendungspool" auf **kein verwalteter Code**. Legen Sie die **physischen Pfad** auf **C:\Publish** (in der Sie werden später Bereitstellen der ASP.NET-Projekt).

4. Mit den Standort im IIS-Manager ausgewählt haben, wählen Sie **Berechtigungen bearbeiten**, und stellen Sie sicher, diese IUSR, IIS_IUSRS oder der Benutzer, die für den Anwendungspool ein autorisierter Benutzer mit Berechtigungen für Lesen & ausführen wird konfiguriert.

    Wenn Sie einen dieser Benutzer mit Zugriff nicht angezeigt wird, wechseln Sie über die erforderlichen Schritte zum Hinzufügen des IUSR-Konto als Benutzer mit Berechtigungen für Lesen & ausführen.

### <a name="bkmk_webdeploy"></a>(Optional) Veröffentlichen und Bereitstellen der app mithilfe von Web Deploy von Visual Studio

Wenn Sie Web Deploy, mit dem Webplattform-Installer installiert haben, können Sie die app direkt in Visual Studio bereitstellen.

1. Starten Sie Visual Studio mit erhöhten Rechten aus, und öffnen Sie das Projekt erneut.

    Dies kann erforderlich sein, zum Bereitstellen Ihrer app mithilfe von Web Deploy.

2. Klicken Sie im **Projektmappen-Explorer**mit der rechten Maustaste auf den Projektknoten, und wählen Sie **Veröffentlichen**aus.

3. Für **Veröffentlichungsziel auswählen**Option **Microsoft Azure Virtual Machines** , und klicken Sie auf **veröffentlichen**.

    ![RemoteDBG_Publish_IISl](../debugger/media/remotedbg_azure_vm_profile.png "RemoteDBG_Publish_IIS")

4. Wählen Sie im Dialogfeld Azure-VM an, die Sie zuvor erstellt haben.

4. Geben Sie die Korrektur Konfigurationsparameter für Ihr Azure-VM "und" IIS-Setup aus.

    ![RemoteDBG_Publish_WebDeployl](../debugger/media/remotedbg_iis_webdeploy_config.png "RemoteDBG_Publish_WebDeploy")

    Wenn Sie ein Hostnamen nicht behoben wird, wenn Sie versuchen, überprüfen Sie in den nächsten Schritten, in der **Server** Text im Feld, und versuchen Sie die IP-Adresse. Stellen Sie sicher, dass die Verwendung von Port 80 in der **Server** Text ein, und stellen Sie sicher, dass Port 80 in der Firewall geöffnet ist.

6. Klicken Sie auf **Weiter**, wählen Sie eine **Debuggen** Konfiguration, und wählen Sie **entfernen weiterer Dateien am Ziel** unter der **-Datei veröffentlichen** Optionen.

5. Klicken Sie auf **Prev**, und wählen Sie dann **Validate**. Wenn dem Einrichten der Verbindung überprüft hat, können Sie versuchen, veröffentlichen.

6. Klicken Sie auf **veröffentlichen** zum Veröffentlichen der app.

    Die Registerkarte "Ausgabe" erfahren Sie, wenn die Publishing ist erfolgreich, und öffnen Sie Ihr Browser wird die app.

    Wenn Sie einen Web Deploy erwähnen Fehler erhalten, überprüfen Sie die Installationsschritte Web Deploy und stellen Sie sicher, dass die [richtigen Ports geöffnet sind,](#bkmk_openports) werden auf dem Server.

    Wenn die app erfolgreich bereitgestellt, aber nicht ordnungsgemäß ausgeführt werden kann, überprüfen Sie, dass IIS und Visual Studio-Projekt die gleiche Version von ASP.NET verwenden. Wenn also nicht das Problem möglicherweise ein Problem mit der IIS-Konfiguration oder Konfiguration Ihrer Website. Öffnen Sie auf dem Windows-Server die Website aus IIS finden Sie spezifischere Fehlermeldungen, und überprüfen Sie dann erneut bereits beschriebenen Schritte.

### <a name="optional-publish-and-deploy-the-app-by-publishing-to-a-local-folder-from-visual-studio"></a>(Optional) Veröffentlichen und Bereitstellen der Anwendung in einen lokalen Ordner durch die Veröffentlichung aus Visual Studio

Wenn Sie Web Deploy nicht verwenden, müssen Sie veröffentlichen und Bereitstellen der app mit dem Dateisystem oder anderen Tools. Sie können durch Erstellen eines Pakets mit dem Dateisystem starten und das Paket manuell bereitstellen oder auch mit anderen Tools wie PowerShell oder RoboCopy mit XCopy. In diesem Abschnitt wird davon ausgegangen, dass Sie das Paket manuell kopieren, wenn Sie Web Deploy nicht verwenden werden.

[!INCLUDE [remote-debugger-deploy-app-local](../debugger/includes/remote-debugger-deploy-app-local.md)]

### <a name="BKMK_msvsmon"></a>Herunterladen Sie und installieren Sie der Remotetools unter WindowsServer

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]
  
### <a name="BKMK_setup"></a>Einrichten des Remotedebuggers unter Windows Server

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]

> [!NOTE]
> Wenn Sie benötigen Berechtigungen für zusätzliche Benutzer hinzufügen ändern den Authentifizierungsmodus oder Portnummer für den Remotedebugger, finden Sie unter [Konfigurieren des Remotedebuggers](../debugger/remote-debugging.md#configure_msvsmon).

### <a name="BKMK_attach"></a> Anfügen an die ASP.NET-Anwendung vom Visual Studio-Computer aus

1. Öffnen Sie auf dem Visual Studio-Computer die **MyASPApp** Lösung.
2. Klicken Sie in Visual Studio auf **Debuggen > an den Prozess anhängen** (Strg + Alt + P).

    > [!TIP]
    > In Visual Studio 2017 können Sie erneut mit dem gleichen Prozess, die Sie zuvor mit angefügte Anfügen **Debuggen > an Prozess anfügen...** (Umschalt + Alt + P). 

3. Legen Sie auf das Feld "Qualifizierer"  **\<Name des Remotecomputers >: 4022**.
4. Klicken Sie auf **aktualisieren**.
    Im Fenster sollten einige Prozesse **Verfügbare Prozesse** angezeigt werden.

    Wenn alle Prozesse nicht angezeigt wird, versuchen Sie die IP-Adresse anstelle des remote-Computer (der Port ist erforderlich). Sie können `ipconfig` in einer Befehlszeile, um die IPv4-Adresse abzurufen.

    Wenn Sie verwenden möchten die **suchen** Schaltfläche, müssen Sie möglicherweise [Öffnen von UDP-Port 3702](#bkmk_openports) auf dem Server.

5. Aktivieren Sie  **Prozesse aller Benutzer anzeigen**.
6. Geben Sie den ersten Buchstaben des Namens eines Prozesses, schnell zu finden **dotnet.exe** (für ASP.NET Core).
    >Hinweis: Der vorherige Name des Prozesses wurde für eine app ASP.NET Core dnx.exe.

    ![RemoteDBG_AttachToProcess](../debugger/media/remotedbg_attachtoprocess_aspnetcore.png "RemoteDBG_AttachToProcess")

7. Klicken Sie auf **Anfügen**aus.

8. Öffnen Sie die Website des Remotecomputers. Navigieren Sie in einem Browser auf **http://\<Remotecomputername >**.
    
    Es sollte die ASP.NET-Webseite angezeigt werden.
9. Klicken Sie in der laufenden Anwendung ASP.NET auf den Link, um die **zu** Seite.

    Der Haltepunkt sollte in Visual Studio erreicht werden.

### <a name="bkmk_openports"></a>Zur Fehlerbehebung: Öffnen Sie erforderlichen Ports auf Windows Server

In den meisten Installationen werden die erforderlichen Ports durch die Installation von ASP.NET und den Remotedebugger geöffnet. Wenn die Behandlung von Problemen bei der Bereitstellung werden Sie aus, und die app gehostet wird, hinter einer Firewalls, müssen Sie sicherstellen, dass die richtigen Ports geöffnet sind.

Auf einem virtuellen Azure-Computer müssen Sie Ports durch Öffnen der [Netzwerksicherheitsgruppe](/azure/virtual-machines/virtual-machines-windows-hero-role#open-port-80). 

Erforderliche Ports:

- 80 - wird für IIS erforderlich.
- 4022 - erforderlich, für das Remotedebuggen aus Visual Studio 2017 (finden Sie unter [-Remotedebugger – Portzuweisungen](../debugger/remote-debugger-port-assignments.md) für Weitere Informationen).
- UDP 3702 - erkennungsport (Optional) ermöglicht es Ihnen, die **suchen** Schaltfläche beim Anfügen an den Remotedebugger in Visual Studio.

Darüber hinaus sollte diese Ports bereits von der Installation von ASP.NET geöffnet werden:
- 8172 – (Optional) erforderlich für Web Deploy zum Bereitstellen der app aus Visual Studio

