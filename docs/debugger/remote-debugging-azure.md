---
title: Remotedebuggen für ASP.NET Core auf IIS und Azure | Microsoft-Dokumentation
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
ms.openlocfilehash: cc889accc116fb2115ae56155a190ed6ea2d3fc0
ms.sourcegitcommit: c57ae28181ffe14a30731736661bf59c3eff1211
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/11/2018
ms.locfileid: "38797851"
---
# <a name="remote-debug-aspnet-core-on-iis-in-azure-in-visual-studio-2017"></a>Remotedebuggen von ASP.NET Core auf IIS in Azure in Visual Studio 2017

Dieses Handbuch wird erläutert, wie einrichten und Konfigurieren einer Visual Studio 2017 ASP.NET Core-app, in IIS mithilfe von Azure bereitstellen und fügen Sie den Remotedebugger in Visual Studio.

Die empfohlene Methode zum Remotedebuggen in Azure hängt vom Szenario ab:

* Zum Debuggen von ASP.NET Core in Azure App Service finden Sie unter [Debuggen von Azure-apps, die mit dem Momentaufnahmedebugger](../debugger/debug-live-azure-applications.md). Dies ist die empfohlene Methode.
* Führen Sie die Schritte in diesem Thema zum Debuggen von ASP.NET Core in Azure App Service mithilfe der eher traditionelle Debugfunktionen (finden Sie im Abschnitt [Remotedebuggen in Azure App Service](#remote_debug_azure_app_service)).

    Klicken Sie in diesem Szenario müssen Sie Ihre app aus Visual Studio in Azure bereitstellen, aber Sie müssen nicht manuell installieren oder Konfigurieren von IIS oder der Remotedebugger (diese Komponenten mit einer gepunkteten Linien dargestellt werden), wie in der folgenden Abbildung dargestellt.

    ![Remote Debugger-Komponenten](../debugger/media/remote-debugger-azure-app-service.png "Remote_debugger_components")

* Führen Sie die Schritte in diesem Thema zum Debuggen von IIS auf einer Azure-VM (finden Sie im Abschnitt [Remote Debuggen auf einer Azure-VM](#remote_debug_azure_vm)). Dadurch können Sie eine angepasste Konfiguration von IIS verwenden, aber die Schritte für Einrichtung und Bereitstellung sind komplizierter.

    Für eine Azure-VM müssen Sie Ihre app aus Visual Studio in Azure bereitstellen, und darüber hinaus müssen die IIS-Rolle und dem Remotedebugger manuell installieren wie in der folgenden Abbildung dargestellt.

    ![Remote Debugger-Komponenten](../debugger/media/remote-debugger-azure-vm.png "Remote_debugger_components")

* Zum Debuggen von ASP.NET Core in Azure Service Fabric finden Sie unter [Debuggen eine Service Fabric-Remoteanwendung](/azure/service-fabric/service-fabric-debugging-your-application#debug-a-remote-service-fabric-application).

> [!WARNING]
> Achten Sie darauf, dass Sie die Azure-Ressourcen zu löschen, die Sie erstellen, wenn Sie die Schritte in diesem Lernprogramm abgeschlossen haben. Auf diese Weise vermeiden Sie unnötige Kosten.


### <a name="requirements"></a>Anforderungen

Debuggen zwischen zwei Computern über einen Proxy verbunden sind, wird nicht unterstützt. Debuggen über eine hohe Latenz oder niedriger Bandbreite, wie z. B. DFÜ, Internet oder über das Internet in Ländern wird nicht empfohlen und möglicherweise fehl oder unzumutbar langsam werden. Eine vollständige Liste der Anforderungen, finden Sie unter [Anforderungen](../debugger/remote-debugging.md#requirements_msvsmon).

## <a name="create-the-aspnet-core-application-on-the-visual-studio-2017-computer"></a>Erstellen von ASP.NET Core-Anwendung auf dem Visual Studio 2017-computer 

1. Erstellen Sie eine neue ASP.NET Core-Anwendung. (Wählen Sie **Datei > Neu > Projekt**, und wählen Sie dann **Visual c# > Web > ASP.NET Core-Webanwendung**).

    In der **ASP.NET Core** -Vorlagenabschnitt wählen **Webanwendung**.

2. Stellen Sie sicher, dass **ASP.NET Core 2.0** ausgewählt ist, **Docker-Unterstützung aktivieren** ist **nicht** ausgewählten und **Authentifizierung** auf festgelegt ist **Keine Authentifizierung**.

3. Nennen Sie das Projekt **MyASPApp** , und klicken Sie auf **OK** um die neue Projektmappe zu erstellen.

4. Öffnen Sie die Datei About.cshtml.cs und Festlegen eines Haltepunkts in der `OnGet` Methode (in älteren Vorlagen, stattdessen "HomeController.cs" öffnen, und legen Sie den Haltepunkt der `About()` Methode).

## <a name="remote_debug_azure_app_service"></a> Remotedebuggen von ASP.NET Core in Azure App Service

In Visual Studio können Sie schnell veröffentlichen und Debuggen Ihrer app auf eine vollständig bereitgestellte Instanz von IIS. Allerdings der IIS-Konfiguration ist voreingestellt, und es kann nicht angepasst werden. Ausführlichere Anweisungen finden Sie unter [bereitstellen eine ASP.NET Core-Web-app in Azure mithilfe von Visual Studio](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs). (Wenn Sie die Möglichkeit zum Anpassen von IIS benötigen, versuchen Sie es Debuggen auf einem [Azure-VM](#remote_debug_azure_vm).) 

#### <a name="to-deploy-the-app-and-remote-debug-using-server-explorer"></a>Zum Bereitstellen der app und Remotedebuggen mit Server-Explorer

1. Klicken Sie in Visual Studio mit der rechten Maustaste des Projektknotens, und wählen Sie **veröffentlichen**.

    Wenn Sie Veröffentlichungsprofile, zuvor konfiguriert haben die **veröffentlichen** angezeigt. Klicken Sie auf **neues Profil**.

1. Wählen Sie **Azure App Service** aus der **veröffentlichen** wählen Sie im Dialogfeld **neu erstellen**, und befolgen Sie die Anweisungen zum Veröffentlichen.

    Ausführliche Anweisungen finden Sie unter [bereitstellen eine ASP.NET Core-Web-app in Azure mithilfe von Visual Studio](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs).

    ![Veröffentlichen in Azure App Service](../debugger/media/remotedbg_azure_app_service_profile.png)

1. Open **Server-Explorer** (**Ansicht** > **Server-Explorer**) mit der rechten Maustaste auf die App Service-Instanz, und wählen Sie **-Debuggeranfügen**.

1. Klicken Sie in der laufenden Anwendung ASP.NET auf den Link, um die **zu** Seite.

    Der Haltepunkt sollte in Visual Studio erreicht werden.

    Das ist alles! Die restlichen Schritte in diesem Thema gelten für die remote-Debuggen auf einer Azure-VM.

## <a name="remote_debug_azure_vm"></a> Remotedebuggen von ASP.NET Core in Azure-VMs

Sie können erstellen ein Azure-VM für Windows Server und dann installieren und Konfigurieren von IIS und die erforderlichen Softwarekomponenten. Dies dauert länger als eine Bereitstellung in Azure App Service und erfordert, dass Sie die restlichen Schritte in diesem Tutorial ausführen.

Führen Sie zunächst die Schritte unter [installieren und Ausführen von IIS](/azure/virtual-machines/windows/quick-create-portal).

Wenn Sie Port 80 in der Netzwerksicherheitsgruppe öffnen, müssen öffnen Sie Port 4022 auch, für den Remotedebugger. Auf diese Weise müssen Sie es später noch Mal zu öffnen.

### <a name="app-already-running-in-iis-on-the-azure-vm"></a>Die App bereits in IIS auf virtuellen Azure-Computer ausgeführt?

Dieser Artikel enthält Schritte zum Einrichten einer Standardkonfiguration von IIS unter Windows Server und das Bereitstellen der app aus Visual Studio. Diese Schritte sind enthalten, um sicherzustellen, dass der Server verfügt über die erforderlichen Komponenten installiert, die, dass die app ordnungsgemäß ausgeführt werden kann und Sie bereit, remote zu debuggen sind.

* Wenn Ihre app in IIS ausgeführt wird und Sie wollen den Remotedebugger herunterladen und mit dem Debuggen beginnen, navigieren zu [herunterladen und installieren Sie die Remoteserver-Verwaltungstools unter Windows Server](#BKMK_msvsmon).

* Wenn Sie Hilfe, um sicherzustellen, dass Ihre app bereitgestellt eingerichtet wurde, anzeigen möchten und ordnungsgemäß in IIS ausgeführt, damit Sie debuggen können, befolgen alle Schritte in diesem Thema.

### <a name="update-browser-security-settings-on-windows-server"></a>Browser-Sicherheitseinstellungen auf Windows Server aktualisieren

Wenn die verstärkte Sicherheitskonfiguration in Internet Explorer aktiviert ist (er ist standardmäßig aktiviert), müssen Sie einige Domänen als vertrauenswürdige Sites, um einige der Web-Server-Komponenten herunterladen können hinzufügen. Der vertrauenswürdigen Sites hinzufügen, indem Sie zu **Internetoptionen > Sicherheit > Vertrauenswürdige Sites > Websites**. Fügen Sie den folgenden Domänen hinzu.

- microsoft.com
- go.microsoft.com
- 0download.microsoft.com
- IIS.NET

Wenn Sie die Software herunterladen, erhalten Sie möglicherweise Anforderungen an die Berechtigung zum Laden von verschiedenen Website-Skripts und Ressourcen zu erteilen. Einige dieser Ressourcen sind nicht erforderlich, jedoch zur Vereinfachung des Prozesses, klicken Sie auf **hinzufügen** Aufforderung.

### <a name="install-aspnet-core-on-windows-server"></a>Installieren von ASP.NET Core unter WindowsServer

1. Installieren Sie die [.NET Core Windows Server Hosting](https://aka.ms/dotnetcore-2-windowshosting) Paket auf dem Hostsystem. Das Paket installiert die .NET Core-Runtime, .NET Core-Bibliothek und ASP.NET Core-Modul. Weitere ausführlichen Anweisungen finden Sie [Publishing to IIS](/aspnet/core/publishing/iis?tabs=aspnetcore2x#iis-configuration).

    > [!NOTE]
    > Wenn das System nicht über eine Internetverbindung verfügt, beziehen und Installieren der *[Microsoft Visual C++ 2015 Redistributable](https://www.microsoft.com/download/details.aspx?id=53840)* vor der Installation des .NET Core Windows Server Hosting-Pakets.

3. Das System neu starten (oder führen Sie **net Stop was/y** gefolgt von **Net start w3svc** über eine Eingabeaufforderung, um eine Änderung an den Systempfad zu übernehmen).

## <a name="choose-a-deployment-option"></a>Wählen Sie eine Bereitstellungsoption

Wenn Sie Hilfe benötigen, um die app in IIS bereitzustellen, sollten Sie diese Optionen:

* Erstellen eine Datei mit veröffentlichungseinstellungen in IIS, und importieren die Einstellungen in Visual Studio bereitstellen. In einigen Szenarien ist dies eine schnelle Möglichkeit zum Bereitstellen Ihrer app. Wenn Sie die Datei mit veröffentlichungseinstellungen erstellen, werden Berechtigungen automatisch in IIS festgelegt.

* Veröffentlichen in einen lokalen Ordner, und Kopieren der Ausgabe von einer bevorzugten Methode in einem vorbereiteten app-Ordner auf IIS bereitstellen.

## <a name="optional-deploy-using-a-publish-settings-file"></a>(Optional) Bereitstellen Sie über eine Datei mit veröffentlichungseinstellungen

Verwenden Sie diese Option erstellen Sie eine Datei mit veröffentlichungseinstellungen aus, und klicken Sie in Visual Studio importieren.

> [!NOTE]
> Diese Methode der Bereitstellung wird die Web Deploy verwendet. Wenn Sie Web Deploy manuell in Visual Studio zu konfigurieren, anstatt die Einstellungen importieren möchten, können Sie Web bereitstellen 3.6 anstelle von Web-bereitstellen-3.6 für Hostserver installieren. Jedoch, wenn Sie Web Deploy manuell konfigurieren, Sie müssen sicherstellen, dass ein app-Ordner auf dem Server mit den richtigen Werten und die Berechtigungen konfiguriert ist (siehe [ASP.NET-Website konfigurieren](#BKMK_deploy_asp_net)).

### <a name="install-and-configure-web-deploy-for-hosting-servers-on-windows-server"></a>Installieren und Konfigurieren von Web Deploy für Hostserver unter Windows Server

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/install-web-deploy-with-hosting-server.md)]

### <a name="create-the-publish-settings-file-in-iis-on-windows-server"></a>Erstellen Sie die Datei mit veröffentlichungseinstellungen in IIS unter Windows Server

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/create-publish-settings-iis.md)]

### <a name="import-the-publish-settings-in-visual-studio-and-deploy"></a>Die Einstellungen für die Veröffentlichung in Visual Studio importieren und bereitstellen

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/import-publish-settings-vs.md)]

Nachdem die app erfolgreich bereitgestellt wurde, sollten sie automatisch gestartet. Wenn die app aus Visual Studio nicht gestartet wird, starten Sie die app in IIS. Für ASP.NET Core, müssen Sie sicherstellen, dass der Anwendungspool für Feld der **DefaultAppPool** nastaven NA hodnotu **kein verwalteter Code**.

1. In der **Einstellungen** (Dialogfeld), aktivieren Sie Debuggen, indem Sie auf **Weiter**, wählen Sie eine **Debuggen** Konfiguration, und wählen Sie dann **entfernen weiterer Dateien am Ziel** unter der **-Datei veröffentlichen** Optionen.

    > [!NOTE]
    > Wenn Sie eine Releasekonfiguration auswählen, deaktivieren Sie Debuggen in der *"Web.config"* -Datei, wenn Sie veröffentlichen.

1. Klicken Sie auf **speichern** , und klicken Sie dann die app erneut veröffentlichen.

## <a name="optional-deploy-by-publishing-to-a-local-folder"></a>(Optional) Durch die Veröffentlichung in einen lokalen Ordner bereitstellen

Sie können diese Option verwenden, um Ihre app bereitzustellen, wenn Sie die app in IIS mithilfe von Powershell RoboCopy kopieren möchten, oder Sie die Dateien manuell kopieren möchten.

### <a name="BKMK_deploy_asp_net"></a> Konfigurieren der ASP.NET-Website auf dem Windows Server-computer

Beim Importieren von veröffentlichungseinstellungen, können Sie diesen Abschnitt überspringen.

1. Öffnen Sie den **Internetinformationsdienste-Manager (IIS)** , und navigieren Sie zu **Websites**.

2. Klicken Sie mit der rechten Maustaste auf den Knoten **Standardwebsite** , und wählen Sie **Anwendung hinzufügen**aus.

3. Legen Sie die **Alias** Feld **MyASPApp** und das Feld "Anwendungspool" auf **kein verwalteter Code**. Legen Sie die **physischer Pfad** zu **C:\Publish** (wird später Bereitstellungsszenario ASP.NET-Projekt).

4. Wählen Sie den Standort ausgewählt im IIS-Manager, **Berechtigungen bearbeiten**, und stellen Sie sicher, diese IUSR, IIS_IUSRS oder der Benutzer, die für den Anwendungspool ein autorisierter Benutzer mit Berechtigungen für Lesen & ausführen wird konfiguriert.

    Wenn Sie einen dieser Benutzer mit Zugriff nicht angezeigt wird, wechseln Sie über die Schritte zum Hinzufügen des IUSR-Konto als Benutzer mit Berechtigungen für Lesen & ausführen.

### <a name="optional-publish-and-deploy-the-app-by-publishing-to-a-local-folder-from-visual-studio"></a>(Optional) Veröffentlichen und Bereitstellen der app in einen lokalen Ordner durch die Veröffentlichung von Visual Studio

Wenn Sie Web Deploy nicht verwenden, müssen Sie veröffentlichen und Bereitstellen der app, die über das Dateisystem oder andere Tools. Sie können zunächst erstellen Sie ein Paket mit dem Dateisystem, und klicken Sie dann entweder das Paket entweder manuell oder mit anderen Tools wie XCopy, RoboCopy oder PowerShell. In diesem Abschnitt wird davon ausgegangen, dass Sie das Paket manuell kopieren, wenn Sie Web Deploy nicht verwenden werden.

[!INCLUDE [remote-debugger-deploy-app-local](../debugger/includes/remote-debugger-deploy-app-local.md)]

### <a name="BKMK_msvsmon"></a> Herunterladen Sie und installieren Sie die Remoteserver-Verwaltungstools unter Windows Server

In diesem Tutorial verwenden wir Visual Studio 2017.

Wenn Sie Probleme beim Öffnen der Seite mit dem Remotedebugger Download haben, finden Sie unter [entsperren Sie den Dateidownload](../debugger/remote-debugging.md#unblock_msvsmon) um Hilfe zu erhalten.

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]
  
### <a name="BKMK_setup"></a> Richten Sie den Remotedebugger unter Windows Server

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]

> [!NOTE]
> Wenn Sie zum Hinzufügen von Berechtigungen für weitere Benutzer: des Authentifizierungsmodus ändern oder Portnummer für den Remotedebugger, finden Sie unter [Konfigurieren des Remotedebuggers](../debugger/remote-debugging.md#configure_msvsmon).

### <a name="BKMK_attach"></a> Anfügen an die ASP.NET-Anwendung vom Visual Studio-Computer aus

1. Öffnen Sie auf dem Computer Visual Studio die Projektmappe, die Sie debuggen möchten (**MyASPApp** , wenn Sie die Schritte in diesem Artikel folgen).
2. Klicken Sie in Visual Studio auf **Debuggen > an den Prozess anhängen** (Strg + Alt + P).

    > [!TIP]
    > In Visual Studio 2017 können Sie erneut an den gleichen Prozess, die Sie zuvor mit angefügte Anfügen **Debuggen > an Prozess anfügen...** (Umschalt + Alt + P). 

3. Legen Sie auf das Feld "Qualifizierer"  **\<Name des Remotecomputers >: 4022**.
4. Klicken Sie auf **aktualisieren**.
    Im Fenster sollten einige Prozesse **Verfügbare Prozesse** angezeigt werden.

    Wenn alle Prozesse, die nicht angezeigt wird, versuchen Sie den Namen des Remotecomputers (der Port ist erforderlich.) anstelle der IP-Adresse. Sie können `ipconfig` in einer Befehlszeile, um die IPv4-Adresse zu erhalten.

    Wenn Sie verwenden möchten die **finden** Schaltfläche müssen Sie möglicherweise [Öffnen von UDP-Port 3702](#bkmk_openports) auf dem Server.

5. Aktivieren Sie  **Prozesse aller Benutzer anzeigen**.

6. Geben Sie den ersten Buchstaben eines Prozessnamens schnell und problemlos suchen *dotnet.exe* (für ASP.NET Core).
   
   Für eine ASP.NET Core-app wurde der vorherigen Prozessnamen *dnx.exe*.

    ![RemoteDBG_AttachToProcess](../debugger/media/remotedbg_attachtoprocess_aspnetcore.png "RemoteDBG_AttachToProcess")

7. Klicken Sie auf **Anfügen**aus.

8. Öffnen Sie die Website des Remotecomputers. Wechseln Sie in einem Browser zu **http://\<Remotecomputernamen >**.
    
    Es sollte die ASP.NET-Webseite angezeigt werden.
9. Klicken Sie in der laufenden Anwendung ASP.NET auf den Link, um die **zu** Seite.

    Der Haltepunkt sollte in Visual Studio erreicht werden.

### <a name="bkmk_openports"></a> Problembehandlung: Erforderliche Ports für Windows Server öffnen

In den meisten Setups werden die erforderlichen Ports durch die Installation von ASP.NET und den Remotedebugger geöffnet. Wenn die Behandlung von Problemen bei der Bereitstellung, und die app hinter einer Firewalls gehostet wird, müssen Sie sicherstellen, dass die richtigen Ports geöffnet sind.

Auf einem virtuellen Azure-Computer müssen Sie Ports durch Öffnen der [Netzwerksicherheitsgruppe](/azure/virtual-machines/virtual-machines-windows-hero-role#open-port-80-for-web-traffic). 

Erforderliche Ports:

- 80 - wird für IIS erforderlich.
- 4022 – erforderlich für das Remotedebuggen von Visual Studio 2017 (finden Sie unter [Remotedebugger – Portzuweisungen](../debugger/remote-debugger-port-assignments.md) Informationen).
- UDP 3702 - erkennungsport (Optional) können Sie die **finden** Schaltfläche beim Anfügen an den Remotedebugger in Visual Studio.

Darüber hinaus müssen diese Ports bereits von der Installation von ASP.NET geöffnet werden:
- 8172 – (Optional) erforderlich für Web Deploy, um die app aus Visual Studio bereitstellen

