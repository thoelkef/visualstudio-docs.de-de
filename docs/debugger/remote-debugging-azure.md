---
title: Remote Debug ASP.NET Core unter IIS und Azure | Microsoft Docs
ms.custom: remotedebugging
ms.date: 05/21/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: a6c04b53-d1b9-4552-a8fd-3ed6f4902ce6
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- aspnet
- dotnetcore
- azure
ms.openlocfilehash: a4e03f9a369959a5736d7030a1dac885771d7984
ms.sourcegitcommit: 58052c29fc61c9a1ca55a64a63a7fdcde34668a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/04/2018
ms.locfileid: "34746766"
---
# <a name="remote-debug-aspnet-core-on-iis-in-azure-in-visual-studio-2017"></a>Remotedebuggen ASP.NET Core unter IIS in Azure in Visual Studio 2017

Dieses Handbuch erläutert das Einrichten und konfigurieren eine Visual Studio 2017 ASP.NET Core-app, auf IIS mithilfe von Azure bereitgestellt und von Visual Studio remote Debugger anfügen.

Die empfohlene Methode zum Remotedebuggen in Azure hängt von Ihrem Szenario ab:

* Zum Debuggen von ASP.NET Core in Azure App Service finden Sie unter [Debuggen von Azure-apps, die mit der Snapshot-Debugger](../debugger/debug-live-azure-applications.md). Dies ist die empfohlene Methode.
* Führen Sie die Schritte in diesem Thema zum Debuggen von ASP.NET Core in Azure App Service mithilfe der eher traditionelle Debugfunktionen (finden Sie im Abschnitt [Remote Debuggen in Azure App Service](#remote_debug_azure_app_service)).

    In diesem Szenario müssen Sie Ihre app aus Visual Studio in Azure bereitstellen, aber Sie müssen nicht manuell installieren oder Konfigurieren von IIS oder des Remotedebuggers (diese Komponenten sind mit gepunkteten Linien dargestellt), wie in der folgenden Abbildung dargestellt.

    ![Remotedebugger-Komponenten](../debugger/media/remote-debugger-azure-app-service.png "Remote_debugger_components")

* Führen Sie die Schritte in diesem Thema zum Debuggen von IIS auf einer Azure-VM (finden Sie im Abschnitt [Remote Debuggen auf einer Azure-VM](#remote_debug_azure_vm)). Dadurch können Sie eine benutzerdefinierte Konfiguration von IIS verwenden, aber die Schritte für Setup und Bereitstellung sind komplexer.

    Für eine Azure-VM müssen Sie Ihre app aus Visual Studio in Azure bereitstellen, und müssen Sie auch manuell installieren Sie die IIS-Rolle und den Remotedebugger wie in der folgenden Abbildung dargestellt.

    ![Remotedebugger-Komponenten](../debugger/media/remote-debugger-azure-vm.png "Remote_debugger_components")

* Zum Debuggen von ASP.NET Core auf Azure Service Fabric finden Sie unter [Debuggen eine Remoteanwendung Service Fabric](/azure/service-fabric/service-fabric-debugging-your-application#debug-a-remote-service-fabric-application).

> [!WARNING]
> Achten Sie darauf, dass Sie die Azure-Ressourcen zu löschen, die Sie erstellen, wenn Sie die Schritte in diesem Lernprogramm abgeschlossen haben. Auf diese Weise vermeiden Sie unnötige Gebühren anfallen.


### <a name="requirements"></a>Anforderungen

Debuggen zwischen zwei Computern über einen Proxy verbunden wird nicht unterstützt. Remotedebuggen über eine hohe Latenz oder niedriger Bandbreite, wie z. B. DFÜ, Internet oder über das Internet Ländern wird nicht empfohlen und möglicherweise fehl oder sehr langsam sein. Eine vollständige Liste der Anforderungen, finden Sie unter [Anforderungen](../debugger/remote-debugging.md#requirements_msvsmon).

## <a name="create-the-aspnet-core-application-on-the-visual-studio-2017-computer"></a>Erstellen Sie die ASP.NET Core-Anwendung auf dem Computer Visual Studio 2017 

1. Erstellen einer neuen ASP.NET Core-Anwendung. (Wählen Sie **Datei > Neu > Projekt**, und wählen Sie dann **Visual c# > Web > ASP.NET Core Web Application**).

    In der **ASP.NET Core** -Vorlagenabschnitt wählen **Webanwendung**.

2. Stellen Sie sicher, dass **ASP.NET Core 2.0** ausgewählt ist, **Docker-Unterstützung aktivieren** ist **nicht** ausgewählten und **Authentifizierung** auf festgelegt ist **Keine Authentifizierung**.

3. Nennen Sie das Projekt **MyASPApp** , und klicken Sie auf **OK** um die neue Projektmappe zu erstellen.

4. Öffnen Sie die Datei About.cshtml.cs, und legen Sie einen Haltepunkt der `OnGet` Methode (Öffnen Sie in älteren Vorlagen HomeController.cs stattdessen, und legen Sie den Haltepunkt der `About()` Methode).

## <a name="remote_debug_azure_app_service"></a> Remotedebuggen ASP.NET Core unter Azure App Service

In Visual Studio können Sie schnell veröffentlichen und Debuggen der app auf eine vollständig bereitgestellte Instanz von IIS. Allerdings ist die Konfiguration von IIS voreingestellt und kann nicht angepasst. Ausführlichere Anweisungen finden Sie unter [eine ASP.NET Core Web-app in Azure mithilfe von Visual Studio bereitstellen](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs). (Wenn Sie die Möglichkeit, IIS anpassen möchten, versuchen Sie es Debuggen auf einem [Azure-VM](#BKMK_azure_vm).) 

#### <a name="to-deploy-the-app-and-remote-debug-using-server-explorer"></a>Zur Bereitstellung der app und Remotedebuggen mit Server-Explorer

1. Klicken Sie in Visual Studio mit der rechten Maustaste des Projektknotens, und wählen Sie **veröffentlichen**.

    Wenn Sie Veröffentlichungsprofile zuvor konfiguriert haben die **veröffentlichen** Bereich wird angezeigt. Klicken Sie auf **neues Profil**.

1. Wählen Sie **Azure App Service** aus der **veröffentlichen** wählen Sie im Dialogfeld **neu erstellen**, und befolgen Sie die Anweisungen zum Veröffentlichen.

    Ausführliche Anweisungen finden Sie unter [eine ASP.NET Core Web-app in Azure mithilfe von Visual Studio bereitstellen](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs).

    ![Veröffentlichen in Azure App Service](../debugger/media/remotedbg_azure_app_service_profile.png)

1. Open **Server-Explorer** (**Ansicht** > **Server-Explorer**) mit der rechten Maustaste auf die App Service-Instanz, und wählen Sie **-Debuggeranfügen**.

1. Klicken Sie in der laufenden Anwendung ASP.NET auf den Link, um die **zu** Seite.

    Der Haltepunkt sollte in Visual Studio erreicht werden.

    Das ist alles! Die restlichen Schritte in diesem Thema gelten für das Remotedebuggen auf einer Azure-VM.

## <a name="remote_debug_azure_vm"></a> Remotedebuggen von ASP.NET Core auf einer Azure-VM

Erstellen ein Azure-VM für Windows Server und dann installieren, und Konfigurieren von IIS und die erforderlichen Softwarekomponenten. Dies dauert länger als die Bereitstellung in Azure App Service und setzt voraus, dass Sie die restlichen Schritte in diesem Lernprogramm ausführen.

Führen Sie zunächst die in beschriebenen Schritte [installieren und Ausführen von IIS](/azure/virtual-machines/windows/quick-create-portal).

Beim Öffnen von Port 80 in der Sicherheitsgruppe "Netzwerk" Öffnen Sie Port 4022 auch für den Remotedebugger. Auf diese Weise müssen Sie es später erneut zu öffnen.

### <a name="app-already-running-in-iis-on-the-azure-vm"></a>Die App in IIS bereits auf der Azure-VM ausgeführt?

Dieser Artikel enthält die Schritte zum Einrichten einer Standardkonfiguration von IIS unter WindowsServer und zum Bereitstellen der app aus Visual Studio. Diese Schritte sind enthalten, um sicherzustellen, dass der Server die erforderlichen Komponenten installiert, dass die app ordnungsgemäß ausgeführt werden kann und Sie bereit, remote zu debuggen sind.

* Wenn Ihre app in IIS ausgeführt wird und Sie nur den Remotedebugger herunterladen und starten Sie das Debuggen, wechseln zur möchten [herunterladen und installieren Sie die Remoteserver-Verwaltungstools für Windows Server](#BKMK_msvsmon).

* Wenn Sie Hilfe, um sicherzustellen, dass Ihre app bereitgestellt eingerichtet wird, und ordnungsgemäß in IIS ausgeführt, um Sie zu debuggen, führen Sie alle Schritte in diesem Thema.

### <a name="update-browser-security-settings-on-windows-server"></a>Aktualisieren von Browsersicherheitseinstellungen unter Windows Server

Wenn die verstärkte Sicherheitskonfiguration in Internet Explorer aktiviert ist (er ist standardmäßig aktiviert), müssen Sie einige Domänen hinzufügen, als vertrauenswürdigen Sites ermöglichen Ihnen, einige Web-Server-Komponenten herunterzuladen. Fügen Sie der vertrauenswürdigen Sites hinzu, durch das Aufrufen **Internetoptionen > Sicherheit > Vertrauenswürdige Sites > Sites**. Fügen Sie die folgenden Domänen hinzu.

- microsoft.com
- go.microsoft.com
- 0download.microsoft.com
- IIS.NET

Wenn Sie die Software heruntergeladen haben, erhalten Sie möglicherweise Anforderungen an die Berechtigung zum Laden von verschiedenen Website-Skripts und Ressourcen gewähren. Einige dieser Ressourcen sind nicht erforderlich, aber den Prozess zu vereinfachen, klicken Sie auf **hinzufügen** Aufforderung.

### <a name="install-aspnet-core-on-windows-server"></a>Installieren Sie ASP.NET Core unter WindowsServer

1. Installieren der [.NET Core Windows Server-Hosting](https://aka.ms/dotnetcore-2-windowshosting) Paket auf dem Hostsystem. Das Paket wird die .NET Core-Laufzeit, .NET Core-Bibliothek und ASP.NET Core-Modul installiert. Weitere ausführlichen Anweisungen finden Sie in [in IIS veröffentlichen](/aspnet/core/publishing/iis?tabs=aspnetcore2x#iis-configuration).

    > [!NOTE]
    > Wenn das System nicht über eine Internetverbindung verfügt, erhalten und installieren Sie die *[Microsoft Visual C++ 2015 Redistributable](https://www.microsoft.com/download/details.aspx?id=53840)* vor der Installation von .NET Core Windows Server-Hosting-Paket.

3. Das System neu starten (oder führen Sie **net Stop wurde/y** gefolgt von **Net start w3svc** über eine Eingabeaufforderung, um eine Änderung am System Pfad übernehmen).

## <a name="choose-a-deployment-option"></a>Wählen Sie eine Bereitstellungsoption

Wenn Sie Hilfe benötigen, auf die app unter IIS bereitzustellen, sollten Sie diese Optionen:

* Erstellen eine Datei mit veröffentlichungseinstellungen in IIS, und Importieren der Einstellungen in Visual Studio bereitstellen. In einigen Szenarien ist dies eine schnelle Möglichkeit zum Bereitstellen Ihrer app. Wenn Sie die Datei mit veröffentlichungseinstellungen erstellen, werden Berechtigungen automatisch in IIS festgelegt.

* Veröffentlichen in einen lokalen Ordner, und kopieren die Ausgabe durch eine bevorzugte Methode auf eine vorbereitete Anwendungsordners auf IIS bereitstellen.

## <a name="optional-deploy-using-a-publish-settings-file"></a>(Optional) Die Bereitstellung über eine Datei mit veröffentlichungseinstellungen

Verwenden Sie diese Option können Sie eine Datei mit veröffentlichungseinstellungen zu erstellen und importieren Sie es in Visual Studio.

> [!NOTE]
> Diese Bereitstellungsmethode verwendet Web Deploy. Wenn Sie Web Deploy manuell in Visual Studio zu konfigurieren, anstatt die Einstellungen importieren möchten, können Sie Web bereitstellen 3.6 statt Web bereitstellen 3.6 für Hosting-Server installieren. Jedoch, wenn Sie Web Deploy manuell konfigurieren, Sie müssen sicherstellen, dass ein app-Ordners auf dem Server mit den richtigen Werten und die Berechtigungen konfiguriert ist (siehe [ASP.NET-Website konfigurieren](#BKMK_deploy_asp_net)).

### <a name="install-and-configure-web-deploy-for-hosting-servers-on-windows-server"></a>Installieren und Konfigurieren von Web Deploy für Hosting-Server unter Windows Server

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/install-web-deploy-with-hosting-server.md)]

### <a name="create-the-publish-settings-file-in-iis-on-windows-server"></a>Erstellen Sie die Datei mit veröffentlichungseinstellungen in IIS unter Windows Server

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/create-publish-settings-iis.md)]

### <a name="import-the-publish-settings-in-visual-studio-and-deploy"></a>Die Einstellungen für die Veröffentlichung in Visual Studio importieren und bereitstellen

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/import-publish-settings-vs.md)]

Nachdem die app erfolgreich bereitgestellt hat, sollte er automatisch gestartet. Wenn die app aus Visual Studio nicht gestartet wird, starten Sie die app in IIS. Für ASP.NET Core, müssen Sie sicherstellen, dass der Anwendungspool für Feld der **DefaultAppPool** festgelegt ist, um **kein verwalteter Code**.

1. In der **Einstellungen** (Dialogfeld), aktivieren Sie Debuggen, indem Sie auf **Weiter**, wählen Sie eine **Debuggen** Konfiguration, und wählen Sie dann **entfernen weiterer Dateien am Ziel** unter der **-Datei veröffentlichen** Optionen.

    > [!NOTE]
    > Wenn Sie eine Releasekonfiguration auswählen, deaktivieren Sie Debuggen in der *"Web.config"* beim Veröffentlichen der Datei.

1. Klicken Sie auf **speichern** und veröffentlichen Sie die app erneut.

## <a name="optional-deploy-by-publishing-to-a-local-folder"></a>(Optional) Durch die Veröffentlichung in einen lokalen Ordner bereitstellen

Sie können diese Option verwenden, zum Bereitstellen Ihrer app, wenn Sie so kopieren Sie die app in IIS mithilfe von Powershell RoboCopy, oder Sie die Dateien manuell kopieren möchten.

### <a name="BKMK_deploy_asp_net"></a> Konfigurieren der ASP.NET-Website auf dem Windows Server-computer

Beim Importieren von veröffentlichungseinstellungen, Sie können diesen Abschnitt überspringen.

1. Öffnen Sie den **Internetinformationsdienste-Manager (IIS)** , und navigieren Sie zu **Websites**.

2. Klicken Sie mit der rechten Maustaste auf den Knoten **Standardwebsite** , und wählen Sie **Anwendung hinzufügen**aus.

3. Legen Sie die **Alias** Feld **MyASPApp** und das Feld "Anwendungspool" auf **kein verwalteter Code**. Legen Sie die **physischen Pfad** auf **C:\Publish** (in der Sie werden später Bereitstellen der ASP.NET-Projekt).

4. Mit den Standort im IIS-Manager ausgewählt haben, wählen Sie **Berechtigungen bearbeiten**, und stellen Sie sicher, diese IUSR, IIS_IUSRS oder der Benutzer, die für den Anwendungspool ein autorisierter Benutzer mit Berechtigungen für Lesen & ausführen wird konfiguriert.

    Wenn Sie einen dieser Benutzer mit Zugriff nicht angezeigt wird, wechseln Sie über die erforderlichen Schritte zum Hinzufügen des IUSR-Konto als Benutzer mit Berechtigungen für Lesen & ausführen.

### <a name="optional-publish-and-deploy-the-app-by-publishing-to-a-local-folder-from-visual-studio"></a>(Optional) Veröffentlichen und Bereitstellen der Anwendung in einen lokalen Ordner durch die Veröffentlichung aus Visual Studio

Wenn Sie Web Deploy nicht verwenden, müssen Sie veröffentlichen und Bereitstellen der app mit dem Dateisystem oder anderen Tools. Sie können durch Erstellen eines Pakets mit dem Dateisystem starten und das Paket manuell bereitstellen oder auch mit anderen Tools wie PowerShell oder RoboCopy mit XCopy. In diesem Abschnitt wird davon ausgegangen, dass Sie das Paket manuell kopieren, wenn Sie Web Deploy nicht verwenden werden.

[!INCLUDE [remote-debugger-deploy-app-local](../debugger/includes/remote-debugger-deploy-app-local.md)]

### <a name="BKMK_msvsmon"></a> Herunterladen Sie und installieren Sie die Remoteserver-Verwaltungstools für Windows Server

In diesem Lernprogramm verwenden wir 2017 von Visual Studio.

Wenn Sie die Seite zu öffnen, mit dem Remotedebugger Download Probleme haben, finden Sie unter [entsperren den Dateidownload](../debugger/remote-debugging.md#unblock_msvsmon) um Hilfe zu erhalten.

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]
  
### <a name="BKMK_setup"></a> Einrichten des Remotedebuggers unter Windows Server

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]

> [!NOTE]
> Wenn Sie benötigen Berechtigungen für zusätzliche Benutzer hinzufügen ändern den Authentifizierungsmodus oder Portnummer für den Remotedebugger, finden Sie unter [Konfigurieren des Remotedebuggers](../debugger/remote-debugging.md#configure_msvsmon).

### <a name="BKMK_attach"></a> Anfügen an die ASP.NET-Anwendung vom Visual Studio-Computer aus

1. Öffnen Sie auf dem Computer Visual Studio die Projektmappe, den Sie debuggen möchten (**MyASPApp** , wenn Sie die Schritte in diesem Artikel folgen).
2. Klicken Sie in Visual Studio auf **Debuggen > an den Prozess anhängen** (Strg + Alt + P).

    > [!TIP]
    > In Visual Studio 2017 können Sie erneut mit dem gleichen Prozess, die Sie zuvor mit angefügte Anfügen **Debuggen > an Prozess anfügen...** (Umschalt + Alt + P). 

3. Legen Sie auf das Feld "Qualifizierer"  **\<Name des Remotecomputers >: 4022**.
4. Klicken Sie auf **aktualisieren**.
    Im Fenster sollten einige Prozesse **Verfügbare Prozesse** angezeigt werden.

    Wenn alle Prozesse nicht angezeigt wird, versuchen Sie die IP-Adresse anstelle des remote-Computer (der Port ist erforderlich). Sie können `ipconfig` in einer Befehlszeile, um die IPv4-Adresse abzurufen.

    Wenn Sie verwenden möchten die **suchen** Schaltfläche, müssen Sie möglicherweise [Öffnen von UDP-Port 3702](#bkmk_openports) auf dem Server.

5. Aktivieren Sie  **Prozesse aller Benutzer anzeigen**.

6. Geben Sie den ersten Buchstaben des Namens eines Prozesses, schnell zu finden *dotnet.exe* (für ASP.NET Core).
   
   Für eine app ASP.NET Core der vorherige Name des Prozesses wurde *dnx.exe*.

    ![RemoteDBG_AttachToProcess](../debugger/media/remotedbg_attachtoprocess_aspnetcore.png "RemoteDBG_AttachToProcess")

7. Klicken Sie auf **Anfügen**aus.

8. Öffnen Sie die Website des Remotecomputers. Navigieren Sie in einem Browser auf **http://\<Remotecomputername >**.
    
    Es sollte die ASP.NET-Webseite angezeigt werden.
9. Klicken Sie in der laufenden Anwendung ASP.NET auf den Link, um die **zu** Seite.

    Der Haltepunkt sollte in Visual Studio erreicht werden.

### <a name="bkmk_openports"></a> Zur Fehlerbehebung: Öffnen Sie erforderlichen Ports auf Windows Server

In den meisten Installationen werden die erforderlichen Ports durch die Installation von ASP.NET und den Remotedebugger geöffnet. Wenn die Behandlung von Problemen bei der Bereitstellung werden Sie aus, und die app gehostet wird, hinter einer Firewalls, müssen Sie sicherstellen, dass die richtigen Ports geöffnet sind.

Auf einem virtuellen Azure-Computer müssen Sie Ports durch Öffnen der [Netzwerksicherheitsgruppe](/azure/virtual-machines/virtual-machines-windows-hero-role#open-port-80). 

Erforderliche Ports:

- 80 - wird für IIS erforderlich.
- 4022 - erforderlich, für das Remotedebuggen aus Visual Studio 2017 (finden Sie unter [-Remotedebugger – Portzuweisungen](../debugger/remote-debugger-port-assignments.md) für Weitere Informationen).
- UDP 3702 - erkennungsport (Optional) ermöglicht es Ihnen, die **suchen** Schaltfläche beim Anfügen an den Remotedebugger in Visual Studio.

Darüber hinaus sollte diese Ports bereits von der Installation von ASP.NET geöffnet werden:
- 8172 – (Optional) erforderlich für Web Deploy zum Bereitstellen der app aus Visual Studio

